# Category API Guide

Categories provide a hierarchical organizational structure for all content and entity types in AVCI-CMS. They support parent-child relationships, multi-level nesting, and custom metadata.

## Base URL
`GET /v1/category`

---

## Category Statuses

| Status | Description |
| :--- | :--- |
| `ACTIVE` | Category is live and items can be assigned to it. |
| `DRAFT` | Category is hidden from public listings. |

---

## Endpoints

### List Categories
`GET /v1/category/:type/list`

Retrieves a flat list of active categories for a specific module.

---

### List as Menu (Hierarchical)
`GET /v1/category/:type/list-as-menu`

Retrieves the category tree structure, perfect for building navigation menus or sidebars.

**Response Data (`data` array item):**
```json
{
  "_id": "6911c78bab835e55263a9cb8",
  "title": "Ceramics",
  "slug": "ceramics",
  "children": [
    { "title": "Vases", "slug": "vases", "children": [] },
    { "title": "Plates", "slug": "plates", "children": [] }
  ]
}
```

---

### Get Children for Category
`GET /v1/category/:type/children/:slug`

Retrieves sub-categories belonging to a specific parent category.

---

### Get Category with Items
`GET /v1/category/:type/items/:slug`

Retrieves category details along with a list of items (e.g., Products) associated with it.

**Response Data (`data`):**
```json
{
  "title": "Ceramics",
  "slug": "ceramics",
  "description": "...",
  "items": [
    { "name": "Blue Vase", "slug": "blue-vase", "price": { ... } }
  ]
}
```

---

## Module Types (Path Parameters)
The `:type` parameter must be one of the following:
`product`, `event`, `blog`, `news`, `project`, `merchant`, `brand`, `place`, `organization`.
