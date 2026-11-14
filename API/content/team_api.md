# Team API Guide

The Team API provides dynamic corporate roster, executive leadership, and staff directory endpoints for corporate showcase pages ("About Us", "Our Team", "Advisory Board"). It allows storefronts to replace static HTML staff rosters with live content managed in AVCI CMS.

## Base URL
`GET /v1/team`

---

## Endpoints

### List Team Members
`GET /v1/team`

Retrieves a paginated list of active corporate team members.

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number (Default: 1) |
| `limit` | `number` | Items per page (Default: 20) |
| `search` | `string` | Search query matching member name, title, or bio |
| `department` | `string` | Filter members by department (e.g. `Executive`, `Design`, `Operations`) |

**Response Data (`data` array item):**
```json
{
  "id": "team_6735a12f9b8c",
  "slug": "jane-doe",
  "name": "Jane Doe",
  "title": "Chief Technology Officer",
  "department": "Engineering",
  "avatar": "https://cdn.avcicms.com/team/jane-doe.jpg",
  "biography": "Leading cloud architecture and platform scalability.",
  "socialMedia": {
    "linkedin": "https://linkedin.com/in/janedoe",
    "github": "https://github.com/janedoe"
  },
  "order": 1
}
```

---

### Get Team Member Details by Slug
`GET /v1/team/:slug`

Retrieves full biographical profile, publications, and social links for a specific team member.

**Example Request:**
`GET /v1/team/jane-doe`

---

### Get Team Member Details by ID
`GET /v1/team/id/:id`

Retrieves details for a team member by their unique ID.

**Example Request:**
`GET /v1/team/id/team_6735a12f9b8c`

