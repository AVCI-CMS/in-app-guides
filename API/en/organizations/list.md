# Organization API: List Guide

The Organization API manages the profiles of corporate entities, institutions, and umbrella organizations within the platform.

---

## 📡 List Endpoints

### 1. List Organizations
`GET /v1/organization`

Returns all active organizational profiles as a paginated list.

**Query Parameters:**
- `page`: Page number
- `limit`: Items per page
- `search`: Search by name or description

---

## 🚦 Organization Statuses
- `ACTIVE`: Fully registered and live corporate profile.
- `DRAFT`: Profile in development.

---

## 🏗️ Data Structure Summary
| Field | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | The organization's trading or primary name. |
| `corporateName` | `string` | Legal registered entity name. |
| `corporationType` | `string` | Type of legal entity (e.g., Sole Proprietorship, LLC). |
| `website` | `string` | Official website URL. |
