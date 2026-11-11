# Interactions API Guide

The Interactions API provides common social and engagement features like liking, following, commenting, and asking questions. These services are cross-modular and apply to products, events, blog posts, and more.

## Base URL
`POST /v1/{service}`

---

## Like Service
`POST /v1/like/:type/:id`

Toggles a "like" for a specific item.

**Path Parameters:**
- `type`: `product`, `event`, `blog`, `collection`, etc.
- `id`: The UUID or slug of the item.

**Endpoints:**
- `GET /v1/like/:type/:id/count`: Get total like count for an item.
- `GET /v1/like/:type/:id/check`: Check if the current user has liked the item.

---

## Follow Service
`POST /v1/follow/:type/:id`

Toggles a "follow" for a specific entity.

**Path Parameters:**
- `type`: `merchant`, `brand`, `user`.

---

## Comment & Rating Service
`POST /v1/comment/:type/:id`

Submits a comment and/or rating for an item.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `content` | `string` | Yes | The comment text |
| `rating` | `number` | No | Score (e.g., 1-5) |
| `images` | `array` | No | List of image IDs |

**Endpoints:**
- `GET /v1/comment/:type/:id`: List approved comments/ratings for an item.
- `GET /v1/comment/:type/rating/stats`: Get overall rating distribution.

---

## Question Service
`POST /v1/question/:type/:id`

Allows users to ask questions specifically to merchants or about products.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `message` | `string` | Yes | The question text |

**Endpoints:**
- `GET /v1/question/:type/:id`: List answered questions for an item.

---

## View Service
`POST /v1/view/:type/:id`

Logs a view activity for a specific item (for analytics).

**Endpoints:**
- `GET /v1/view/:type/:id/check`: Checks if the user has already viewed the item.

---

## Share Service
`POST /v1/share/:type/:id`

Logs a share action on a specific platform.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `platform` | `string` | Yes | `facebook`, `twitter`, `whatsapp`, etc. |
