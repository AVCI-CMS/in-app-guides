# Newsletter API: Usage Guide

The Newsletter API manages email lists, allowing users to opt-in or out of marketing announcements and platform updates.

---

## 📡 Subscription Endpoints

### 1. Subscribe to Newsletter
`POST /v1/newsletter/subscribe`

Adds a new email address to the subscription list.

**Request Body:**
```json
{
  "email": "user@example.com",
  "name": { "first": "Jane", "last": "Doe" }
}
```

**Response:**
Upon subscription, a verification email is sent to the user. The `isVerified` flag remains `false` until confirmation.

---

### 2. Unsubscribe
`POST /v1/newsletter/unsubscribe`

Moves the specified email address from the active list to the unsubscribed list.

---

## 🚦 Statuses
- `ACTIVE`: Subscribed and verified.
- `UNSUBSCRIBED`: Opted out manually.
- `BOUNCED`: Delivery failure (Invalid address).
