# Basket API: Usage Guide

The Basket API enables users to manage shopping carts containing both physical products and event tickets. It tracks quantities, price calculations, and cart reservations.

---

## 📡 Core Endpoints

### 1. Get My Basket
`GET /v1/basket`

Returns the active basket for the authenticated user, including items and totals.

### 2. Add Items to Basket
`POST /v1/basket/add/:basketId`

Adds new products or event tickets to the specified cart.
**Request Body:**
```json
{
  "items": [
    { "id": "item_uuid", "quantity": 2, "itemType": "product" }
  ]
}
```

### 3. Update Quantity / Currency / Clear
- `PUT /v1/basket/update/:basketId/:itemId/increase`: Increments quantity.
- `PUT /v1/basket/update/:basketId/:itemId/decrease`: Decrements quantity.
- `PUT /v1/basket/currency/:basketId`: Changes cart active currency.
- `DELETE /v1/basket/clear/:basketId`: Clears the entire basket.

---

## 🎟️ Tickets and Reservations
- **Capacity Lock:** When event items are added to the basket, the platform temporarily reserves capacity (e.g., for 10 min).
- **Participant Info:** If the basket contains `event` or `route` items, participant information is required at checkout.

---

## 🔗 Documentation Link
For detailed guides and SDK usage, visit [AVCI CMS Basket Documentation](https://doc.avcicms.com/api/finance/basket).

