# News API: Detail Guide

Used to access the full content, media gallery, and SEO metadata of a specific news item.

---

## 📄 Detail Endpoints

### 1. Get News Details
`GET /v1/news/:slug`

Returns the full profile and text content of a news item.

**Sample Response:**
```json
{
  "title": "New Artisan Workshop Opens in Istanbul",
  "slug": "new-artisan-workshop-istanbul",
  "type": "INTERNAL",
  "content": "Full HTML/Markdown content...",
  "images": [ { "url": "..." } ],
  "author": "John Doe"
}
```

---

## 🔗 External Links
For `EXTERNAL` news types, the `url` field contains the destination link. The platform typically provides a summary and a "Read More" trigger to this external URL.
