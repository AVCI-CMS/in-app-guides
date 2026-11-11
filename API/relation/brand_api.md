# Brand API Guide

The Brand API manages the identity and public presence of creators, artisans, and manufacturers on the platform. It covers everything from visual assets and social badges to technical expertise and location data.

## Base URL
`GET /v1/brand`

---

## Brand Statuses
- `ACTIVE`: Publicly visible brand profile.
- `PENDING`: Brand under review.
- `DRAFT`: Brand profile being set up.

---

## Data Structures

### Brand Profile
| Field | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | Brand display name. |
| `logo` | `object` | Image object for the brand logo. |
| `owner` | `object` | Reference to the brand owner (User). |
| `techniques` | `array` | List of specialized techniques used by the brand. |
| `badges` | `array` | Certifications or platform achievements. |
| `location` | `object` | `{ lat, lng }` geographical coordinates. |

---

## Endpoints

### List Brands
`GET /v1/brand`

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number |
| `limit` | `number` | Items per page |
| `category` | `string` | Filter by category slug |
| `search` | `string` | Search by name or description |

---

### Get Brand by Slug
`GET /v1/brand/slug/:slug`

Retrieves the exhaustive brand profile, including team members, contact info, and exhibition history.

**Response Data (`data`):**
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
  "badges": [ { "title": "Verified Artisan" } ],
  "team": [ { "name": "Alice", "role": "Master Potter" } ]
}
```

---

## Social & Interactions
- `/v1/brand/category`: Browse brand categories.
- `/v1/brand/like/:slug`: Follow or like a brand.
- `/v1/brand/view/:slug`: Log a profile view.
- `/v1/brand/question/:slug`: Q&A specifically for the brand.
- `/v1/brand/share/:slug`: Track social sharing of the brand profile.
