# Word (Dictionary) API Guide

The Word API provides a comprehensive dictionary or glossary service. It supports linguistic details like etymology, pronunciation, and part of speech, as well as pedagogical content like examples and synonyms.

## Base URL
`GET /v1/word`

---

## Word Statuses
Standard visibility statuses: `PUBLISHED`, `HIDDEN`, `DRAFT`.

---

## Linguistic Features
Each word entry can contain the following specialized fields:
- `definition`: Clear explanation of the word's meaning.
- `partOfSpeech`: Grammatical category (Noun, Verb, Adjective, etc.).
- `phonetic` / `pronunciation`: How to pronounce the word.
- `etymology` / `history`: The origin and development of the word.
- `synonyms` / `antonyms`: Similar and opposite words.
- `examples`: Sentences demonstrating the word's usage.

---

## Endpoints

### List Words
`GET /v1/word`

Retrieves a paginated list of words in the dictionary.

---

### Get Word Details
`GET /v1/word/:slug`

Retrieves the exhaustive linguistic and historical profile for a specific word.

**Response Data (`data`):**
```json
{
  "name": "Earthenware",
  "slug": "earthenware",
  "definition": "Pottery made of clay fired at a low temperature.",
  "partOfSpeech": "Noun",
  "phonetic": "/ˈərTHənˌwer/",
  "pronunciation": "ur-thuhn-wair",
  "etymology": "From Old English 'eorthe' (earth) + 'ware' (goods).",
  "synonyms": ["Pottery", "Ceramics", "Terra cotta"],
  "examples": [
    "The museum has a collection of ancient Roman earthenware."
  ],
  "category": { "title": "Ceramic Types", "slug": "ceramic-types" },
  "metadata": { ... }
}
```

---

## Social & Interactions
- `/v1/word/category`: Browse glossary categories.
- `/v1/word/like/:slug`: Favorite a word.
- `/v1/word/share/:slug`: Track social sharing of word entries.
