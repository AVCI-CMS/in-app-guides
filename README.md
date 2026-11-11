# AVCI CMS — In-App Contextual Guides (`in-app-guides`)

[![AVCI CMS Ecosystem](https://img.shields.io/badge/AVCI%20CMS-Ecosystem-blue.svg)](https://avcicms.com)
[![Documentation](https://img.shields.io/badge/Docs-doc.avcicms.com-emerald.svg)](https://doc.avcicms.com)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-orange.svg)](https://avcicms.com)

This repository hosts the **contextual in-panel quick guides** for the **AVCI CMS Management Dashboard**.

Instead of forcing operators, merchants, and developers to switch back and forth between the admin panel and external documentation portals, AVCI CMS embeds these lightweight guides directly inside the interface via the slide-over **Right Toolbar** (`RightToolbar`).

---

## 🎯 Purpose & Design Philosophy

The in-app guides system is built around three core principles:

1. **Zero Context Switching:** Users view relevant operational workflows (`HELP`) and REST API endpoints (`API`) directly alongside the active screen they are working on (e.g., viewing Product API schemas while editing a product).
2. **Scannable & Action-Oriented:** Content is strictly optimized for quick reads — bullet points, status tables, query parameter summaries, and pro-tips. Long conceptual essays are forbidden here.
3. **Deep Portal Referrals:** Every guide includes a prominent referral callout to the full, comprehensive developer portal at [doc.avcicms.com](https://doc.avcicms.com) for exhaustive payload schemas, SDK methods, and error dictionaries.

---

## 📂 Repository Structure

The guides are partitioned by **Guide Type** (`API` vs. `HELP`), **Language Code** (`en`, `tr`), and **Module**:

```
in-app-guides/
├── API/                          # Developer & Integrator API References
│   ├── en/                       # English API Guides
│   │   ├── blog/
│   │   ├── products/
│   │   │   ├── list.md           # Displayed on /products (list screen)
│   │   │   └── detail.md         # Displayed on /products/[id]/edit (detail screen)
│   │   ├── custom-forms/
│   │   │   ├── list.md
│   │   │   └── detail.md
│   │   └── ...                   # (merchants, orders, payments, campaigns, etc.)
│   └── tr/                       # Turkish API Guides
│       ├── products/
│       └── ...
└── HELP/                         # Operator, Merchant & Editor User Guides
    ├── en/                       # English Operational Guides
    │   ├── products/
    │   │   ├── list.md
    │   │   └── detail.md
    │   └── ...
    └── tr/                       # Turkish Operational Guides
        ├── products/
        └── ...
```

---

## 🔄 Dynamic In-Panel Route Resolution

When an operator or developer clicks the **Code (`API`)** or **Question (`HELP`)** icon in the AVCI CMS Right Toolbar, the frontend dynamically resolves the document path based on the current Next.js route:

| Current Dashboard Route | Target Screen Type | Resolved Guide Path |
| :--- | :--- | :--- |
| `/products` | List Screen | `guides/{type}/{locale}/products/list.md` |
| `/products/create` | Detail / Editor | `guides/{type}/{locale}/products/detail.md` |
| `/products/664a7.../edit` | Detail / Editor | `guides/{type}/{locale}/products/detail.md` |
| `/custom-forms` | List Screen | `guides/{type}/{locale}/custom-forms/list.md` |
| `/custom-forms/665.../answers` | Detail / Review | `guides/{type}/{locale}/custom-forms/detail.md` |
| `/tools/slider` | Tool Screen | `guides/{type}/{locale}/slider/list.md` |

### Supported Core Modules
- **Content & Catalog:** `blog`, `news`, `products`, `events`, `pages`, `dictionary`, `projects`
- **Multi-Tenant Relations:** `merchants`, `brands`, `organizations`, `places`
- **Marketing & Engagement:** `custom-forms`, `campaigns`, `coupons`, `newsletter`, `contact-forms`, `faq`, `tickets`
- **Commerce & Operations:** `orders`, `payments`, `basket`
- **Services & Media:** `media`, `menu`, `slider`, `notifications`, `comments`, `questions`, `search`

---

## ⚙️ Connecting to an AVCI CMS Workspace

AVCI CMS allows tenants to use this default repository or point to their own private/custom documentation fork:

1. In the CMS panel, navigate to:  
   **`Workspace > Settings > Appearance > Guides`**
2. Ensure your **GitHub Integration** is connected in `Workspace > Integrations`.
3. Configure your documentation repository:
   * **Repository Name:** `AVCI-CMS/in-app-guides` (or your company's custom fork, e.g. `your-org/my-cms-guides`)
   * **Branch:** `main` (or a dedicated staging branch like `drafts`)
4. Save changes. The AVCI CMS backend synchronizes and caches the Markdown files seamlessly.

---

## ✍️ Authoring Standards for In-App Guides

When contributing or adding new guides to this repository, adhere strictly to the following formatting rules:

### 1. Mandatory Referral Callout (Top & Bottom)
Always place a clear callout at the top directing readers to the master developer portal:
```markdown
# Product API: Quick Reference

> 💡 **Need deep technical schemas, error codes, and SDK examples?**  
> Read the complete guide at the [AVCI CMS Developer Portal](https://doc.avcicms.com/docs/api/catalog/products).
```

### 2. Compact Parameter & Status Tables
Use Markdown tables instead of long narrative paragraphs:
```markdown
## 🚦 Entity Statuses

| Status | Description | Actionable By |
| :--- | :--- | :--- |
| `DRAFT` | Initial draft state. Not visible on storefronts. | Editor / Merchant |
| `PENDING_APPROVAL` | Submitted for operational review. | Operator / Admin |
| `PUBLISHED` | Active and publicly visible. | Automated / Admin |
```

### 3. Clear Endpoint Signatures
Document the HTTP verb, path, query parameters, and essential headers clearly:
```markdown
## 📡 Key Endpoints

### 1. List Products
* `GET /api/v1/product`
* **Query Params:** `page`, `limit`, `category`, `search`, `status`
* **Required Headers:** `x-avci-client: <client-id>`
```

### 4. Length Constraint
An in-app guide should not exceed **80-120 lines**. If more detail is required, add it to the Docusaurus portal (`doc.avcicms.com`) and link to it.

---

## 🛠️ Local Development & Preview

In local development mode (`NODE_ENV=development`), the AVCI CMS frontend serves these Markdown files directly from your local filesystem at `frontend/app/api/docs/[...path]/route.ts`:

```bash
# Relative directory structure expected during local development:
AVCI-CMS/
├── frontend/        # Next.js Dashboard
├── guides/          # This repository (cloned locally as 'guides')
└── ...
```

---

## 📄 License & Intellectual Property

Copyright © 2026 AVCI CMS Ecosystem & Kurucu Bireysel Fikri Mülkiyet (IP) Kalkanı.  
All rights reserved. Unauthorized reproduction, distribution, or commercial reuse without explicit written consent is strictly prohibited.

