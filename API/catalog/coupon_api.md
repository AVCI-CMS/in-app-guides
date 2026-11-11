# Coupon API Guide

The Coupon API allows users to check the validity of discount codes and retrieve details about specific promotional offers.

## Base URL
`GET /v1/coupon`

---

## Coupon Statuses

| Status | Description |
| :--- | :--- |
| `ACTIVE` | The coupon code is valid and can be applied. |
| `INACTIVE` | The coupon code is manually disabled. |
| `EXPIRED` | The current date is past the `validUntil` date. |
| `DELETED` | The coupon code has been removed from the system. |

---

## Discount Types

| Type | Description |
| :--- | :--- |
| `PERCENTAGE` | A percentage-based discount (e.g., 20% off). |
| `FIXED` | A fixed currency amount discount (e.g., $10 off). |
| `FREE_SHIPPING` | Removes shipping costs from the order. |

---

## Endpoints

### Check Coupon Details
`GET /v1/coupon/check/:code`

Retrieves public information about a coupon code to check its existence and terms.

**Path Parameters:**
- `code`: The alphanumeric coupon code (e.g., `SUMMER20`).

**Response Data:**
```json
{
  "code": "SUMMER20",
  "discountType": "PERCENTAGE",
  "discountValue": 20,
  "validFrom": "2024-06-01T00:00:00.000Z",
  "validUntil": "2024-08-31T23:59:59.000Z",
  "isActive": true,
  "minOrderAmount": 50,
  "availableUsageCount": 100,
  "usageTerms": [
    "Min purchase of $50",
    "Max discount $20"
  ]
}
```

---

### Validate Coupon
`POST /v1/coupon/validate` (also supports `GET`)

Validates a coupon code against a specific cart total and customer.

**Request Body / Query Parameters:**
| Parameter | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `code` | `string` | Yes | The coupon code to validate |
| `cartTotal` | `number` | Yes | The current total of the shopping cart |
| `customerId` | `string` | No | UUID of the customer (to check usage limits) |

**Response Data:**
```json
{
  "valid": true,
  "coupon": {
    "code": "SUMMER20",
    "discountType": "PERCENTAGE",
    "discountValue": 20,
    "minOrderAmount": 50,
    "usageTerms": ["..."]
  },
  "discount": 10.00,
  "message": "Coupon applied successfully"
}
```

---

## Usage Constraints
- **minOrderAmount**: The minimum cart subtotal required to use the coupon.
- **availableUsageCount**: Remaining number of times this coupon can be used globally.
- **appliesTo (Internal Logic)**: Coupons may be restricted to specific **Products** or **Categories**. The validation endpoint handles this logic automatically based on the provided cart.
