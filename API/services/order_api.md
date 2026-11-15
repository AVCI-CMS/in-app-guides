# Order API Guide

The Order API handles the finalization of purchases and provides exhaustive tracking of order history, payment statuses, and shipment progress.

## Base URL
`GET /v1/order`

> **Note:** Management endpoints (`/v1/order/management/*`) are private and strictly reserved for the internal admin panel (`frontend/`). They are not exposed to external SDKs or public integrations. For full documentation, visit [AVCI CMS Order Documentation](https://doc.avcicms.com/api/finance/order).

---

## Order Statuses

| Status | Description |
| :--- | :--- |
| `PENDING_PAYMENT`| Order created, awaiting successful transaction. |
| `PREPARING` | Payment confirmed, merchant is preparing items. |
| `ON_SHIPMENT` | Package has been handed to the carrier. |
| `DONE` | Order successfully delivered. |
| `REFUNDED` | Payment returned to the customer. |
| `CANCELED` | Order terminated before fulfillment. |

---

## Endpoints

### Create Order
`POST /v1/order`

Finalizes the checkout process using a prepared basket and validated addresses.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `basketId` | `string` | Yes | Active basket UUID |
| `paymentMethod` | `string` | Yes | `CREDIT_CARD`, `BANK_TRANSFER`, etc. |
| `addresses` | `object` | Yes | `{ shipmentAddressId, billingAddressId }` |
| `participants` | `array` | Conditional | **Required when the basket contains ticket items (event or route).** See [Participant information for ticket items](#participant-information-for-ticket-items-event--route) below. |

---

### Participant information for ticket items (event / route)

When the basket contains **ticket items** (events or routes), the tenant frontend **must** collect participant (attendee) information and send it in the Create Order request. Without this data, the platform cannot register attendees on the event or route after payment.

- **When is it required?**  
  If the basket has at least one item with `type` (or `itemType`) `event` or `route`, include a `participants` array.

- **Request field: `participants`**  
  Array of participant objects. Each object represents one attendee slot (e.g. one ticket). For multiple tickets of the same event/route, send one entry per ticket.

| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `basketItemId` | `string` | Yes | The basket line item `_id` this participant belongs to (links to an event or route item). |
| `name` | `string` | Yes | Full name of the attendee. |
| `email` | `string` | No* | Email (*required if different from the logged-in user or if required by workspace settings). |
| `phone` | `string` | No | Phone number for contact. |

**Example (basket has one event ticket and one route ticket):**
```json
{
  "basketId": "basket_uuid",
  "paymentMethod": "CREDIT_CARD",
  "addresses": { "shipmentAddressId": "...", "billingAddressId": "..." },
  "participants": [
    { "basketItemId": "item_event_123", "name": "Ayşe Yılmaz", "email": "ayse@example.com" },
    { "basketItemId": "item_route_456", "name": "Mehmet Demir", "email": "mehmet@example.com" }
  ]
}
```

- **Backend behavior after payment:**  
  For **event** items, the platform adds the participant (e.g. by user id or the given name/email) to that event’s `attendees`. For **route** items, the participant is added to the route’s `attendees` and to **all events** inside that route, so one route ticket registers the attendee for the full tour.

**Backend implementation notes (reference):**
- **Transaction:** For route tickets, the platform must perform the route + all events’ attendee updates inside a **single database transaction** (e.g. MongoDB `session.withTransaction`). If any step fails (e.g. an event’s capacity was filled by another user), the entire operation is rolled back and the client receives an error such as “Sorry, this slot is no longer available.”
- **Cart lock (optional):** When a user adds an event or route ticket to the basket, the backend may **temporarily reserve** that capacity (e.g. via Redis) for a short period (e.g. 10 minutes) so that during checkout the user does not get a “sold out” error. Lock is released when the item is removed from the basket or when the reservation expires; payment success converts the reservation into a permanent attendee record.

---

### List My Orders
`GET /v1/order`

Retrieves a paginated list of the user's order history.

**Response Data (`data` array item):**
```json
{
  "orderId": "ORD-12345",
  "status": "PREPARING",
  "orderDate": "2023-10-01T...",
  "amount": { "total": 450.50, "currency": "TRY" },
  "receiver": "John Doe",
  "orderSummary": { "product": 2, "event": 1 }
}
```

---

### Get Order Details
`GET /v1/order/:orderId`

Retrieves the full profile of an order, including individual sub-orders (for multi-merchant baskets), payment breakdown, and shipping tracking.

**Response Data (`data`):**
```json
{
  "orderId": "ORD-12345",
  "status": "ON_SHIPMENT",
  "date": "...",
  "payment": {
    "price": { "total": 450.50, "currency": "TRY" },
    "paymentStatus": "SUCCESS",
    "installment": 1
  },
  "addresses": {
    "shipment": { "city": "Istanbul", "district": "Besiktas", ... },
    "billing": { ... }
  },
  "items": [
    {
      "name": "Ceramic Bowl",
      "quantity": 2,
      "price": { "amount": 150, ... },
      "merchant": { "name": "Artisan Shop" }
    }
  ]
}
```

---

### Cancel Order Directly (Before Shipment)
`POST /v1/order/:orderId/cancel`

Allows customers to directly cancel their orders before the package has been handed to the carrier (`WAITING`, `PREPARING`, or `PENDING_PAYMENT`).
Instantly releases product reservations/stock (`restoreStockCounts`), rolls back coupon usage, and issues a payment void/refund with the payment provider.

**Request Body:**
```json
{
  "reason": "Wrong item or size selected",
  "reasonCode": "BUYER_CANCELLED"
}
```

**Response (200 OK):**
```json
{
  "status": "success",
  "message": "Order canceled successfully",
  "data": {
    "orderId": "ORD-12345",
    "status": "CANCELED",
    "refundResult": { "status": "success", "type": "VOID", "amount": 450.50 }
  }
}
```

---

### Saved Payment Cards (with Primary / Default Card)
Manages stored credit cards with full PCI-DSS compliance. AVCI CMS never stores PAN, CVV, or expiry dates; card tokens are maintained by the payment provider, and the customer's preferred primary card token is tracked on their account.

- **List Saved Cards:** `GET /v1/order/saved-cards`  
  Returns stored cards enriched with `isPrimary: boolean`. The primary card is always sorted first.
- **Store Card:** `POST /v1/order/saved-cards`  
  Accepts card details and optional `"isPrimary": true`. Automatically marks the first saved card as primary.
- **Delete Card:** `DELETE /v1/order/saved-cards/:id`  
  Deletes card token. If the deleted card was primary, automatically promotes the next available card to primary.
- **Set Primary Card:** `PUT /v1/order/saved-cards/:id/primary`  
  Sets the card as default for future 1-click checkouts and returns the updated card list.

---

### Vendor Sub-Orders (Isolated)

Merchants and marketplace sellers query their isolated sub-orders using their seller API credentials.

#### List Vendor Sub-Orders
`GET /v1/order/vendor`

Query params: `page`, `limit`, `status`.

#### Get Vendor Sub-Order
`GET /v1/order/vendor/:subOrderId`

Returns the merchant's items, recipient delivery address, and merchant-specific payout details.

#### Cancel Assigned Sub-Order (Vendor)
`POST /v1/order/management/sub-order/:subOrderId/cancel`

Marketplace seller cancels their unfulfilled sub-order (e.g. out of stock). Restores merchant item stock, calculates customer refund via `RefundAllocationService`, and recalculates parent order status.

```json
{
  "reason": "Item out of stock / Cannot fulfill",
  "autoRefund": true,
  "restoreStock": true,
  "isSellerFault": true
}
```

---

### Cancellations and Returns Workflow

AVCI CMS provides a two-tiered cancellation and return architecture:

1. **Pre-Shipment (Instant Direct Cancellation):**
   - Customer endpoint: `POST /v1/order/:orderId/cancel`
   - Vendor endpoint: `POST /v1/order/management/sub-order/:subOrderId/cancel`
   - Admin endpoint: `POST /v1/order/management/:id/cancel`
   - Triggered while status is `WAITING`, `PREPARING`, or `PENDING_PAYMENT`. Completely automated: stocks are restored, coupons rolled back, and payments refunded/voided immediately.

2. **Post-Shipment (RMA Return Flow via Ticket Module):**
   - Once items are shipped (`ON_SHIPMENT`, `DONE`), direct cancellation is closed. Customers request a return or dispute via the **Ticket API**:
   ```http
   POST /v1/ticket
   Content-Type: application/json

   {
     "type": "RETURN",
     "title": "Return Request - ORD-12345",
     "message": "I would like to return the ceramic bowl.",
     "relatedEntity": "order",
     "relatedId": "ORD-12345"
   }
   ```
   - Store operators and sellers review the dispute in the management console, issue a return shipping barcode, inspect returned goods, and process the refund via `/order/management/sub-order/:id/refund`.

---

## 🔗 Official Documentation
For complete technical details, code samples, and workflow guides:
- [AVCI CMS Order API Reference](https://doc.avcicms.com/api/finance/order)
- [Order & Logistics Multi-Role Guide](https://doc.avcicms.com/guides/modules/finance-logistics/orders)

