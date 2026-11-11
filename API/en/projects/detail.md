# Project API: Detail Guide

Used to access the exhaustive project profile, including team composition and media links.

---

## 📄 Detail Endpoints

### 1. Get Project Details
`GET /v1/project/:slug`

Returns the full project profile and team list.

**Sample Response:**
```json
{
  "title": "Riverside Urban Park",
  "slug": "riverside-urban-park",
  "date": "2024-05-12T00:00:00.000Z",
  "category": [ { "name": "Urban Design", "slug": "urban" } ],
  "team": [ { "name": "Jane Doe", "role": "Lead Architect" } ],
  "images": ["url_1", "url_2"]
}
```

---

## 🔗 Related Services
- `/v1/project/category`: Browse categories.
- `/v1/project/attribute`: Technical attributes (Year, Location, etc.).
- `/v1/project/like/:slug`: Track item favorite.
- `/v1/project/share/:slug`: Track share metrics.
