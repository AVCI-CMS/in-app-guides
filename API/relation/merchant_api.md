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

## Social & Interactions
- `/v1/merchant/category`: Browse merchant categories.
- `/v1/merchant/follow/:slug`: Follow a merchant for updates.
- `/v1/merchant/like/:slug`: Like a merchant profile.
- `/v1/merchant/view/:slug`: Log profile/shop views.
- `/v1/merchant/question/:slug`: Direct messaging or Q&A.
