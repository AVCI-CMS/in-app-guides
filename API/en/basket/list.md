# Basket API: Usage Guide

The Basket API enables users to manage shopping carts containing both physical products and event tickets. It tracks quantities, price calculations, and cart reservations.

---

## 📡 Core Endpoints

### 1. Get My Basket
`GET /v1/basket`

Returns the active basket for the authenticated user, including items and totals.

### 2. Add Items to Basket
`POST /v1/basket/add`

Adds new products or event tickets to the cart.
**Request Body:**
```json
{
  "items": [
    { "id": "item_uuid", "quantity": 2, "itemType": "product" }
  ]
}
```

### 3. Update Quantity / Clear
- `PUT /v1/basket/update/:itemId/increase`: Increments quantity.
- `PUT /v1/basket/update/:itemId/decrease`: Decrements quantity.
- `DELETE /v1/basket`: Clears the entire basket.

---

## 🎟️ Tickets and Reservations
- **Capacity Lock:** When event items are added to the basket, the platform may temporarily reserve capacity (e.g., for 10 min).
- **Participant Info:** If the basket contains `event` or `route` items, participant information is required at checkout.
