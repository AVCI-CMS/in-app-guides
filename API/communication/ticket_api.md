# Support Ticket API Guide

The Support Ticket API facilitates formal communication between customers and workspace staff. It supports categorized inquiries, priority levels, threaded messaging, and satisfaction feedback.

## Base URL
`GET /v1/ticket`

---

## Ticket Classifications

### Statuses
| Status | Description |
| :--- | :--- |
| `NEW` | Ticket recently created, awaiting staff review. |
| `IN_PROGRESS` | Staff is actively working on the request. |
| `WAITING_CUSTOMER` | Awaiting a response or information from the customer. |
| `RESOLVED` | The issue has been addressed. |
| `CLOSED` | Finalized ticket; no further messages allowed. |

### Categories
- `ORDER`: Issues with specific orders.
- `RETURN` / `CANCELLATION`: Logistics-related requests.
- `COMPLAINT`: Grievances regarding service or products.
- `TECHNICAL`: Website or app technical difficulties.
- `OTHER`: General inquiries.

---

## Endpoints

### Create Ticket
`POST /v1/ticket`

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `category` | `string` | Yes | See categories list above |
| `order` | `string` | No | UUID of the related Order |
| `priority` | `string` | Yes | `LOW`, `MEDIUM`, `HIGH`, `URGENT` |
| `message` | `string` | Yes | Initial detail of the issue |

---

### List My Tickets
`GET /v1/ticket/customer`

Retrieves the authenticated user's ticket history.

---

### Ticket Messaging
Tickets support threaded conversations:
- `POST /v1/ticket/message`: Send a new message to an existing ticket.
- `GET /v1/ticket/message/ticket/:ticketId`: Retrieve all messages for a ticket.

**Message Object:**
```json
{
  "senderType": "staff",
  "message": "We have received your request and are looking into it.",
  "attachments": [ { "url": "...", "name": "screenshot.png" } ],
  "createdAt": "..."
}
```

---

### Submit Feedback
`POST /v1/ticket/feedback`

Post-resolution satisfaction survey.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `ticket` | `string` | Yes | Ticket UUID |
| `rating` | `number` | Yes | 1 to 5 stars |
| `comment` | `string` | No | Additional feedback |
