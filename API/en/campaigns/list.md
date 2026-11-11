# Campaign API: List Guide

The Campaign API manages promotional activities, discounts, and marketing campaigns within a workspace. Campaigns can be targeted at specific products, categories, or customer segments.

---

## 📡 List Endpoints

### 1. List Campaigns
`GET /v1/campaign`

Returns all public campaigns as a paginated list.

**Query Parameters:**
- `page`: Page number
- `limit`: Items per page
- `status`: `ACTIVE`, `INACTIVE`, or `EXPIRED` filter.
- `isActive`: List only active ones (`true`/`false`).

---

### 🔥 Active Campaigns
- `GET /v1/campaign/active`: A shortcut to retrieve all currently running campaigns.

---

## 🚦 Campaign Statuses

| Status | Description |
| :--- | :--- |
| `ACTIVE` | The campaign is currently running and eligible for usage. |
| `INACTIVE` | The campaign is manually disabled. |
| `EXPIRED` | The current date is past the `endDate` of the campaign. |
