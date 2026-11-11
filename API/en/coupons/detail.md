# Coupon API: Validate and Use

Used to validate a coupon code against a specific shopping cart and user.

---

## 📄 Validation Endpoint

### 1. Validate Coupon
`POST /v1/coupon/validate`

Validates a coupon code against a specific cart total and customer.

**Request Body:**
- `code`: The coupon code to validate.
- `cartTotal`: The current total of the shopping cart.
- `customerId`: The UUID of the customer (to check usage limits).

**Response Data:**
```json
{
  "valid": true,
  "discount": 10.00,
  "message": "Coupon applied successfully"
}
```

---

## 🎟️ Discount Types
- `PERCENTAGE`: Percentage-based discount (e.g., 20%).
- `FIXED`: Fixed currency amount discount (e.g., $10).
- `FREE_SHIPPING`: Removes shipping costs from the order.

---

## ⚖️ Usage Constraints
- **minOrderAmount**: The minimum cart subtotal required to use the coupon.
- **availableUsageCount**: Remaining number of times this coupon can be used globally.
- **appliesTo**: Coupons may be restricted to specific **Products** or **Categories** (The validation endpoint handles this logic automatically).
