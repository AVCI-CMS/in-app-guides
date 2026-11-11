# FAQ API Guide

The FAQ (Frequently Asked Questions) API provides public access to the workspace's support Knowledge Base, organized into logical groups and hierarchical categories.

## Base URL
`GET /v1/faq`

---

## Data Structures

### FAQ Item
| Field | Type | Description |
| :--- | :--- | :--- |
| `question` | `string` | The question text. |
| `answer` | `string` | The detailed answer (may contain HTML/Markdown). |
| `date` | `string` | Publication date. |

### FAQ Group
Groups allow for clustering questions by topic (e.g., "Shipping", "Payments"). Groups can be nested.

---

## Endpoints

### List All FAQs
`GET /v1/faq`

Retrieves a flat list of all active FAQs across all groups.

**Response Data (`data` array item):**
```json
{
  "question": "How do I track my order?",
  "answer": "You can track your order using the link sent to your email...",
  "date": "2024-04-10T11:00:00.000Z",
  "group": {
    "title": "Shipping & Delivery",
    "slug": "shipping-delivery"
  }
}
```

---

### Get Group with Questions
`GET /v1/faq/:slug`

Retrieves the details of a specific FAQ group and all the questions belonging to it.

**Path Parameters:**
- `slug`: The unique slug of the FAQ group.

**Response Data (`data`):**
```json
{
  "title": "Shipping & Delivery",
  "slug": "shipping-delivery",
  "description": "Information about our shipping partners and timelines.",
  "questions": [
    { "question": "...", "answer": "..." }
  ],
  "children": [
    { "title": "International Shipping", "slug": "international" }
  ]
}
```

---

## Usage Tips
- **Search**: For custom search implementations, it's recommended to fetch all FAQs and perform client-side filtering or use the global search endpoint.
- **Rendering**: Answers are intended to be rendered as rich text to preserve formatting and links.
