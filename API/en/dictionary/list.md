# Dictionary (Word) API: List Guide

The Dictionary API provides a comprehensive glossary or term management service. It supports linguistic details like etymology, pronunciation, and part of speech.

---

## 📡 List Endpoints

### 1. List Words
`GET /v1/word`

Returns paginated dictionary items.

**Query Parameters:**
- `page`: Page number
- `limit`: Items per page
- `category`: Dictionary category
- `language`: Language code (`en`, `tr`)
- `search`: Search within words or definitions

---

## 🚦 Basic Statuses
- `PUBLISHED`: Live and visible in the dictionary.
- `HIDDEN`: Accessible only via direct link.
- `DRAFT`: Under development.
