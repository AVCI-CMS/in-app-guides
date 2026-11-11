# Event API: Detail Guide

Used to access the complete activity profile, including capacity, location, and guest list data.

---

## 📄 Detail Endpoints

### 1. Get Event Details
`GET /v1/event/:slug`

Returns the full profile and text content of an event.

**Sample Response:**
```json
{
  "name": "Artisan Ceramic Workshop",
  "slug": "artisan-ceramic-workshop",
  "price": { "amount": 150.00, "sale": 120.00, "currency": "TRY" },
  "capacity": { "min": 5, "max": 15, "track": true },
  "venue": { "name": "Studio A", "slug": "studio-a" },
  "date": { "start": "...", "end": "..." }
}
```

---

## 🔗 Related Items and Services
- `/v1/event/like/:slug`: Toggle item favorite.
- `/v1/event/view/:slug`: Log item view analytics.
- `/v1/event/share/:slug`: Track social share activity.
- `/v1/event/category`: Browse event categories.
