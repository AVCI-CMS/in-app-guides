# Newsletter API Guide

The Newsletter API manages email subscription lists, allowing users to opt-in or out of marketing communications and platform updates.

## Base URL
`POST /v1/newsletter`

---

## Subscription Statuses

| Status | Description |
| :--- | :--- |
| `ACTIVE` | User is currently subscribed and verified. |
| `UNSUBSCRIBED` | User has opted out of communications. |
| `BOUNCED` | Email delivery failed consistently. |

---

## Endpoints

### Subscribe to Newsletter
`POST /v1/newsletter/subscribe`

Adds a new email address to the newsletter list.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `email` | `string` | Yes | Valid email address |
| `name` | `object` | No | `{ first: string, last: string }` |

**Response Data:**
```json
{
  "status": "success",
  "message": "Subscription request received. Please check your email for verification.",
  "data": {
    "isVerified": false,
    "status": "ACTIVE"
  }
}
```

---

### Unsubscribe from Newsletter
`POST /v1/newsletter/unsubscribe`

Removes an email address from the active mailing list.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `email` | `string` | Yes | The email address to unsubscribe |

**Response Data:**
```json
{
  "status": "success",
  "message": "You have been successfully unsubscribed."
}
```

---

## Verification & Trust
- **Double Opt-in**: The system typically sends a verification email upon subscription. The `isVerified` flag remains `false` until the user confirms.
- **Member Linkage**: If the user is authenticated during subscription, the `user` field is automatically linked to their profile.
