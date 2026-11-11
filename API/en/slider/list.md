# Slider API: List Guide

The Slider API manages carousel structures for websites and mobile applications, used for "Hero" areas and campaign showcases.

---

## 📡 List Endpoints

### 1. List Sliders
`GET /v1/slider`

Returns a summary list (title, slug, type) of all active sliders.

**Required Header:**
- `x-avci-workspace`: Tenant workspace ID (mandatory).

**Sample Response:**
```json
{
  "data": [
    {
      "title": "Home Page Hero",
      "slug": "home-page-hero",
      "type": "hero"
    }
  ]
}
```

---

## 🚦 Statuses
Only sliders and slides with `PUBLISHED` status are returned via the public API.
