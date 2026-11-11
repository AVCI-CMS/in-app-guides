# Group API Guide

Groups provide a way to categorize and cluster entities beyond the standard hierarchical categories. They support nesting (parent-child groups) and can be used for brand-specific clustering, thematic groupings, or organizational units.

## Base URL
`GET /v1/group`

---

## Group Statuses

| Status | Description |
| :--- | :--- |
| `ACTIVE` | Group is live and visible. |
| `DRAFT` | Group is hidden from public views. |
| `ARCHIVED` | Past group legacy data. |

---

## Endpoints

### List Groups
`GET /v1/group/:type`

Retrieves a list of active groups for a specific module.

**Path Parameters:**
- `type`: The item type contained in the group (e.g., `product`, `merchant`, `blog`).

**Response Data (`data` array item):**
```json
{
  "_id": "group_uuid",
  "title": "Winter Collection",
  "slug": "winter-collection",
  "itemsCount": 24,
  "status": "ACTIVE",
  "featuredImage": { "url": "..." }
}
```

---

### Get Group Details
`GET /v1/group/:type/slug/:slug`

Retrieves the full group profile, including linked items and its position in a hierarchy (parent/children).

**Response Data (`data`):**
```json
{
  "id": "group_uuid",
  "title": "Winter Collection",
  "slug": "winter-collection",
  "description": "Premium winter gear and apparel.",
  "items": ["prod_1", "prod_2"],
  "parent": { "title": "Main Collection", "slug": "main" },
  "children": [
    { "title": "Winter Jackets", "slug": "jackets" }
  ],
  "campaign": "campaign_uuid",
  "metadata": { ... }
}
```

---

## Social & Interactions
Groups support a full suite of engagement features:
- `POST /v1/group/like/:slug`: Like a group.
- `POST /v1/group/share/:slug`: Share activities.
- `GET /v1/group/comment/:slug`: Reviews or discussions.
- `GET /v1/group/question/:slug`: Group-specific questions.
