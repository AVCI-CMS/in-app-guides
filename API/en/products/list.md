# Product API: List Guide

The Product API is the heart of the AVCI-CMS catalog. It provides comprehensive access to physical, digital, and service-based products.

---

## 📡 List Endpoints

### 1. List Products (Paginated)
`GET /v1/product`

**Query Parameters:**
- `page`: Page number (e.g., `1`)
- `limit`: Items per page (e.g., `20`)
- `category`: Category slug or ID
- `brand`: Brand slug
- `merchant`: Merchant slug
- `minPrice` / `maxPrice`: Price range
- `search`: Keyword search

---

### 🛍️ Featured Item Groups
- `GET /v1/product/new`: Recently added items.
- `GET /v1/product/popular`: Most viewed or sold items.
- `GET /v1/product/random/:amount`: A random selection of items.

---

## 🚦 Product Statuses

| Status | Description |
| :--- | :--- |
| `PUBLISHED` | Product is live and buyable. |
| `OUT_OF_STOCK` | Stock has run out. |
| `SOLD_OUT` | Product no longer available (for unique items). |
| `HIDDEN` | Hidden from search and list pages. |
