# JSON-LD API Guide

The JSON-LD API provides structured data for search engine optimization, allowing crawlers to understand the context of various content types.

## Base URL
`GET /v1/json-ld`

---

## Endpoints

### Workspace JSON-LD
`GET /v1/json-ld/`

Retrieves the organization/web-identity schema for the current workspace.

---

### Product JSON-LD
`GET /v1/json-ld/product/:slug`

Retrieves the `Product` schema for a specific item.

---

### Blog / News JSON-LD
`GET /v1/json-ld/blog/:slug`
`GET /v1/json-ld/news/:slug`

Retrieves the `Article` or `BlogPosting` schema.

---

### Other Entities
The following entities also support JSON-LD schema retrieval:
- `event`
- `project`
- `page`
- `word`
- `merchant`
- `brand`
- `place`
- `organization`
