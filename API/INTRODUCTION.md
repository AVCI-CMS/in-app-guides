# AVCI-CMS Public API Reference

Welcome to the AVCI-CMS Public API documentation.

> [!IMPORTANT]
> For a full list of all documented modules, see the [Table of Contents](./TABLE_OF_CONTENTS.md).

This guide is intended for developers building storefronts, mobile applications, or secondary services that integrate with an AVCI-CMS workspace.

## Core Concepts

### Multi-tenancy
AVCI-CMS is a multi-tenant platform. Every request to the public API must identify the workspace (tenant) it is interacting with. This is done via a mandatory HTTP header:

`x-avci-workspace: {WORKSPACE_ID_OR_SLUG}`

### Base URL
The base URL for all v1 API endpoints is:
`https://api.yourdomain.com/v1`

---

## API Groups

### [Authentication & User](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/auth/user_api.md)
User login, registration (signup), OTP verification, password reset, and [Profile Management](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/user/profile_api.md).

### [Catalog & Products](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/catalog/product_api.md)
Search and retrieve Products, Events, Projects, Campaigns, and validate Coupons.

### [Content & Blog](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/content/blog_api.md)
Access Blog posts, Pages, News, and the [Dictionary/Glossary](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/content/word_api.md).

### [Common Services](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/common/category_api.md)
Shared modules like Categories, Attributes, Collections, and Groups.

### [E-commerce Services](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/services/basket_api.md)
Shopping Basket, Order creation, and Checkout flows.

### [Transactions & Finance](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/services/payment_api.md)
[Payments](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/services/payment_api.md), [Purchases](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/services/purchase_api.md), and [Invoices](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/services/invoice_api.md).

### [Communication](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/communication/newsletter_api.md)
Newsletters, Contact Forms, [FAQ](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/communication/faq_api.md), [Tickets](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/communication/ticket_api.md), and [Dynamic Forms](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/communication/form_api.md).

### [Technical & SEO](file:///Users/mertcanavci/Sites/AVCI/AVCI-CMS/guides/API/technical/seo_technical_api.md)
Sitemaps, RSS feeds, and technical metadata.
