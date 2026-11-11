# Applyment API Guide

The Applyment API allows external users, merchants, or organizations to submit applications for various statuses or memberships within the workspace.

## Base URL
`POST /v1/applyment`

---

## Supported Application Types

| Type | Target Entity | Model Name |
| :--- | :--- | :--- |
| `merchant` | Merchant Status | `MerchantApplyment` |
| `brand` | Brand Partnership | `BrandApplyment` |
| `organization` | Corporate Membership | `OrganizationApplyment` |
| `user` | Specialized User Roles | `UserApplyment` |

---

## Endpoints

### Submit Application
`POST /v1/applyment/:type`

Submits a new application for a specific type.

**Path Parameters:**
- `type`: One of `merchant`, `brand`, `organization`, or `user`.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `name` | `string` | Yes | Application or Applicant name |
| `corporateName` | `string` | No | Legal entity name if applicable |
| `owner` | `string` | Yes | User ID who owns the application |
| `contact` | `object` | Yes | Detailed contact information (email, phone, address) |

**Example Body:**
```json
{
  "name": "Artisan Application",
  "corporateName": "Blue Clay Studio LLC",
  "owner": "6911c78bab835e55263a9cb8",
  "contact": {
    "email": "apply@example.com",
    "mobileNumber": [
      { "countryCode": "90", "areaCode": "555", "phoneNumber": "1234567" }
    ]
  }
}
```

---

## Tracking Applications
Management of applications (viewing status, updating, or deleting) is a protected administrative action and is handled via the `/v1/applyment/:type/management` endpoints, which require the `Applyments:View` permission or higher.
