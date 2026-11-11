# Notification API: List Guide

The Notification API manages user alerts and system messages (Email, Push, In-App). It synchronizes read/seen states across devices.

---

## 📡 List and Management Endpoints

### 1. List Notifications
`GET /v1/notification/management/all`

Returns all notifications (Order, Follow, Comment, etc.) for the authenticated user.

---

### 2. Unread Counts
`GET /v1/notification/management/unread/menu-list`

Returns unread notification counts for the UI "Bell" icon or menus.

---

### 3. State Updates
- `PUT /v1/notification/management/read/:id`: Marks a specific notification as **"Read"**.
- `PUT /v1/notification/management/seen/`: Marks all new notifications as **"Seen"** (Removes new tag).
- `PUT /v1/notification/management/hide/:id`: Removes the notification from the user's active list.

---

## 🚦 Categories
- **Transactional:** `ORDER`, `PAYMENT`, `SHIPMENT`.
- **Interaction:** `COMMENT`, `LIKE`, `FOLLOW`, `SHARE`, `QUESTION`.
- **System:** `PENALTY`, `MEMBER`.
- **Communication:** `MESSAGE`, `TICKET`, `NEWSLETTER`.
