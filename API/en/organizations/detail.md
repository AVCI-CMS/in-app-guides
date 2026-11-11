# Organization API: Detail Guide

Used to access the exhaustive corporate profile, including contact details, bank information, and team structure.

---

## 📄 Detail Endpoints

### 1. Get Organization Details
`GET /v1/organization/slug/:slug`

Returns the full corporate identity and operational data.

**Sample Response:**
```json
{
  "name": "Artisans Association",
  "slug": "artisans-association",
  "corporateName": "National Artisans Group LLC",
  "description": "A non-profit organization supporting local pottery...",
  "logo": { "url": "..." },
  "email": "contact@...",
  "website": "artisans.org",
  "bank": {
    "bankName": "Sample Bank",
    "iban": "TR..."
  },
  "team": [ { "name": "Mark", "role": "Director" } ]
}
```

---

## 💬 Social & Interactions
- `/v1/organization/category`: Browse categories.
- `/v1/organization/like/:slug`: Follow or like an organization.
- `/v1/organization/view/:slug`: Log a view.
- `/v1/organization/question/:slug`: Organization-specific Q&A.
- `/v1/organization/share/:slug`: Track share metrics.
