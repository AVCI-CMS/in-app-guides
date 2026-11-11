# Menu API: List Guide

The Menu API manages hierarchical navigation structures (Header, Footer, Sidebar, etc.) for websites and mobile applications.

---

## 📡 List Endpoints

### 1. List Menus
`GET /v1/menu`

Returns a list of all configured menus for the workspace.

**Sample Response:**
```json
{
  "menus": [
    {
      "name": "Main Navigation",
      "slug": "main-nav",
      "location": "header",
      "isActive": true
    }
  ]
}
```

---

## 🚦 Locations
- `header`: Top navigation area.
- `footer`: Bottom-of-the-page area.
- `sidebar`: Side panel navigation.
- `custom`: Special placement areas.
