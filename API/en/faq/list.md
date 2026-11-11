# FAQ API: Usage Guide

The FAQ API provides access to the platform's Knowledge Base. Questions can be clustered into logical groups and hierarchical categories.

---

## 📡 List and Group Endpoints

### 1. List All FAQs
`GET /v1/faq`

Returns all active questions and answers as a flat list.

---

### 2. Get FAQs by Group
`GET /v1/faq/:slug`

Returns details and all questions belonging to a specific topic group (e.g., "Payments", "Shipping").

**Sample Response:**
```json
{
  "title": "Shipping & Delivery",
  "questions": [
    {
      "question": "How do I track my order?",
      "answer": "You can track your order using the link sent to your email..."
    }
  ]
}
```

---

## 💡 Tip
Answers (`answer`) can contain Rich Text; thus it's recommended to render it with appropriate formatting (HTML/Markdown) on the frontend.
