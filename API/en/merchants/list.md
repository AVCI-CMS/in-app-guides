# Merchant API: List Guide

The Merchant API manages the legal and business profiles of vendors. While a "Brand" represents a creative identity, a "Merchant" represents the legal entity responsible for sales, taxation, and logistics.

---

## 📡 List Endpoints

### 1. List Merchants
`GET /v1/merchant`

Returns all active merchants as a paginated list.

**Query Parameters:**
- `page`: Page number
- `limit`: Items per page
- `search`: Search by name or description

---

### 📍 Map Services
- `GET /v1/merchant/location`: Returns coordinates for all active merchants, optimized for map rendering.

---

## 🚦 Merchant Statuses
- `ACTIVE`: Onboarded and open for trade.
- `PENDING`: Application under review.
- `DRAFT`: Profile incomplete.
