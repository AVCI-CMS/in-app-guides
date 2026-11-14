# Basket API Guide

The Basket API allows users to manage their shopping carts, supporting both products and event tickets. It tracks items, quantities, multi-merchant groupings, and real-time total calculations.

## Base URL
`GET /v1/basket`

> For full developer documentation and SDK examples, visit [AVCI CMS Basket Documentation](https://doc.avcicms.com/api/finance/basket).

---

## Data Structures

### Basket Item Object
An extension of the standard item log, including the date it was added.
```json
{
  "_id": "item_uuid",
  "name": "Ceramic Bowl",
  "slug": "ceramic-bowl",
  "quantity": 2,
  "type": "product",
  "price": { "amount": 150, "currency": "TRY" },
  "image": "image_url",
  "addedToBasketAt": "2023-10-01T..."
}
```

---

## Endpoints

### Create or Initialize Basket
`POST /v1/basket`

Initializes a new basket or updates currency settings.

---

### Get My Basket
`GET /v1/basket` or `GET /v1/basket/:basketId`

Retrieves the active basket for the authenticated user or by basket ID. If no basket exists, it returns an empty structure.

**Response Data (`data`):**
```json
{
  "basketId": "unique_basket_id",
  "items": [ ... ],
  "price": {
    "total": 300,
    "currency": "TRY",
    "discount": 0
  },
  "coupon": "optional_coupon_id",
  "updatedAt": "..."
}
```

---

### Add Items to Basket
`POST /v1/basket/add/:basketId`

Adds items to the specified basket.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `items` | `array` | Yes | List of `{ id, quantity, itemType }` objects |

*Note: `itemType` must be either `product` or `event` (and `route` when the catalog supports routes).*

**Important for ticket items:** When the basket contains **event** or **route** items, the tenant must collect **participant (attendee) information** at checkout and send it in the order/purchase request. See [Order API – Participant information for ticket items](order_api.md#participant-information-for-ticket-items-event--route) for the required `participants` payload.

**Capacity reservation (cart lock):** The platform temporarily reserves capacity for event/route items when they are added to the basket (e.g., 10 minutes via Redis), so that the user can complete checkout without losing the slot.

---

### Update Item Quantity
`PUT /v1/basket/update/:basketId/:itemId/:action`

**Path Parameters:**
- `basketId`: Basket ID
- `itemId`: The UUID of the item in the basket.
- `action`: `increase` or `decrease`.

Automatically recalculates basket totals.

---

### Change Basket Currency
`PUT /v1/basket/currency/:basketId`

**Request Body:**
```json
{
  "currency": "USD"
}
```

---

### Clear Basket
`DELETE /v1/basket/clear/:basketId`

Removes all items and resets the basket state.

---

## 🔗 Official Documentation
- [AVCI CMS Basket API Reference](https://doc.avcicms.com/api/finance/basket)

