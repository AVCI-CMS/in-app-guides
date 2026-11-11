# Product API: Detail Guide

Used to access the complete item profile, including stock, variations, price history, and vendor data.

---

## 📄 Detail Endpoints

### 1. Get Product Details
`GET /v1/product/:slug`

Returns the full profile and text content of a product.

**Sample Response:**
```json
{
  "name": "Artisan Ceramic Bowl",
  "slug": "artisan-ceramic-bowl",
  "price": { "amount": 150.00, "sale": 120.00, "currency": "TRY" },
  "stock": { "quantity": 10, "track": true },
  "brand": { "name": "Ceramics Co", "slug": "ceramics-co" },
  "merchant": { "name": "Artisan Goods LTD", "slug": "artisan-goods" }
}
```

---

## 🔗 Related Items and Services
- `/v1/product/like/:slug`: Toggle item favorite.
- `/v1/product/view/:slug`: Log item view analytics.
- `/v1/product/share/:slug`: Track social share activity.
- `/v1/product/category`: Browse item categories.
