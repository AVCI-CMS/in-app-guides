# Coupon API: List Guide

The Coupon API allows users to check the validity of discount codes and retrieve details about specific promotional offers.

---

## 📡 List Endpoints

### 1. Check Coupon Details
`GET /v1/coupon/check/:code`

Retrieves public information about a coupon code (e.g., `SUMMER20`) to check its existence and terms.

**Path Parameters:**
- `code`: The alphanumeric coupon code.

**Sample Response:**
```json
{
  "code": "SUMMER20",
  "discountType": "PERCENTAGE",
  "discountValue": 20,
  "minOrderAmount": 50,
  "usageTerms": ["Min purchase of $50", "Max discount $20"]
}
```

---

## 🚦 Coupon Statuses
- `ACTIVE`: Valid and eligible for usage.
- `INACTIVE`: Manually disabled.
- `EXPIRED`: Past validity date.
