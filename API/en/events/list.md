# Event API: List Guide

The Event API manages ticketed or free activities like workshops, exhibitions, and virtual meetings. It supports complex scheduling and capacity management.

---

## 📡 List Endpoints

### 1. List Events (Paginated)
`GET /v1/event`

**Query Parameters:**
- `page`: Page number (Default: `1`)
- `limit`: Items per page (Default: `10`)
- `status`: Status filter (e.g., `PUBLISHED`)
- `category`: Category ID or slug
- `minPrice` / `maxPrice`: Price range

---

### 📅 Filtered Item Groups
- `GET /v1/event/new`: Recently added activities.
- `GET /v1/event/upcoming`: Future activities.
- `GET /v1/event/passed`: Past activities.

---

## 🚦 Event Statuses

| Status | Description |
| :--- | :--- |
| `PUBLISHED` | Live and ticketable. |
| `SOLD_OUT` | Capacity reached, ticket sales closed. |
| `PASSED` | Activity has completed. |
| `PRE_REQUEST` | Sales not yet started, pre-collection of interest. |
