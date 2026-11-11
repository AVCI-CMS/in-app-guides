# User Profile API Guide

The User Profile API allows authenticated users to manage their personal information, delivery addresses, security preferences, and regional settings across the AVCI-CMS ecosystem.

## Base URL
`GET /v1/user`

---

## User Statuses

| Status | Description |
| :--- | :--- |
| `ACTIVE` | Normal account standing. |
| `PENDING_VALIDATION` | Awaiting email or phone verification. |
| `SUSPENDED` | Account restricted due to policy violations. |

---

## Endpoints

### Get Current User Profile
`GET /v1/auth/me` (Note: Auth details in Authentication Guide)

### Update Profile
`PUT /v1/user/:id`

Updates personal details like name, gender, or birth date.

---

### Address Management
- `GET /v1/user/address`: List all saved delivery/billing addresses.
- `POST /v1/user/address`: Add a new address.
- `PUT /v1/user/address/:id`: Update an existing address.
- `DELETE /v1/user/address/:id`: Remove an address.

**Address Object:**
```json
{
  "title": "Home",
  "name": { "first": "John", "last": "Doe" },
  "city": "Istanbul",
  "district": "Besiktas",
  "addressLine1": "Main St. No: 5",
  "isDefault": true
}
```

---

### Notification Preferences
- `GET /v1/user/notification/settings`: Retrieve current alert preferences.
- `PUT /v1/user/notification/settings`: Enable/Disable specific channels (Email, SMS, Push) for different activity categories.
- `POST /v1/user/notification/device`: Register a new push token (FCM/Expo) for the current device.

---

### System Settings
`GET /v1/user/system-settings`

Manages localized UX preferences:
- `language`: `en`, `tr`.
- `currency`: `USD`, `TRY`, `EUR`.
- `timezone`, `dateFormat`, `theme`.
