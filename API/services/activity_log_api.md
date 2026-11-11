# Activity Log API Guide

The Activity Log API allows for logging user-driven events for analytics or auditing purposes.

## Base URL
`POST /v1/activity-log`

---

## Log Activity
`POST /v1/activity-log/:type/:id`

Registers an activity log for a specific entity.

**URL Parameters:**
- `type`: The entity type (e.g., `product`, `event`, `blog`).
- `id`: The UUID of the item.

**Request Body:**
| Field | Type | Description |
| :--- | :--- | :--- |
| `action` | `string` | The action performed (e.g., `VIEW`, `SHARE`, `SEARCH`). |

**Example:**
`POST /v1/activity-log/product/6911c78bab835e55263a9cb8`
```json
{
  "action": "VIEW"
}
```
