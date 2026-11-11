# Question API: List Guide

The Question API enables users to ask direct questions to merchants or about specific products.

---

## 📡 List and Submission Endpoints

### 1. List Questions
`GET /v1/question/:type/:id`

Returns all answered questions for a specific item or merchant.
**Types:** `product`, `merchant`, `brand`.

---

### 2. Ask a Question
`POST /v1/question/:type/:id`

Enables customers to ask a new question.
**Request Body:**
```json
{
  "message": "Are other colors coming for this item?"
}
```

---

## 🚦 Logic and Flow
- Questions are forwarded directly to the merchant (Merchant/Brand).
- Only questions answered by the merchant are listed on the public API (with "answered" status).
