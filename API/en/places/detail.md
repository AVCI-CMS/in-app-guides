# Place API: Detail Guide

Used to access the exhaustive venue profile, including gallery images, capacity details, and weekly schedule.

---

## 📄 Detail Endpoints

### 1. Get Place Details
`GET /v1/place/:slug`

Returns exhaustive operational and media profile.

**Sample Response:**
```json
{
  "name": "The Grand Workshop",
  "slug": "grand-workshop",
  "capacity": { "min": 20, "max": 150 },
  "working": [
    { "day": 1, "hours": { "start": "09:00", "end": "18:00" } }
  ],
  "address": { "city": "Istanbul", "district": "Besiktas" },
  "gallery": [ { "url": "..." } ]
}
```

---

### 🃏 Short Info
- `GET /v1/place/short/:slug`: Retrieves a condensed profile optimized for mobile cards and list overlays.

---

## 💬 Social & Interactions
- `/v1/place/category`: Browse categories (mapped as `area`).
- `/v1/place/like/:slug`: Favorite a venue.
- `/v1/place/view/:slug`: Log a view.
- `/v1/place/question/:slug`: Venue-specific Q&A.
- `/v1/place/share/:slug`: Track share metrics.
