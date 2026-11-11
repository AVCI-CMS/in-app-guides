# Technical & SEO API Guide

This guide covers technical services including SEO metadata, Sitemaps, RSS feeds, and Badge information.

## SEO Metadata
Most public content modules (Product, Event, Blog, etc.) provide integrated SEO metadata within their detail responses.

**Standard SEO Schema:**
```json
{
  "title": "string",
  "description": "string",
  "keywords": ["string"],
  "openGraph": {
    "title": "string",
    "description": "string",
    "images": [ { "url": "URL" } ]
  },
  "twitter": { "card": "summary_large_image" }
}
```

---

## Sitemap
`GET /v1/sitemap`

The system provides dynamic XML sitemaps for search engines.

| Endpoint | Description |
| :--- | :--- |
| `/v1/sitemap/products` | All active products |
| `/v1/sitemap/brands` | All active brands |
| `/v1/sitemap/blog` | All blog posts |
| `/v1/sitemap/news` | All news articles |
| `/v1/sitemap/events` | All events |

---

## RSS Feeds
`GET /v1/rss`

Standard RSS feeds for content aggregation.

| Endpoint | Description |
| :--- | :--- |
| `/v1/rss/products` | Latest products |
| `/v1/rss/blog` | Latest blog posts |
| `/v1/rss/news` | Latest news |

---

## Badges
Badges are achievements or icons associated with Organizations and Entities.

`GET /v1/badge`

While management is private, public information is usually embedded in the host entity's details (e.g., Organization details).
