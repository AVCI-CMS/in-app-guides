# Place API: List Guide

The Place API manages physical venues, event locations, and geographical points of interest. It provides logistical data such as capacity and operational hours.

---

## 📡 List Endpoints

### 1. List Places
`GET /v1/place`

Returns all active venues as a paginated list.

**Query Parameters:**
- `page`: Page number
- `limit`: Items per page
- `area`: Filter by area/neighborhood slug
- `search`: Search by name or description

---

## 🚦 Place Statuses
- `ACTIVE`: Publicly visible and bookable location.
- `DRAFT`: Venue under setup.

---

## 🏗️ Data Structure Summary
| Field | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | The venue name. |
| `capacity` | `object` | Visitor limits (`min`, `max`). |
| `working` | `array` | Daily operational hours (Monday-Sunday). |
| `address` | `object` | Physical address and district info. |
