# Notification API Guide

The Notification API manages user alerts and system messages across multiple delivery channels. It provides endpoints for synchronized read/seen states across devices.

## Base URL
`GET /v1/notification`

---

## Notification Categories
Notifications are classified into categories for granular filtering and preference management:
- **Transactional**: `ORDER`, `PAYMENT`, `SHIPMENT`, `TRANSACTION`.
- **Engagement**: `COMMENT`, `REPLY`, `FOLLOW`, `LIKE`, `SHARE`, `QUESTION`.
- **System**: `PENALTY`, `NOTIFICATION`, `MEMBER`.
- **Communication**: `MESSAGE`, `CONTACT_FORM`, `TICKET`, `NEWSLETTER`, `FORM`.

---

## Delivery Channels
- `IN_APP`: Visible within the workspace panel or application.
- `PUSH`: Mobile/Desktop push notifications.
- `EMAIL`: Direct email alerts.
- `SMS`: Text messages.
- `SLACK` / `TELEGRAM`: Third-party integration alerts.

---

## Endpoints

### List Notifications
`GET /v1/notification/management/all`

Retrieves a list of all notifications for the authenticated user.

---

### Get Unread Counts
`GET /v1/notification/management/unread/menu-list`

Retrieves counts of unread notifications, typically used for UI badges.

---

### Mark as Read
`PUT /v1/notification/management/read/:_id`

Marks a specific notification as "read" using its content ID.

---

### Sync Seen State
`PUT /v1/notification/management/seen/`

Marks all notifications as "seen," which usually removes the "new" indicator from the notification bell without marking individual items as read.

---

### Hide Notification
`PUT /v1/notification/management/hide/:_id`

Dismisses a notification from the user's active list.

---

## Response Structure (`data`)
```json
{
  "_id": "notification_uuid",
  "category": "ORDER",
  "body": {
    "title": "Order Shipped",
    "message": "Your order #12345 has been shipped!",
    "description": "Click to track your package."
  },
  "isRead": false,
  "seen": true,
  "createdAt": "2024-05-20T14:30:00.000Z",
  "expiresAt": "2024-06-20T14:30:00.000Z"
}
```
