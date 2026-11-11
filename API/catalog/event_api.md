# Event API Guide

The Event API manages ticketed or non-ticketed activities, including workshops, exhibitions, and virtual meetings. It supports complex scheduling, capacity management, and location tracking.

## Base URL
`GET /v1/event`

---

## Event Statuses

| Status | Description |
| :--- | :--- |
| `PUBLISHED` | The event is live and visible to the public. |
| `SOLD_OUT` | No more tickets or capacity available. |
| `PASSED` | The event has already taken place. |
| `PRE_REQUEST` | Upcoming event where ticket sales have not yet started. |

---

## Event Types

| Type | Description |
| :--- | :--- |
| `PHYSICAL` | Traditional event at a physical location. |
| `VIRTUAL` | Online event (e.g., Zoom, YouTube Live). |
| `HYBRID` | Event occurring both physically and virtually. |

---

## Endpoints

### List Events (Paginated)
`GET /v1/event`

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number (default: 1) |
| `limit` | `number` | Items per page (default: 10) |
| `status` | `string` | Filter by status (e.g., `PUBLISHED`) |
| `category` | `string` | Filter by category ID or slug |
| `minPrice` | `number` | Minimum price filter |
| `maxPrice` | `number` | Maximum price filter |

---

### Filtered Listings
Shortcuts for common event views:
- `GET /v1/event/new`: Recently added events.
- `GET /v1/event/upcoming`: Events happening soon.
- `GET /v1/event/passed`: Archive of past events.

---

### Get Event Details
`GET /v1/event/:slug`

Retrieves full details including dates, capacity, location, and merchant info.

**Response Data (`data`):**
```json
{
  "id": "event_uuid",
  "name": "Advanced Glass Blowing Workshop",
  "slug": "advanced-glass-blowing",
  "status": "PUBLISHED",
  "date": {
    "start": "2024-07-15T10:00:00.000Z",
    "end": "2024-07-15T17:00:00.000Z"
  },
  "price": {
    "amount": 150.00,
    "sale": 120.00,
    "currency": "USD",
    "discount": { "percentage": 20 }
  },
  "capacity": {
    "min": 5,
    "max": 15,
    "cancelation": true
  },
  "place": {
    "name": "Craft Studio A",
    "address": "..."
  },
  "merchant": {
    "name": "Artisan Collective",
    "slug": "artisan-collective"
  },
  "content": "Full workshop description...",
  "rules": ["Must be over 18", "Materials provided"],
  "notes": ["Lunch included"],
  "images": [ { "url": "...", "alt": "..." } ],
  "metadata": { "featured": true }
}
```

---

## Social & Interactions
Events support integrated social features via common service endpoints:
- `POST /v1/event/like/:slug`: Toggle like
- `GET /v1/event/comment/:slug`: View/Post reviews
- `GET /v1/event/question/:slug`: Ask/View questions

---

## Platform behavior (Routes)

When the catalog includes **routes** (multi-event tours):

- **Event update:** If an event’s time or place is changed, the platform may check whether any **published route** contains this event. Affected routes may be **re-validated** (e.g. timeline rule T_min); if the route becomes invalid, it can be set to **Draft** and the route owner notified.
- **Place soft-delete:** If the **place** linked to an event is soft-deleted (e.g. venue closed), events using that place and **routes** that include those events may be **unpublished or set to Draft** so that broken routes do not remain on sale. See also [Place API](../relation/place_api.md) for cascade behavior.
