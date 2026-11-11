# Campaign API: Detail Guide

Used to access the scope, discount rates, and application conditions of a single campaign.

---

## 📄 Detail Endpoints

### 1. Get Campaign Details
`GET /v1/campaign/:id`

Returns exhaustive campaign details, including applicable products and participation conditions.

**Sample Response:**
```json
{
  "title": "Summer Sale 2024",
  "startDate": "2024-06-01T00:00:00.000Z",
  "endDate": "2024-08-31T23:59:59.000Z",
  "discountPercentage": 20,
  "conditions": ["Min purchase of $50", "Registered users only"],
  "appliesTo": {
    "products": ["prod_uuid_1"],
    "categories": ["cat_uuid_summer"]
  }
}
```

---

## 📒 Calculation Logic
- **Percentage Discount:** If `discountPercentage` is provided, a percentage is deducted from the total.
- **Fixed Discount:** If `discountAmount` is provided, a fixed value is deducted from the total.

---

## 🎯 Targeting (AppliesTo)
Campaigns can be scoped to:
- **Products**: Only specific item UUIDs.
- **Categories**: All items belonging to specific category UUIDs.
- **Segments**: Targeted at specific user groups (e.g., "New Customers").
