# Product API Guide

The Product API is the core of the AVCI-CMS catalog, providing comprehensive access to physical, digital, and service-based items. It supports advanced filtering, variant management, and social interactions.

## Base URL
`GET /v1/product`

---

## Product Statuses

| Status | Description |
| :--- | :--- |
| `PUBLISHED` | Product is live and available. |
| `OUT_OF_STOCK` | Product exists but has zero inventory. |
| `SOLD` / `SOLD_OUT` | Product is no longer available (usually for unique items). |
| `HIDDEN` | Product is temporarily removed from search and listings. |

---

## Technical Specifications

| Property | Description |
| :--- | :--- |
| `type` | `PHYSICAL`, `DIGITAL`, or `SERVICE`. |
| `saleType` | `UNIT`, `PAIR`, `PACKAGE`, or `TEAM`. |
| `sku` | Stock Keeping Unit (Unique Identifier). |
| `stock` | Current inventory levels (`amount`, `min`). |
| `edition` | For unique/limited items (`number` of `amount`). |

---

## Endpoints

### List Products (Paginated)
`GET /v1/product`

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number (default: 1) |
| `limit` | `number` | Items per page (default: 10) |
| `category` | `string` | Filter by category slug or ID |
| `brand` | `string` | Filter by brand slug |
| `merchant` | `string` | Filter by merchant slug |
| `minPrice` / `maxPrice` | `number` | Price range filters |
| `attributes` | `json` | Filter by attribute values (JSON string) |
| `search` | `string` | Keyword search across titles/abstracts |

---

### Specialized Listings
- `GET /v1/product/new`: Recently added products.
- `GET /v1/product/popular`: Products with highest interaction/sales.
- `GET /v1/product/random/:amount`: Retrieve a selection of random items.

---

### Get Product Details
`GET /v1/product/:slug`

Retrieves full product data, including technical properties, merchant info, and images.

**Response Data (`data`):**
```json
{
  "id": "prod_uuid",
  "name": "Handmade Ceramic Vase",
  "slug": "handmade-ceramic-vase",
  "year": 2024,
  "sku": "CER-001",
  "price": {
    "amount": 85.00,
    "sale": 75.00,
    "currency": "USD",
    "discount": 10
  },
  "brand": { "name": "ClayCraft", "slug": "claycraft" },
  "merchant": { "name": "Artisan Hall", "slug": "artisan-hall" },
  "techniques": ["Hand-thrown", "Glazed"],
  "materials": ["Earthenware Clay", "Natural Pigments"],
  "tools": ["Pottery Wheel", "Kiln"],
  "attributes": [
    { "label": "Color", "value": "Blue" },
    { "label": "Height", "value": "20", "unit": "cm" }
  ],
  "stock": { "amount": 12, "min": 2 },
  "images": ["url_1", "url_2"],
  "description": "Full HTML/Markdown description...",
  "shipment": { "weight": 1.5, "dimensions": "..." }
}
```

---

## Integrated Services
Products seamlessly integrate with shared catalog services:
- `/v1/product/category`: Browse categories relevant to products.
- `/v1/product/attribute`: Find searchable attributes.
- `/v1/product/like/:slug`: engagement tracking.
- `/v1/product/comment/:slug`: Reviews and ratings.
- `/v1/product/question/:slug`: Product Q&A.
