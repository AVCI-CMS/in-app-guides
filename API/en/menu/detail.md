# Menu API: Detail and Hierarchy

Used to access the hierarchical tree of all links (items) and sub-menus within a specific menu.

---

## 📄 Detail Endpoints

### 1. Get Menu Details
`GET /v1/menu/:slug`

Returns all items and their recursive sub-divisions (`children`).

**Sample Menu Item:**
```json
{
  "title": "Shop",
  "url": "/catalog",
  "icon": "icon_name",
  "order": 1,
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

## 🔗 List All Items
- `GET /v1/menu/items`: Retrieves a flat list of all menu items across all menus, useful for sitemaps or global search.
