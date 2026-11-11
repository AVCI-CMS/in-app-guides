# Support Ticket API: List Guide

The Support Ticket API facilitates formal communication between customers and workspace staff, managing categorized inquiries and threaded messages.

---

## 📡 Tickets and Messaging

### 1. Create New Ticket
`POST /v1/ticket`

Enables a customer to open a support ticket for a specific topic (Order, Return, Technical, etc.).

**Request Body:**
```json
{
  "category": "ORDER",
  "priority": "HIGH",
  "message": "My order has not arrived yet."
}
```

---

### 2. Message History
- `POST /v1/ticket/message`: Adds a new message to an existing ticket (Attachments supported).
- `GET /v1/ticket/message/ticket/:id`: Returns the threaded message history for a ticket.

---

## 🚦 Ticket Statuses
| Status | Description |
| :--- | :--- |
| `NEW` | Recently created, awaiting review. |
| `IN_PROGRESS` | Staff is actively working on the request. |
| `WAITING_CUSTOMER` | Awaiting a response from the customer. |
| `RESOLVED` | The issue has been addressed. |
| `CLOSED` | Ticket is finalized; no further messages allowed. |
