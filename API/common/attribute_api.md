# Attribute API Quick Reference

> 💡 **Need deep technical schemas, error codes, and SDK examples?**  
> Read the complete guide at the [AVCI CMS Developer Portal](https://doc.avcicms.com/docs/api/common/attribute).

The Common Attribute API manages Entity-Attribute-Value (EAV) schemas across all catalog and relational entities in AVCI CMS (`product`, `project`, `event`, `merchant`, `brand`, `organization`, and `place`).

---

## 📡 Key Endpoints

### 1. Storefront Filter List
* `GET /api/v1/attribute/:type`
* **Path Parameter:** `type` (`product`, `project`, `event`, `merchant`, `brand`, `organization`, `place`)
* **Header:** `x-avci-client: <client-id>`
* Returns active attributes with their configured options for storefront sidebar filters.

### 2. Dynamic Source Options
* `GET /api/v1/attribute/:type/source-options`
* Dynamically fetches options for `SOURCE` data type attributes linked to other entities.

### 3. Management Operations (CRUD & Bulk)
* `GET /api/v1/attribute/:type?page=1&limit=20` (Paginated list)
* `GET /api/v1/attribute/:type/list` (Simplified list for form dropdowns)
* `GET /api/v1/attribute/:type/check?key=...` (Key availability validation)
* `POST /api/v1/attribute/:type` (Create attribute)
* `PUT /api/v1/attribute/:type/:id` (Update attribute)
* `DELETE /api/v1/attribute/:type/:id` (Delete single attribute)
* `DELETE /api/v1/attribute/:type/bulk` (Bulk delete, body: `{ ids: [] }`)
* `PUT /api/v1/attribute/:type/bulk/status` (Bulk status, body: `{ ids: [], status: "PASSIVE" }`)

---

## ⚡ Normalized EAV Schema
All entities persist attributes using the normalized structure with automatic `label` backward compatibility:
```json
{
  "attributes": [
    {
      "attributeId": "65f1a2b3c4d5e6f7a8b9c0d1",
      "label": "65f1a2b3c4d5e6f7a8b9c0d1",
      "value": "100% Organic Cotton",
      "unit": "GSM"
    }
  ]
}
```

> 📖 **Read Full Documentation:** [Attribute API Developer Guide](https://doc.avcicms.com/docs/api/common/attribute)
