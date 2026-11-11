# Follow API Guide

The Follow API allows users to follow and unfollow various entities (Products, Brands, Merchants, etc.) to receive updates or keep track of them.

## Base URL
`GET /v1/follow`

---

## Endpoints

### List My Follows
`GET /v1/follow/:type`

Retrieves a list of items the authenticated user is currently following for a specific type.
- `type`: `product`, `brand`, `merchant`, etc.

---

### Toggle Follow
`POST /v1/follow/:type/:id`

Toggles the follow status for a specific item. If the user is already following, it will unfollow.

**Response Data:**
```json
{
  "following": true | false,
  "message": "Successfully followed/unfollowed"
}
```

---

### Check Follow Status
`GET /v1/follow/:type/:id`

Checks if the authenticated user is following a specific item.

---

### Get Follow Count
`GET /v1/follow/:type/:id/count`

Retrieves the total number of followers for a specific item.
