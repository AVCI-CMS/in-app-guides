# Brand API: Detail Guide

Used to access the exhaustive brand profile, including team members, contact information, and artistic expertise.

---

## 📄 Detail Endpoints

### 1. Get Brand Details
`GET /v1/brand/slug/:slug`

Returns the full brand identity and communication data.

**Sample Response:**
```json
{
  "name": "Ceramic Collective",
  "slug": "ceramic-collective",
  "description": "Hand-crafted earthenware and stoneware.",
  "logo": { "url": "..." },
  "techniques": ["Wheel-throwing", "Glazing"],
  "owner": { "name": { "first": "John", "last": "Doe" } },
  "contact": { "email": "info@...", "tel": "..." },
  "address": { "city": "Istanbul", "district": "Kadikoy" },
  "team": [ { "name": "Alice", "role": "Master Potter" } ]
}
```

---

## 💬 Social & Interactions
- `/v1/brand/category`: Browse categories.
- `/v1/brand/like/:slug`: Follow or like a brand.
- `/v1/brand/view/:slug`: Log a view.
- `/v1/brand/question/:slug`: Q&A specific to the brand.
- `/v1/brand/share/:slug`: Track share metrics.
