# Place API Guide

The Place API manages physical venues, event locations, and geographical interest points. It provides detailed logistical information such as capacity, operational hours, and precise location data.

## Base URL
`GET /v1/place`

---

## Place Statuses
- `ACTIVE`: Publicly visible and bookable location.
- `DRAFT`: Venue under setup.

**Cascade on soft-delete:** When a place is soft-deleted (e.g. venue closed), the platform may **unpublish or set to Draft** any **events** that use this place, and any **routes** that contain those events, so that broken tours do not stay on sale. See [Event API – Platform behavior (Routes)](../catalog/event_api.md#platform-behavior-routes) for the event/route side.

---

## Data Structures

### Place Logistics
| Field | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | The venue name. |
| `capacity` | `object` | `{ min: number, max: number }` visitor limits. |
| `working` | `array` | Daily operational hours (0-6 for Mon-Sun). |
| `address` | `object` | Detailed physical address and district info. |
| `area` | `array` | List of categories/neighborhoods this place belongs to. |

---

## Endpoints

### List Places
`GET /v1/place`

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number |
| `limit` | `number` | Items per page |
| `area` | `string` | Filter by area/neighborhood slug |
| `search` | `string` | Search by name or description |

---

### Get Short Place Info
`GET /v1/place/short/:slug`

Retrieves a condensed version of the venue profile, optimized for mobile cards and list overlays.

---

### Get Place Details
`GET /v1/place/:slug`

Retrieves the exhaustive venue profile, including gallery images, full capacity details, and weekly schedule.

**Response Data (`data`):**
```json
{
  "name": "The Grand Workshop",
  "slug": "grand-workshop",
  "abstract": "A spacious venue for artisan events.",
  "capacity": { "min": 20, "max": 150 },
  "working": [
    { "day": 1, "hours": { "start": "09:00", "end": "18:00" } }
  ],
  "address": { "city": "Istanbul", "district": "Besiktas" },
  "logo": { "url": "..." },
  "gallery": [ { "url": "..." } ]
}
```

---

## Social & Interactions
- `/v1/place/category`: Browse place categories (mapped as `area`).
- `/v1/place/like/:slug`: Favorite a venue.
- `/v1/place/view/:slug`: Log a location view.
- `/v1/place/question/:slug`: Venue-specific Q&A.
- `/v1/place/share/:slug`: Track venue profile sharing.
