# Project API Guide

The Project API is used to showcase architectural, design, or business projects. It provides a rich structure for displaying project details, team members, and client information.

## Base URL
`GET /v1/project`

---

## Project Statuses

| Status | Description |
| :--- | :--- |
| `ACTIVE` | Project is live and publicly viewable. |
| `ARCHIVED` | Past project kept for reference. |

---

## Endpoints

### List Projects (Paginated)
`GET /v1/project`

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number |
| `limit` | `number` | Items per page |
| `category` | `string` | Filter by category slug |
| `year` | `number` | Filter by project year |
| `attributes` | `json` | Filter by custom attributes (JSON string) |

---

### Get Project Details
`GET /v1/project/:slug`

Retrieves the full profile of a project, including team composition and media links.

**Response Data (`data`):**
```json
{
  "id": "proj_uuid",
  "title": "Riverside Urban Park",
  "slug": "riverside-urban-park",
  "status": "ACTIVE",
  "date": "2024-05-12T00:00:00.000Z",
  "description": "Full HTML/Markdown description...",
  "abstract": "Brief summary of the project.",
  "category": [ { "name": "Urban Design", "slug": "urban" } ],
  "team": [
    {
      "name": "Design Team",
      "members": [
        { "name": "Jane Doe", "role": "Lead Architect" }
      ]
    }
  ],
  "socialMedia": [
    { "platform": "Instagram", "username": "riverside_park", "url": "..." }
  ],
  "links": {
    "page": "https://...",
    "source": "Github/Behance"
  },
  "images": ["url_1", "url_2"],
  "metadata": { "featured": true }
}
```

---

## Integrated Services
Projects support common engagement features:
- `/v1/project/category`: Relevant project categories.
- `/v1/project/attribute`: Technical attributes (e.g., Year, Location).
- `/v1/project/like/:slug`: Favorite tracking.
- `/v1/project/share/:slug`: Social sharing logs.
