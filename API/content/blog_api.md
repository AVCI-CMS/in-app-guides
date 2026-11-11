# Blog API Guide

The Blog API provides access to articles, tutorials, and announcements. It supports multi-language translations, rich media galleries, and integrated social interactions.

## Base URL
`GET /v1/blog`

---

## Blog Statuses

| Status | Description |
| :--- | :--- |
| `PUBLISHED` | Article is live and publicly viewable. |
| `HIDDEN` | Article exists but is removed from public lists. |
| `DRAFT` | Article is under preparation. |

---

## Endpoints

### List Blog Posts (Paginated)
`GET /v1/blog`

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number |
| `limit` | `number` | Items per page |
| `category` | `string` | Filter by category slug |
| `language` | `string` | Filter by language code (e.g., `en`, `tr`) |

---

### Get New Posts
`GET /v1/blog/new`

Retrieves a selection of the most recently published articles.

---

### Get Blog Details
`GET /v1/blog/:slug`

Retrieves the full content of an article, including metadata for SEO and translations.

**Response Data (`data`):**
```json
{
  "id": "blog_uuid",
  "title": "The Art of Traditional Pottery",
  "slug": "art-traditional-pottery",
  "status": "PUBLISHED",
  "content": "Full HTML/Markdown content...",
  "abstract": "A brief introduction to pottery techniques.",
  "featuredImage": "image_url",
  "readingTime": 5,
  "category": [ { "title": "Craftsmanship", "slug": "craftsmanship" } ],
  "gallery": ["url_1", "url_2"],
  "languages": ["en", "tr"],
  "metadata": { "author": "Jane Doe", "seo": { ... } }
}
```

---

## Social & Interactions
Blog posts support integrated engagement features:
- `/v1/blog/category`: Browse blog categories.
- `/v1/blog/like/:slug`: Like an article.
- `/v1/blog/comment/:slug`: Community discussions and ratings.
- `/v1/blog/share/:slug`: Tracking social shares.
