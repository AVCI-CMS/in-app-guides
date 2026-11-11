# Campaign API Guide

The Campaign API manages promotional activities, discounts, and marketing campaigns within a workspace. Campaigns can be targeted at specific products, categories, or customer segments.

## Base URL
`GET /v1/campaign`

---

## Campaign Statuses

| Status | Description |
| :--- | :--- |
| `ACTIVE` | The campaign is currently running and eligible for usage. |
| `INACTIVE` | The campaign is manually disabled and cannot be used. |
| `EXPIRED` | The current date is past the `endDate` of the campaign. |
| `DELETED` | The campaign has been logically deleted. |

---

## Endpoints

### List Campaigns
`GET /v1/campaign`

Retrieves a paginated list of all public campaigns.

**Query Parameters:**
| Parameter | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `page` | `number` | No | Page number (default: 1) |
| `limit` | `number` | No | Items per page (default: 10) |
| `isActive` | `boolean` | No | Filter by active/inactive status |
| `status` | `string` | No | Filter by `ACTIVE`, `INACTIVE`, or `EXPIRED` |

**Response Data (`data` array item):**
```json
{
  "_id": "6911c78bab835e55263a9cb8",
  "title": "Summer Sale 2024",
  "description": "20% off on all summer essentials.",
  "slug": "summer-sale-2024",
  "startDate": "2024-06-01T00:00:00.000Z",
  "endDate": "2024-08-31T23:59:59.000Z",
  "discountPercentage": 20,
  "discountAmount": 0,
  "isActive": true,
  "status": "ACTIVE",
  "metadata": {
    "featured": true,
    "bannerImage": "image_uuid"
  }
}
```

---

### Get Active Campaigns
`GET /v1/campaign/active`

A shortcut to retrieve all currently running (`isActive: true` and `status: ACTIVE`) campaigns.

---

### Get Campaign Details
`GET /v1/campaign/:_id`

Retrieves comprehensive information about a single campaign, including its scope of application.

**Path Parameters:**
- `_id`: The unique UUID of the campaign.

**Response Data:**
```json
{
  "id": "6911c78bab835e55263a9cb8",
  "title": "Summer Sale 2024",
  "description": "20% off on all summer essentials.",
  "slug": "summer-sale-2024",
  "startDate": "2024-06-01T00:00:00.000Z",
  "endDate": "2024-08-31T23:59:59.000Z",
  "discountPercentage": 20,
  "discountAmount": 0,
  "isActive": true,
  "status": "ACTIVE",
  "conditions": [
    "Min purchase of $50",
    "Only for registered users"
  ],
  "appliesTo": {
    "products": ["prod_uuid_1", "prod_uuid_2"],
    "categories": ["cat_uuid_summer"],
    "customerSegments": ["vip_segment_uuid"]
  },
  "metadata": {
    "promotionalUrl": "https://...",
    "views": 1240
  }
}
```

---

## Implementation Details

### Discount Calculation
- If **`discountPercentage`** is provided, the discount is calculated as a percentage of the total.
- If **`discountAmount`** is provided, it is treated as a fixed value deducted from the total.
- If both are provided, the system logic typically prioritizes one or applies both according to custom business rules (verify with specific integration).

### Scope (AppliesTo)
Campaigns can be scoped to:
- **Products**: Only specific item UUIDs.
- **Categories**: All items belonging to specific category UUIDs.
- **Segments**: Targeted at specific user groups (e.g., "New Customers").
