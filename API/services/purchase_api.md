# Purchase API Guide

The Purchase API manages the final checkout flow, converting a basket into an order.

## Base URL
`POST /v1/purchase`

---

## Checkout Process

### Submit Purchase
`POST /v1/purchase`

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `basketId` | `string` | Yes | The UUID of the basket |
| `addresses` | `object` | Yes | `{ shipmentAddressId, billingAddressId }` |
| `payment` | `object` | Yes | Payment details including method |
| `terms` | `array` | No | Slugs of accepted agreements |
| `participants` | `array` | Conditional | **Required when the basket contains ticket items (event or route).** One entry per attendee slot; each object must include `basketItemId`, `name`, and optionally `email`, `phone`. See [Order API – Participant information for ticket items](order_api.md#participant-information-for-ticket-items-event--route) for the full structure. Backend registers attendees in a **transaction** (route + all events) and may use a **cart lock** (reservation) while the basket contains tickets; see [Order API – Backend implementation notes](order_api.md#backend-implementation-notes-reference). |

**Response Data:**
```json
{
  "success": true,
  "orderId": "string",
  "paymentStatus": "SUCCESS | PENDING | FAILED",
  "requiresVerification": false
}
```

---

## Subscription Purchase
`POST /v1/purchase/subscription`

Used for recurring payments and plans.
