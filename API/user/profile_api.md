# User Profile API Guide

The User Profile API allows authenticated users to manage their personal information, addresses, and account settings.

## Base URL
`GET /v1/user`

---

## Profile Management

### Update Profile
`PUT /v1/user/:id`

Updates the authenticated user's personal details.

**Request Body:**
| Field | Type | Description |
| :--- | :--- | :--- |
| `name` | `object` | `{ first: string, last: string }` |
| `birthDate` | `string` | ISO Date |
| `gender` | `string` | `MALE`, `FEMALE`, `OTHER` |
| `contact` | `object` | Phone and email info |

---

## Address Management

### List Addresses
`GET /v1/user/address`

### Add/Update Address
`POST /v1/user/address` or `PUT /v1/user/address/:id`

**Request Body:**
| Field | Type | Required |
| :--- | :--- | :--- |
| `title` | `string` | Yes (e.g., "Home") |
| `address` | `string` | Yes |
| `city` | `string` | Yes |
| `country` | `string` | Yes |

---

## Settings & Notifications

### Notification Settings
`GET /v1/user/notification/settings`
`PUT /v1/user/notification/settings`

Allows users to toggle specific notification channels (Email, SMS, Push).

### Register Device
`POST /v1/user/notification/device`

Registers a device token (FCM/Expo) for push notifications.
