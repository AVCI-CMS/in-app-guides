# News API Guide

The News API delivers time-sensitive announcements, press releases, and industry updates. It supports both internally written content and links to external news sources.

## Base URL
`GET /v1/news`

---

## News Types

| Type | Description |
| :--- | :--- |
| `INTERNAL` | Articles hosted directly on the AVCI-CMS platform. |
| `EXTERNAL` | Snippets and links pointing to third-party news websites. |

---

## Data Structures

### External News Object
When `newsType` is `EXTERNAL`, the `external` object provides the source details:
```json
{
  "url": "https://...",
  "source": "TechCrunch",
  "title": "... ",
  "description": "...",
  "publishedDate": "..."
}
```

---

## Endpoints

### List News Articles
`GET /v1/news`

**Query Parameters:**
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `page` | `number` | Page number |
| `limit` | `number` | Items per page |
| `category` | `string` | Filter by news category slug |
| `language` | `string` | Filter by language code |

---

### Get Latest News
`GET /v1/news/new`

Retrieves the 10 most recent news items, regardless of type.

---

### Get News Details
`GET /v1/news/:slug`

Retrieves the full content for internal news or the complete source metadata for external news.

**Response Data (`data`):**
```json
{
  "id": "news_uuid",
  "title": "AVCI-CMS Launches v2.0",
  "slug": "avcicms-v2-launch",
  "newsType": "INTERNAL",
  "content": "Full article content...",
  "abstract": "Summary of the launch event.",
  "category": [ { "title": "Press Release", "slug": "press" } ],
  "featuredImage": "image_url",
  "metadata": { ... }
}
```

---

## Social & Interactions
- `/v1/news/category`: Explore news categories.
- `/v1/news/like/:slug`: Like a news item.
- `/v1/news/share/:slug`: Track article sharing.
