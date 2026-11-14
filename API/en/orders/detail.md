# Order API: Detail and Logistics

Used to access specific order contents, tracking information, and generated ticket/file links.

---

## 📄 Detail Endpoints

### 1. Get Order Details
`GET /v1/order/:id`

Returns items, payment summary, and shipping address.

**Sample Response:**
```json
{
  "id": "order_uuid",
  "orderNo": "AVCI-12345",
  "items": [ ... ],
  "shipping": { "trackingNo": "TR123...", "company": "Courier Co" },
  "price": { "total": 1250.00, "currency": "TRY" }
}
```

---

## 🎟️ Participant and Ticket Details
If the order contains an event:
- **Participants:** Name, ID, or Email for each individual ticket holder.
- **Tickets:** PDF or QR code access links.

---

## 🧾 Cancellations, Returns and Vendor Orders
- **Cancellation & Return Tickets:** Storefront users initiate cancellations or return requests through the Support Ticket module (`POST /v1/ticket` with `type: "CANCELLATION"` or `"RETURN"`, `relatedId: orderId`).
- **Vendor Sub-Orders:** Marketplace sellers fetch isolated sub-orders via `GET /v1/order/vendor/:subOrderId`.

---

## 🔗 Documentation Link
For detailed guides and SDK usage, visit [AVCI CMS Order Documentation](https://doc.avcicms.com/api/finance/order).

