# Contact Form API Guide

The Contact Form API allows guest users or customers to send general inquiries, support requests, or lead information to the workspace administrators.

## Base URL
`POST /v1/contact-form`

---

## Endpoints

### Submit Contact Message
`POST /v1/contact-form`

Submits a new contact message to the system.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `name` | `object` | Yes | `{ first: string, last: string }` |
| `email` | `string` | Yes | Valid email address for replies |
| `tel` | `number` | No | Phone number contact |
| `subject` | `string` | Yes | Subject of the inquiry |
| `message` | `string` | Yes | Detailed message content |

**Example Request:**
```json
{
  "name": { "first": "Jane", "last": "Doe" },
  "email": "jane@example.com",
  "tel": 5551234567,
  "subject": "Partnership Inquiry",
  "message": "I would like to discuss a potential partnership..."
}
```

**Response Data:**
```json
{
  "status": "success",
  "message": "Your message has been received."
}
```

---

## Submission Statuses (Internal)
While the public API only handles submissions, messages are tracked internally with the following statuses:
- `UNREAD`: New submission.
- `READEN`: Opened by an admin.
- `REPLYED`: A response has been sent to the user.
