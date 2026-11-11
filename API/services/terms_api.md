# Terms & Agreements API Guide

The Terms API provides access to legal documents and user agreements.

## Base URL
`GET /v1/terms`

---

## Endpoints

### List Legal Documents
`GET /v1/terms`

Retrieves a list of all active terms and agreements.

---

### Get Term by Slug
`GET /v1/terms/:slug`

Retrieves the full content of a specific legal document (e.g., `privacy-policy`).

**Response Data:**
```json
{
  "title": "Privacy Policy",
  "slug": "privacy-policy",
  "content": "HTML or Plain Text content",
  "date": "ISO Date"
}
```
