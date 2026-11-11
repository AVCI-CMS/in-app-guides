# Payment API Guide

The Payment API handles financial transactions, supporting various methods including credit cards (with 3D Secure), bank transfers, and crypto payments.

## Base URL
`POST /v1/payment`

---

## 3D Secure Credit Card Payment

### Create 3DS Payment
`POST /v1/payment/3ds`

**Request Body:**
| Field | Type | Description |
| :--- | :--- | :--- |
| `orderId` | `string` | The UUID of the order |
| `amount` | `number` | Total amount |
| `currency` | `string` | e.g., `USD`, `TRY` |
| `paymentCard` | `object` | Card details (number, expire, cvc, etc.) |
| `callbackUrl` | `string` | URL to return to after 3DS |

**Response Data:**
```json
{
  "htmlContent": "string",
  "paymentId": "string",
  "status": "pending"
}
```

---

## Bank Transfer

### Create Bank Transfer Payment
`POST /v1/payment/bank-transfer`

**Response Data:**
```json
{
  "paymentId": "string",
  "referenceCode": "string",
  "bankAccount": {
    "bankName": "string",
    "iban": "string",
    "accountHolder": "string"
  },
  "expiresAt": "ISO Date"
}
```

---

## Cryptocurrency Payment

### Create Crypto Payment
`POST /v1/payment/crypto`

**Request Body:**
- `cryptoCurrency`: `BTC`, `ETH`, `USDT`, etc.

**Response Data:**
```json
{
  "paymentId": "string",
  "walletAddress": "string",
  "amount": 0.0005,
  "expiresAt": "ISO Date"
}
```
