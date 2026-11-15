# Order API: Detail and Logistics

Used to access specific order contents, tracking information, and generated ticket/file links.

---

## 📄 Detail Endpoints

### 1. Get Order Details
`GET /v1/order/:id`

Returns items, payment summary, and shipping address.

**Sample Response:**
```json
{
  "id": "order_uuid",
  "orderNo": "AVCI-12345",
  "items": [ ... ],
  "shipping": { "trackingNo": "TR123...", "company": "Courier Co" },
  "price": { "total": 1250.00, "currency": "TRY" }
}
```

---

## 🎟️ Participant and Ticket Details
If the order contains an event:
- **Participants:** Name, ID, or Email for each individual ticket holder.
- **Tickets:** PDF or QR code access links.

---

## 🧾 Cancellations, Returns and Vendor Orders

### 1. Direct Pre-Shipment Order Cancellation (Customer)
`POST /v1/order/:orderId/cancel`

Customers can directly cancel orders before carrier dispatch (`WAITING`, `PREPARING`, `PENDING_PAYMENT`). Product reservations are instantly restored, coupon usages rolled back, and provider payments voided or refunded.

```json
{
  "reason": "Wrong size or address entered",
  "reasonCode": "BUYER_CANCELLED"
}
```

### 2. Marketplace Vendor Sub-Order Cancellation
`POST /v1/order/management/sub-order/:subOrderId/cancel`

Sellers cancel an unfulfilled sub-order (e.g. out of stock). Proportional customer refund is computed automatically via `RefundAllocationService`.

```json
{
  "reason": "Item out of stock",
  "autoRefund": true,
  "restoreStock": true,
  "isSellerFault": true
}
```

### 3. Post-Shipment RMA Return Requests
Once orders are shipped (`ON_SHIPMENT`, `DONE`), direct cancellation is closed. Customers initiate return requests via the Support Ticket module (`POST /v1/ticket` with `type: "RETURN"`, `relatedId: orderId`).

- **Vendor Sub-Orders:** Marketplace sellers fetch isolated sub-orders via `GET /v1/order/vendor/:subOrderId`.

---

## 🔗 Documentation Link
For detailed guides and SDK usage, visit [AVCI CMS Order Documentation](https://doc.avcicms.com/api/finance/order).

