# Payment API: Usage Guide

The Payment API handles all financial transactions, including credit cards (3D Secure), bank transfers, and cryptocurrency payments.

---

## 📡 Payment Methods

### 1. Credit Card (3D Secure)
`POST /v1/payment/3ds`

Initiates the 3DS process and returns HTML content for bank verification pages.

**Request Parameters:**
- `orderId`: Order UUID.
- `paymentCard`: Card details (No, Expiry, Cvc).
- `callbackUrl`: Destination after 3DS verification.

---

### 2. Bank Transfer / EFT
`POST /v1/payment/bank-transfer`

Returns bank account details and reference codes. Transactions must be marked as `COMPLETED` manually after verification.

---

### 3. Cryptocurrency Payment
`POST /v1/payment/crypto`

Initiates a transfer to a specific wallet address.

---

## 🚦 Transaction Statuses
- `PENDING`: Awaiting payment confirmation.
- `SUCCESS`: Payment received successfully.
- `FAILED`: Transaction rejected or error occurred.
