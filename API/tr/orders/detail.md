# Sipariş (Order) API: Detay ve Lojistik

Tek bir siparişin içeriğine, kargo takip bilgilerine ve üretilen bilet/dosya linklerine erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Sipariş Detaylarını Getir
`GET /v1/order/:id`

Sipariş edilen kalemleri, ödeme özetini ve teslimat adresini döndürür.

**Örnek Yanıt:**
```json
{
  "id": "order_uuid",
  "orderNo": "AVCI-12345",
  "items": [ ... ],
  "shipping": { "trackingNo": "TR123...", "company": "Yurt içi" },
  "price": { "total": 1250.00, "currency": "TRY" }
}
```

---

## 🎟️ Katılımcı ve Bilet Bilgileri
Eğer sipariş bir etkinlik içeriyorsa:
- **Participants:** Her bilet için tanımlanan katılımcı isimleri.
- **Tickets:** PDF bilet veya QR kod erişim bağlantıları.

---

## 🧾 İptal ve İade
- `POST /v1/order/cancel/:id`: Siparişi iptal etme talebi gönderir (Yasal süreler dahilinde).
