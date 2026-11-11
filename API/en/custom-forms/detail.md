# Custom Form API: Schema, Submission & Review

> 💡 **Need deep technical schemas, error codes, and SDK examples?**  
> Read the complete guide at the [AVCI CMS Developer Portal](https://doc.avcicms.com/docs/api/communication/custom-form).

Used to retrieve form field schemas for dynamic rendering, submit user answers, and execute application review and approval workflows.

---

## 📡 Essential Endpoints

### 1. Fetch Form Schema (Storefront)
* `GET /api/v1/customForm/:formId`
* **Header:** `x-avci-client: <client-id>`
* Returns title, purpose, and dynamic `fields` with validation rules and optional `mappedAttributeId`.

### 2. Submit Form (Storefront)
* `POST /api/v1/customForm/submit/:formId`
* **Header:** `x-avci-client: <client-id>`
* **Body:** Key-value map matching field `name` properties:
  ```json
  {
    "businessName": "Artisan Leather Goods Ltd.",
    "taxId": "1234567890"
  }
  ```

### 3. Review Workspace & Status Update (Management)
* **Get Submission Detail:** `GET /api/v1/customForm/:formId/submissions/:subId`
* **Update Status:** `PUT /api/v1/customForm/:formId/submissions/:subId/status`
* **Lifecycle States:** `PENDING` &rarr; `UNDER_REVIEW` &rarr; `APPROVED` / `REJECTED` / `CANCELLED`

### 4. Automated Approval Execution
* `POST /api/v1/customForm/submissions/:submissionId/process`
* **Action:** Automatically provisions target entity (`Merchant`, `Brand`, `Organization`), converts mapped attributes into normalized EAV structures, and assigns onboarding setup flags.

---

## ⚡ Smart Attribute Mapping
Fields with `mappedAttributeId` automatically populate the normalized `attributes` array (`{ attributeId, value, unit }`) of the newly created entity when the submission is approved.

> 📖 **Read Full Documentation:** [Custom Form Developer Guide](https://doc.avcicms.com/docs/api/communication/custom-form)
