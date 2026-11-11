# Collection API Guide

Collections are curated groupings of entities (Products, Events, Merchants, etc.) used for featured sections, theme-based listings, or promotional highlights. They can be linked to specific campaigns and coupons.

## Base URL
`GET /v1/collection`

---

## Collection Statuses

| Status | Description |
| :--- | :--- |
| `ACTIVE` | Publicly visible and active. |
| `DRAFT` | Hidden from public views. |
| `ARCHIVED` | Deprecated collection kept for records. |

---

## Endpoints

### List Collections
`GET /v1/collection/:type`

Retrieves a list of active collections for a specific item type.

**Path Parameters:**
- `type`: The item type contained in the collection (e.g., `product`, `merchant`, `blog`).

**Response Data (`data` array item):**
```json
{
  "_id": "6911c78bab835e55263a9cb8",
  "title": "Summer Favorites",
  "slug": "summer-favorites",
  "itemsCount": 15,
  "featuredImage": { "url": "..." },
  "order": 1
}
```

---

### Get Collection Details
`GET /v1/collection/:type/:slug`

Retrieves the full list of items within a collection, along with optional campaign or curator data.

**Response Data (`data`):**
```json
{
  "title": "Summer Favorites",
  "slug": "summer-favorites",
  "description": "Our hand-picked selection for the summer.",
  "items": [
    "item_uuid_1", "item_uuid_2"
  ],
  "campaign": "campaign_uuid",
  "coupon": "coupon_uuid",
  "curator": {
    "name": { "first": "John", "last": "Doe" }
  },
  "metadata": { ... }
}
```

---

## Social & Interactions
Collections support engagement tracking:
- `POST /v1/collection/like/:slug`: Favorite a collection.
- `POST /v1/collection/share/:slug`: Log social shares.
- `GET /v1/collection/comment/:slug`: View/Post discussions on the collection.
- `GET /v1/collection/question/:slug`: Q&A specifically for the collection.
