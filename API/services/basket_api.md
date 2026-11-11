# Basket API Guide

The Basket API allows users to manage their shopping carts, supporting both products and event tickets. It tracks items, quantities, and real-time total calculations.

## Base URL
`GET /v1/basket`

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

### Get My Basket
`GET /v1/basket`

Retrieves the active basket for the authenticated user. If no basket exists, it may return a 404 or an empty structure depending on the tenant configuration.

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
`POST /v1/basket/add`

Adds items to the current basket.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `items` | `array` | Yes | List of `{ id, quantity, itemType }` objects |

*Note: `itemType` must be either `product` or `event` (and `route` when the catalog supports routes).*

**Important for ticket items:** When the basket contains **event** or **route** items, the tenant must collect **participant (attendee) information** at checkout and send it in the order/purchase request. See [Order API – Participant information for ticket items](order_api.md#participant-information-for-ticket-items-event--route) and [Purchase API](purchase_api.md) for the required `participants` payload.

**Capacity reservation (cart lock):** The platform may temporarily reserve capacity for event/route items when they are added to the basket (e.g. for 10 minutes via Redis), so that the user can complete checkout without losing the slot. Details are backend-specific; see [Order API – Backend implementation notes](order_api.md#backend-implementation-notes-reference).

---

### Update Item Quantity
`PUT /v1/basket/update/:itemId/:action`

**Path Parameters:**
- `itemId`: The UUID of the item in the basket.
- `action`: `increase` or `decrease`.

Automatically recalculates basket totals.

---

### Clear Basket
`DELETE /v1/basket`

Removes all items and resets the basket state.
