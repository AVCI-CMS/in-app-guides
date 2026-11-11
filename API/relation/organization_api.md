# Organization API Guide

The Organization API manages the profiles of corporate entities, institutions, and umbrella organizations within the platform. It provides detailed corporate metadata, team structures, and operational data.

## Base URL
`GET /v1/organization`

---

## Organization Statuses
- `ACTIVE`: Fully registered and active corporate profile.
- `DRAFT`: Profile under development.

---

## Data Structures

### Corporate Profile
| Field | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | The organization's trading or primary name. |
| `corporateName` | `string` | Legal registered entity name. |
| `corporationType` | `string` | Type of legal entity (e.g., Sole Proprietorship, LLC). |
| `owner` | `object` | Reference to the primary account owner (User). |
| `website` | `string` | Official organization website. |
| `location` | `object` | `{ lat, lng }` geographical coordinates. |

---

## Endpoints

### List Organizations
`GET /v1/organization`

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number |
| `limit` | `number` | Items per page |
| `search` | `string` | Search by name or description |

---

### Get Organization Details
`GET /v1/organization/slug/:slug`

Retrieves the exhaustive corporate profile, including contact details, bank information, and team structure.

**Response Data (`data`):**
```json
{
  "name": "Artisans Association",
  "slug": "artisans-association",
  "corporateName": "National Artisans Group LLC",
  "description": "A non-profit organization supporting local pottery...",
  "logo": { "url": "..." },
  "email": "contact@...",
  "website": "artisans.org",
  "address": { "city": "Istanbul", "district": "Uskudar" },
  "bank": {
    "bankName": "Sample Bank",
    "iban": "TR..."
  },
  "team": [ { "name": "Mark", "role": "Director" } ]
}
```

---

## Social & Interactions
- `/v1/organization/category`: Browse organization categories.
- `/v1/organization/like/:slug`: Follow or like an organization.
- `/v1/organization/view/:slug`: Log a profile view.
- `/v1/organization/question/:slug`: Organization-specific Q&A.
- `/v1/organization/share/:slug`: Track social sharing of the profile.
