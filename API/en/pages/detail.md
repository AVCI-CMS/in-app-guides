# Page API: Detail Guide

Used to access the layout, sections, and metadata of a specific page.

---

## 📄 Detail Endpoints

### 1. Get Page Details
`GET /v1/page/slug/:slug`

Returns the full profile and text content of a page.

**Sample Response:**
```json
{
  "title": "Terms of Service",
  "slug": "terms-of-service",
  "abstract": "Brief overview...",
  "content": "Full HTML/Markdown content...",
  "category": { "title": "Legal", "slug": "legal" },
  "metadata": { "seo_title": "..." }
}
```

---

## 🎨 Layout and Sections
Pages can contain multiple content sections. The `sections` array in the response (if applicable) provides data for modular page builder components in the frontend.
