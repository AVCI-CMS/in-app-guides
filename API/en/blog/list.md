# Blog API: List Guide

Used to list, filter, and search for blog posts registered in the CMS.

---

## 📡 List Endpoints

### 1. List Blog Posts
`GET /v1/blog`

Returns all published articles in a paginated format.

**Query Parameters:**
- `page`: Page number (Default: `1`)
- `limit`: Items per page (Max: `100`)
- `category`: Filter by category slug
- `language`: Language code (`en`, `tr`)
- `status`: Publication status (Only `PUBLISHED` in public API)

---

### 2. Get New Posts
`GET /v1/blog/new`

Returns the most recently published 5-10 articles for quick access.

---

## 🚦 Important Statuses
Blog post statuses are:
- `PUBLISHED`: Live
- `DRAFT`: Draft (Not in the list)
- `HIDDEN`: Not live (Not in the list)
