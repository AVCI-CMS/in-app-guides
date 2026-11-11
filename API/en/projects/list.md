# Project API: List Guide

The Project API showcases architectural, design, or business projects. It provides a rich structure for displaying team members and client info.

---

## 📡 List Endpoints

### 1. List Projects (Paginated)
`GET /v1/project`

**Query Parameters:**
- `page`: Page number
- `limit`: Items per page
- `category`: Category slug
- `year`: Project year filter
- `search`: Search within titles or abstracts

---

## 🚦 Project Statuses

| Status | Description |
| :--- | :--- |
| `ACTIVE` | Project is live and publicly viewable. |
| `ARCHIVED` | Past project kept for reference. |
