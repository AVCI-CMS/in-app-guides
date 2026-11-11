# Menu API Guide

The Menu API provides access to hierarchical navigation structures. It supports multi-location placement (Header, Footer, Sidebar) and nested menu items for complex site architectures.

## Base URL
`GET /v1/menu`

---

## Data Structures

### Menu Item Object
```json
{
  "title": "Shop",
  "url": "/catalog",
  "icon": "icon_name",
  "order": 1,
  "isActive": true,
  "children": [
    {
      "title": "Accessories",
      "url": "/catalog/accessories",
      "order": 1
    }
  ]
}
```

---

## Endpoints

### List Menus
`GET /v1/menu`

Retrieves all configured menus for the workspace.

**Response Data (`data`):**
```json
{
  "menus": [
    {
      "name": "Main Navigation",
      "slug": "main-nav",
      "location": "header",
      "isActive": true
    }
  ],
  "total": 1
}
```

---

### Get Menu Details
`GET /v1/menu/:slug`

Retrieves the full hierarchical tree for a specific menu slug.

**Response Data (`data`):**
```json
{
  "name": "Main Navigation",
  "slug": "main-nav",
  "location": "header",
  "items": [ ... recursive menu items ... ]
}
```

---

### List All Menu Items
`GET /v1/menu/items`

Retrieves a flat list of all menu items across all menus. Useful for global search or sitemap generation.
