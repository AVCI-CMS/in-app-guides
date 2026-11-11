# Dictionary (Word) API: Detail Guide

Used to access the full linguistic and historical profile of a specific word or term.

---

## 📄 Detail Endpoints

### 1. Get Word Details
`GET /v1/word/:slug`

Returns the definition, pronunciation, origin, and sample usages.

**Sample Response:**
```json
{
  "name": "Ceramics",
  "slug": "ceramics",
  "definition": "The art of making objects from clay hardened by heat.",
  "partOfSpeech": "Noun",
  "phonetic": "/səˈramɪks/",
  "etymology": "From Greek 'keramos' (potter's clay).",
  "synonyms": ["Pottery", "Earthenware"],
  "examples": [
    "Anatolia has a long tradition of ceramics."
  ]
}
```

---

## 💬 Social & Interactions
- `/v1/word/category`: Browse categories.
- `/v1/word/like/:slug`: Add word to favorites.
- `/v1/word/share/:slug`: Track share metrics.
