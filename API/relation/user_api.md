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
- `POST /v1/user/address`: Add a new address. If `isPrimary: true` is sent, it is automatically designated as the default address and all other addresses have `isPrimary` reset.
- `PUT /v1/user/address/:id`: Update an existing address. Supports matching by `addressId`, legacy `id`, or MongoDB `_id`. Passing `isPrimary: true` will update the address and simultaneously set it as the primary address across the user's account.
- `PUT /v1/user/address/:id/primary`: Dedicated endpoint to set an address as the default without altering other fields.
- `DELETE /v1/user/address/:id`: Remove an address by its identifier.

**Address Object:**
```json
{
  "addressId": "addr_6735be91a12e",
  "title": "Home",
  "firstName": "John",
  "lastName": "Doe",
  "phone": "+905551234567",
  "city": "Istanbul",
  "district": "Besiktas",
  "neighborhood": "Levent Mah.",
  "addressLine1": "Main St. No: 5 D: 2",
  "zipCode": "34340",
  "country": "TR",
  "isPrimary": true
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
