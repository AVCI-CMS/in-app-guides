# Custom Forms API Guide

The Custom Forms API enables the retrieval and submission of dynamic, user-defined forms. These forms are used for a variety of purposes, including merchant applications, job applications, surveys, and feedback.

## Base URL
`GET /v1/form`

---

## Form Purposes

| Purpose | Description |
| :--- | :--- |
| `MERCHANT_APPLICATION` | Onboarding for new vendors/merchants. |
| `JOB_APPLICATION` | Recruitment and HR applications. |
| `FEEDBACK` | Customer satisfaction and feature requests. |
| `SURVEY` | Data collection and market research. |
| `REGISTRATION` | Event or service sign-ups. |
| `CUSTOM` | General purpose dynamic forms. |

---

## Field Types & Validation

Forms support rich input types with integrated validation:
- **Basic**: `text`, `textarea`, `number`, `email`, `date`.
- **Selection**: `select`, `checkbox`, `radio`.
- **Complex**: 
    - `phone`: Structured phone input with country codes.
    - `file`: Document/Image uploads (supports `maxSize` and `accept` filters).
    - `nested`: Repeating groups of fields (e.g., "Add another experience").
    - `predefined`: Standardized `address` or `phone` blocks.

---

## Endpoints

### Get Form Structure
`GET /v1/form/:formId`

Retrieves the UI schema and validation rules for a specific form.

**Response Data (`data`):**
```json
{
  "title": "Vendor Application",
  "description": "Apply to become a merchant on our platform.",
  "fields": [
    {
      "name": "business_name",
      "label": "Business Name",
      "type": "text",
      "required": true
    },
    {
      "name": "logo",
      "label": "Company Logo",
      "type": "file",
      "validation": { "maxSize": 5242880, "accept": "image/*" }
    }
  ],
  "submitButtonText": "Submit Application",
  "purpose": "MERCHANT_APPLICATION"
}
```

---

### Submit Form Data
`POST /v1/form/submit/:formId`

Submits the user's responses for processing.

**Request Body:**
The body should contain the values mapped to the field `name` identifiers.
```json
{
  "business_name": "Artisan Goods Co.",
  "tax_id": "123456789",
  "contact_person": { "first": "John", "last": "Doe" }
}
```

---

### Check User Submission
`GET /v1/form/has-submission/:formId`

Checks if the current authenticated user has already submitted this form. Useful for preventing duplicate applications or showing "Thank you" states.
