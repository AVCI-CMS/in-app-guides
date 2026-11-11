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

## 🚦 Order Statuses
| Status | Description |
| :--- | :--- |
| `PENDING` | Order processed, awaiting payment approval. |
| `COMPLETED` | Successfully finished (Tickets generated). |
| `SHIPPED` | Physical goods handed to the courier. |
| `CANCELLED` | Order cancelled or refunded. |
