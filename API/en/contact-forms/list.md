# Contact Form API: Usage Guide

The Contact Form API allows guest users or customers to send general inquiries, support requests, or lead information to the workspace administrators.

---

## 📡 Submission Endpoint

### 1. Submit Message
`POST /v1/contact-form`

Registers a new contact message in the system.

**Request Body:**
```json
{
  "name": { "first": "Jane", "last": "Doe" },
  "email": "jane@example.com",
  "tel": 5551234567,
  "subject": "Partnership Inquiry",
  "message": "I would like to discuss a potential partnership..."
}
```

---

## 🚦 Internal Statuses
Incoming messages go through several stages in the panel:
- `UNREAD`: New submission, not yet opened.
- `READEN`: Opened by an administrator.
- `REPLYED`: Responded to or processed by an administrator.
