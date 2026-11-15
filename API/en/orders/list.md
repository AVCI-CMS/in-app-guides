# Order API: List Guide

The Order API manages sales records, ticket generation, and logistics processes following successful payments.

---

## 📡 List Endpoints

### 1. List My Orders
`GET /v1/order`

Returns all past and active orders for the authenticated user.

**Query Parameters:**
- `page`: Page number.
- `status`: Filter by `PENDING`, `COMPLETED`, `SHIPPED`, `CANCELLED`.

---

### 🎟️ My Tickets and Reservations
- `GET /v1/order/tickets`: Returns only purchased event tickets and QR codes.
- `GET /v1/order/upcoming`: Summary of orders for future activities.

---

### 🛍️ Vendor Orders (Marketplace)
- `GET /v1/order/vendor`: Isolated sub-order listing for authenticated merchant accounts.

---

### 💳 Stored Credit Cards & Primary (Default) Card
Fully PCI-DSS compliant token-based storage (via Iyzico, Stripe):
- `GET /v1/order/saved-cards`: Lists stored cards enriched with `isPrimary: true/false` (primary card is always sorted first).
- `POST /v1/order/saved-cards`: Stores a new card (can set `isPrimary: true` to make it default immediately).
- `DELETE /v1/order/saved-cards/:id`: Deletes card token (if default is deleted, the next card is promoted to primary).
- `PUT /v1/order/saved-cards/:id/primary`: Sets selected card as the customer's **Primary Card** for 1-click checkout.

---

## 🚦 Order Statuses
| Status | Description |
| :--- | :--- |
| `PENDING` | Order processed, awaiting payment approval. |
| `COMPLETED` | Successfully finished (Tickets generated). |
| `SHIPPED` | Physical goods handed to the courier. |
| `CANCELLED` | Order cancelled or refunded. |

---

## 🔗 Documentation Link
For detailed guides and SDK usage, visit [AVCI CMS Order Documentation](https://doc.avcicms.com/api/finance/order).

