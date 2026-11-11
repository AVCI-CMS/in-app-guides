# News API: List Guide

The News API provides access to announcements, press releases, and industry updates. It supports both internal content and external news sources.

---

## 📡 List Endpoints

### 1. List News
`GET /v1/news`

Returns paginated news items.

**Query Parameters:**
- `page`: Page number
- `limit`: Items per page
- `category`: Category slug
- `language`: Language code (`en`, `tr`)
- `type`: `INTERNAL` or `EXTERNAL`

---

### 2. Get Latest News
`GET /v1/news/new`

Retrieves the 10 most recent news items.

---

## 🚦 News Types

| Type | Description |
| :--- | :--- |
| `INTERNAL` | Content hosted directly on AVCI-CMS. |
| `EXTERNAL` | Summaries and links redirecting to external news sites. |
