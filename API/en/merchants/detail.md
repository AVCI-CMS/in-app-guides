# Merchant API: Detail Guide

Used to access the complete business profile, including corporate data, bank information, and operational settings.

---

## 📄 Detail Endpoints

### 1. Get Merchant Details
`GET /v1/merchant/:slug`

Returns exhaustive business profile, including corporate data and address.

**Sample Response:**
```json
{
  "name": "Artisan Collective",
  "corporateName": "Artisan Goods LTD",
  "slug": "artisan-collective",
  "taxNumber": 123456789,
  "taxOffice": "Kadikoy VD",
  "address": { "city": "Istanbul", "street": "..." },
  "badges": [ { "title": "Top Seller" } ]
}
```

---

### 🃏 Card View
- `GET /v1/merchant/card/:slug`: Retrieves a condensed profile for UI cards and list displays.

---

## 💬 Social & Interactions
- `/v1/merchant/follow/:slug`: Follow a merchant.
- `/v1/merchant/like/:slug`: Like a profile.
- `/v1/merchant/view/:slug`: Log a view.
- `/v1/merchant/question/:slug`: Message or Q&A specifically for the vendor.
