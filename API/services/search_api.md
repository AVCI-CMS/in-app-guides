# Search API Guide

The Search API provides a centralized gateway to discover content across the platform's multi-module catalog and editorial sections.

## Base URL
`GET /v1/search`

---

## Result Types

| Type | Source | Description |
| :--- | :--- | :--- |
| `artist` | `Brand` | Creator or artisan profiles. |
| `artwork` | `Product` | Products, items, or works of art. |
| `editorial` | `Blog` | Articles and blog posts. |

---

## Endpoints

### Universal Search
`GET /v1/search`

Performs a case-insensitive regex search across titles, names, and abstracts.

**Query Parameters:**
| Parameter | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `query` | `string` | Yes | The search term (regex matched). |

**Response Data (`data` array item):**
```json
{
  "label": "Traditional Pottery Workshop",
  "type": "artist",
  "slug": "traditional-pottery-workshop",
  "description": "",
  "tumbnail": "image_url_string"
}
```
*Note: The field `tumbnail` is currently used for the result's preview image.*

---

### Autocomplete / Short Search
`GET /v1/search/short`

A lightweight search intended for real-time UI suggestions. It follows the same response format as the universal search but may be optimized for speed.
