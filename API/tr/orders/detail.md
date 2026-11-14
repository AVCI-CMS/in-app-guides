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

## 🧾 İptal, İade ve Satıcı Siparişleri
- **İptal & İade Talepleri (Ticket):** Son kullanıcı iptal ve iade talepleri Destek Bilet modülü üzerinden iletilir (`POST /v1/ticket` - `type: "CANCELLATION"` veya `"RETURN"`, `relatedId: orderId`).
- **Satıcı Sipariş Detayı:** Pazar yeri satıcıları kendilerine ait alt siparişi `GET /v1/order/vendor/:subOrderId` ile sorgular.

---

## 🔗 Dokümantasyon
Detaylı teknik kılavuz için [AVCI CMS Sipariş Dokümantasyonu](https://doc.avcicms.com/api/finance/order) sayfasını ziyaret edin.

