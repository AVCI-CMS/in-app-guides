# Page API Guide

The Page API manages static and dynamic information pages, such as "About Us," "Privacy Policy," or specialized landing pages. Pages can integrate custom forms and legal agreements.

## Base URL
`GET /v1/page`

---

## Page Statuses

| Status | Description |
| :--- | :--- |
| `PUBLISHED` | Page is live and accessible. |
| `HIDDEN` | Page is accessible via direct link but hidden from listings. |
| `DRAFT` | Page is in preparation. |

---

## Endpoints

### List Pages
`GET /v1/page`

Retrieves a list of all publicly listed pages.

---

### Get Page Details
`GET /v1/page/:slug`

Retrieves the full content and structural metadata for a specific page.

**Response Data (`data`):**
```json
{
  "id": "page_uuid",
  "title": "Contact Us",
  "slug": "contact",
  "content": "<h1>Get in touch</h1>...",
  "featuredImage": "image_url",
  "form": "form_uuid",
  "agreement": "terms_uuid",
  "languages": ["en", "tr"],
  "metadata": { "seo": { ... } }
}
```

---

## Advanced Integrations

### Form Linkage
Pages can have an associated `form`. If a `form` UUID is present, the frontend should typically render the corresponding [Custom Form](./communication/form_api.md) at the bottom of the page or in a specific section.

### Agreement Linkage
Pages can link to specific [Terms & Conditions](./services/terms_api.md). This is common for legal pages or registration landing pages where a specific version of terms must be display or accepted.

---

## Social & Interactions
- `/v1/page/category`: Browse page groupings.
- `/v1/page/like/:slug`: Track page favorites.
- `/v1/page/share/:slug`: Log page sharing activities.
