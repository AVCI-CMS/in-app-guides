# Merchant API Guide

The Merchant API manages the legal and business profiles of vendors. While a "Brand" represents a creative identity, a "Merchant" represents the legal entity responsible for sales, taxation, and logistics.

## Base URL
`GET /v1/merchant`

---

## Merchant Statuses
- `ACTIVE`: Fully onboarded and trading.
- `PENDING`: Application under review.
- `DRAFT`: Incomplete profile.

---

## Data Structures

### Merchant Profile
| Field | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | Trading name. |
| `corporateName`| `string` | Registered legal name. |
| `taxNumber` | `number` | Government tax identifier. |
| `logo` | `object` | Business logo image. |
| `location` | `object` | `{ lat, lng }` coordinates for maps. |
| `followed` | `boolean` | Current user's follow status. |

---

## Endpoints

### List Merchants
`GET /v1/merchant`

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number |
| `limit` | `number` | Items per page |
| `search` | `string` | Search by name or description |

---

### Get Merchant Map Locations
`GET /v1/merchant/location`

Retrieves a list of all active merchant coordinates, optimized for map rendering.

---

### Get Merchant Card
`GET /v1/merchant/card/:slug`

Retrieves a condensed profile (short version) for UI cards and list item displays.

---

### Get Merchant Details
`GET /v1/merchant/:slug`

Retrieves the exhaustive business profile, including corporate data, bank info, and operational settings.

**Response Data (`data`):**
```json
{
  "name": "Artisan Collective",
  "corporateName": "Artisan Goods LTD",
  "slug": "artisan-collective",
  "taxNumber": 123456789,
  "taxOffice": "Kadikoy VD",
  "email": "sales@...",
  "website": "example.com",
  "address": { "city": "Istanbul", "street": "..." },
  "badges": [ { "title": "Top Seller" } ],
  "settings": { ... }
}
```

---

## Artisan Showcase Self-Profile (`/profil/sayfam`)

Authenticated sellers and craftspeople can inspect and update their public-facing storefront showcase profile directly (e.g. from `/profil/sayfam`).

### Endpoints
- `GET /v1/merchant/me`: Fetch current vendor showcase profile.
- `PUT /v1/merchant/me` or `PATCH /v1/merchant/me`: Update storefront visuals and information.

### Editable Fields
- `logo` / `image`: Storefront logo / avatar.
- `coverImage` / `cover`: Public header banner.
- `description` / `biography`: Artisan story and workshop background.
- `attributes`: Custom attributes (techniques, awards, craft specialties).
- `gallery`: Photos of workshop, studio, or craft process.
- `socialMedia`: Instagram, website, or social links.
- `address`: Public workshop or studio address.

> **Security Note:** Sensitive fields including `status`, `commitionRate`, `isVerified`, and payment configurations are strictly restricted from self-service alteration.

---

## Social & Interactions
- `/v1/merchant/category`: Browse merchant categories.
- `/v1/merchant/follow/:slug`: Follow a merchant for updates.
- `/v1/merchant/like/:slug`: Like a merchant profile.
- `/v1/merchant/view/:slug`: Log profile/shop views.
- `/v1/merchant/question/:slug`: Direct messaging or Q&A.
