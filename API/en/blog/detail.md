# Blog API: Article Detail Guide

Used to access the full content, SEO data, and interactions of a single article.

---

## 📄 Detail Endpoints

### 1. Get Blog Details
`GET /v1/blog/:slug`

Returns the full content (HTML/Markdown) and all metadata information of the article.

**Response Schema:**
```json
{
  "id": "blog-uuid",
  "title": "Article Title",
  "content": "Content Text...",
  "featuredImage": "cover-image-url",
  "gallery": ["image-1", "image-2"],
  "metadata": {
    "author": "Author Name",
    "seo": { "title": "SEO Title", "description": "SEO Description" }
  }
}
```

---

## 💬 Interactions
Actions associated with the detail page:
- `/v1/blog/like/:slug`: Increments the like count.
- `/v1/blog/comment/:slug`: Manages comments.
- `/v1/blog/share/:slug`: Updates share counts.
