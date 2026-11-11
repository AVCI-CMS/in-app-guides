# Invoice API Guide

The Invoice API allows users to retrieve and manage their sales and subscription invoices.

## Base URL
`GET /v1/invoice`

---

## Endpoints

### List User Invoices
`GET /v1/invoice/user/invoices`

Retrieves all invoices for the authenticated user.

---

### Get Invoice Details
`GET /v1/invoice/:invoiceId`

Retrieves full details and the PDF download URL for a specific invoice.

**Response Data:**
```json
{
  "invoiceNumber": "INV-2024-001",
  "status": "PAID | ISSUED",
  "total": 120.50,
  "currency": "USD",
  "pdfUrl": "URL",
  "items": [
    { "name": "string", "quantity": 1, "totalPrice": 120.50 }
  ]
}
```
