# Page API: List Guide

The Page API manages static and dynamic content such as "About Us", "Privacy Policy", or custom landing pages.

---

## 📡 List Endpoints

### 1. List Pages
`GET /v1/page`

Returns all active pages as a list.

**Query Parameters:**
- `page`: Page number
- `limit`: Items per page
- `language`: Language code (`en`, `tr`)
- `category`: Page group

---

## 🚦 Page Statuses

| Status | Description |
| :--- | :--- |
| `PUBLISHED` | Page is live and accessible. |
| `HIDDEN` | Accessible only via direct link, not in lists. |
| `DRAFT` | Page is under development. |
