# Form Management: Design, Fields & Review

> 💡 **Need full step-by-step guides and workflow tutorials?**  
> Read the complete user guide at the [AVCI CMS Documentation Portal](https://doc.avcicms.com/docs/guides/modules/communication/custom-forms).

Configure dynamic input fields, bind entity catalog attributes, and review incoming applicant submissions in the two-column review workspace.

---

## 🛠️ Field Configuration & Types

* **Standard Inputs:** Text, Number, Email, Date, Textarea, Phone.
* **Selection Controls:** Dropdown Select, Single Radio, Multi-select Checkbox.
* **File & Documents:** File upload fields with MIME-type and size validation (e.g. Tax Registration Certificate).
* **Nested Object Groups (`OBJECT`):** Group related fields into reusable composite structures (e.g., Authorized Representative info).

---

## ⚡ Smart Attribute Mapping (`mappedAttributeId`)

For application purposes (`MERCHANT_APPLICATION`, `BRAND_APPLICATION`, `ORGANIZATION_APPLICATION`), you can map form fields directly to target entity attributes:
1. Click **"Map to Attribute"** on any field.
2. Select the corresponding attribute from the dropdown.
3. Upon approval, submitted values are automatically injected into the entity's normalized EAV `attributes` array.

---

## 🚦 Two-Column Review Workspace

When reviewing applicant answers at `/custom-forms/:id/answers/:subId`:
* **Left Panel:** Displays submitted fields, structured subdocuments, and downloadable files.
* **Right Panel:** Manages lifecycle status transitions (`PENDING` &rarr; `UNDER_REVIEW` &rarr; `APPROVED` / `REJECTED`), team comments, and one-click entity provisioning.

> 📖 **Read Full Guide:** [Custom Forms & Application Workflows](https://doc.avcicms.com/docs/guides/modules/communication/custom-forms)
