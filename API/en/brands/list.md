# Brand API: List Guide

The Brand API manages the public identity and presence of creators, artisans, and boutique manufacturers on the platform.

---

## 📡 List Endpoints

### 1. List Brands
`GET /v1/brand`

Returns all active brand profiles as a paginated list.

**Query Parameters:**
- `page`: Page number
- `limit`: Items per page
- `category`: Category slug
- `search`: Search by name or description

---

## 🚦 Brand Statuses
- `ACTIVE`: Publicly visible brand profile.
- `PENDING`: Brand application under review.
- `DRAFT`: Profile in set up mode.

---

## 🏗️ Data Structure Summary
| Field | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | Brand display name. |
| `logo` | `object` | Image object for the brand logo. |
| `owner` | `object` | Reference to the brand owner (User). |
| `techniques` | `array` | Specialized techniques used by the brand. |
