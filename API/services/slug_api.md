# Slug Resolver API Guide

The Slug Resolver is a technical utility that identifies the content type and retrieves the associated data for any given slug. This is helpful for building dynamic routing systems.

## Base URL
`GET /v1/slug`

---

## Resolve Slug
`GET /v1/slug/:slug`

Identifies the module and data associated with a slug.

**Response Data:**
```json
{
  "type": "product | event | blog | ...",
  "data": { 
     /* The actual content object */ 
  },
  "seo": {
    "title": "SEO Title",
    "description": "SEO Description",
    "keywords": ["string"]
  },
  "jsonld": [ { /* Structured data schemas */ } ]
}
```
