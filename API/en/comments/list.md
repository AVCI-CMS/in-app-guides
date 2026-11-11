# Comment and Rating API: List Guide

The Comment and Rating API manages user feedback and 1-5 star ratings for products, events, and blog posts.

---

## 📡 List and Submission Endpoints

### 1. List Comments
`GET /v1/comment/:type/:id`

Returns all approved comments and ratings for a specific item (Product, Event, etc.).
**Types:** `product`, `event`, `blog`, `collection`.

---

### 2. Submit Comment
`POST /v1/comment/:type/:id`

Submits a new comment and/or rating.
**Request Body:**
```json
{
  "content": "Great product!",
  "rating": 5,
  "images": ["image_id_1"]
}
```

---

### 📈 Rating Stats
- `GET /v1/comment/:type/rating/stats`: Returns the distribution of ratings (e.g., number of 5 stars, 4 stars, etc.).

---

## 🚦 Approval Process
All comments may fallback to "Pending" status based on system settings. Only approved comments are returned by the public API.
