# Search API: Universal Access Guide

The Search API provides a centralized gateway to discover content across all modules (Product, Blog, Brand, etc.). It supports flexible regex-based search and lightweight autocomplete suggestions.

---

## 📡 Search Endpoints

### 1. Universal Search
`GET /v1/search`

Searches for specified keywords across all platform content. Uses case-insensitive regex matching.

**Query Parameters:**
- `query`: The search term (Required).

**Sample Response:**
```json
{
  "label": "Traditional Pottery Workshop",
  "type": "artist",
  "slug": "traditional-pottery-workshop",
  "description": "...",
  "tumbnail": "image-url"
}
```

---

### 2. Fast Search (Autocomplete)
`GET /v1/search/short`

A lightweight search endpoint optimized for real-time UI suggestions as the user types.

---

## 🚦 Result Types

| Type | Source Module | Description |
| :--- | :--- | :--- |
| `artist` | `Brand` | Artisan or brand profiles. |
| `artwork` | `Product` | Products, items, or goods. |
| `editorial` | `Blog` | Articles and blog posts. |
| `news` | `News` | Announcements and news items. |
