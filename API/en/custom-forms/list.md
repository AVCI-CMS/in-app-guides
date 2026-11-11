# Custom Form API: Quick Reference

> 💡 **Need deep technical schemas, error codes, and SDK examples?**  
> Read the complete guide at the [AVCI CMS Developer Portal](https://doc.avcicms.com/docs/api/communication/custom-form).

The Custom Form API manages dynamic schema-driven forms, platform applications, surveys, and submission lifecycles.

---

## 📡 Key Endpoints

### 1. List Forms (Management)
* `GET /api/v1/customForm`
* **Query Params:** `page` (default: 1), `limit` (default: 10)
* **Headers:** `x-avci-client: <client-id>`, `Authorization: Bearer <token>`
* Returns paginated form templates including field counts, purpose, and active status.

### 2. Create Form
* `POST /api/v1/customForm`
* Creates a dynamic form template with fields, validations, and approval actions.

---

## 🚦 Application Purposes

| Purpose | Description & Approval Action |
| :--- | :--- |
| `STANDARD` | General data collection, feedback, and custom inquiries. |
| `MERCHANT_APPLICATION` | Vendor onboarding. Approval provisions `Merchant` & onboarding setup. |
| `BRAND_APPLICATION` | Brand registry. Approval provisions `Brand` & brand setup. |
| `ORGANIZATION_APPLICATION` | Cooperative / Chamber application. Approval provisions `Organization`. |
| `SURVEY` | Customer feedback with conversion tracking and submission stats. |

---

## ⚡ Quick Tip
To fetch the public schema of a form on your storefront, call `GET /api/v1/customForm/:formId` with the `x-avci-client` header.

> 📖 **Read Full Documentation:** [Custom Form Developer Guide](https://doc.avcicms.com/docs/api/communication/custom-form)
