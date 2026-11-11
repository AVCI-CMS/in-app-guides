# Relations API Guide

The Relations API manages many-to-many connections between different entities across the platform. It allows for creating semantic links like "Featured Products for this Event" or "Similar Blog Posts for this Merchant."

## Base URL
`GET /v1/relations`

---

## Relation Categories

| Category | Description |
| :--- | :--- |
| `RELATED` | General semantic connection. |
| `RECOMMENDED` | Algorithmic or manual recommendation. |
| `SIMILAR` | Items with high similarity in type or content. |
| `FEATURED` | Explicitly highlighted connections. |

---

## Supported Module Types
Relations can be established between any combination of these types:
`PRODUCT`, `EVENT`, `BLOG`, `NEWS`, `BRAND`, `MERCHANT`, `PLACE`, `PAGE`, `WORD`, `USER`, `PROJECT`.

---

## Endpoints

### Get Relations for Item
`GET /v1/relations/:moduleType/:slug`

Retrieves all entities related to a specific item.

**Path Parameters:**
- `moduleType`: The type of the source item (e.g., `PRODUCT`).
- `slug`: The slug of the source item.

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `relatedType` | `string` | Filter by type of related items (e.g., `EVENT`) |
| `category` | `string` | Filter by relation category (e.g., `FEATURED`) |

**Response Data (`data` array item):**
```json
{
  "id": "relation_uuid",
  "category": "FEATURED",
  "relatedType": "EVENT",
  "related": {
    "name": "Summer Craft Fair",
    "slug": "summer-craft-fair",
    "date": { ... }
  }
}
```

---

### Get Relations by ID
`GET /v1/relations/id/:moduleType/:moduleId`

Same as above, but uses the unique UUID instead of a slug.

---

### Get Reverse Relations
`GET /v1/relations/reverse/:moduleType/:slug`

Finds all entities that point *to* the specified item. For example, "Which Projects feature this Brand?".

---

## Use Cases
- **Product Upselling**: Link "Related" or "Recommended" products to a specific product.
- **Cross-Promotion**: Link a "Merchant" to the "Events" they are attending.
- **Portfolio**: Link a "Brand" to the "Projects" they have completed.
