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

### 1. Kargo Öncesi Doğrudan Sipariş İptali (Müşteri)
`POST /v1/order/:orderId/cancel`

Müşteri henüz kargoya verilmemiş (`WAITING`, `PREPARING`, `PENDING_PAYMENT`) siparişlerini doğrudan iptal edebilir. Ürün stokları otomatik geri yüklenir, kupon kullanımı geri alınır ve ödeme sağlayıcısından anında provizyon/ödeme iadesi gerçekleştirilir.

```json
{
  "reason": "Yanlış beden/ürün seçimi yaptım",
  "reasonCode": "BUYER_CANCELLED"
}
```

### 2. Pazar Yeri Satıcı Alt Sipariş İptali (Vendor)
`POST /v1/order/management/sub-order/:subOrderId/cancel`

Pazar yeri satıcıları temin edemedikleri kendi alt siparişlerini gerekçe belirterek iptal edebilir. Müşteriye ilgili pay oranında otomatik kısmi iade (`RefundAllocationService`) işletilir.

```json
{
  "reason": "Ürün stokta kalmadı",
  "autoRefund": true,
  "restoreStock": true,
  "isSellerFault": true
}
```

### 3. Kargo Sonrası İade Talepleri (RMA & Bilet)
Sipariş kargoya verildikten (`ON_SHIPMENT`, `DONE`) sonra doğrudan iptal kapatılır. Son kullanıcı iade talebini Destek Bilet modülü üzerinden iletir (`POST /v1/ticket` - `type: "RETURN"`, `relatedId: orderId`).

- **Satıcı Sipariş Detayı:** Pazar yeri satıcıları kendilerine ait alt siparişi `GET /v1/order/vendor/:subOrderId` ile sorgular.

---

## 🔗 Dokümantasyon
Detaylı teknik kılavuz için [AVCI CMS Sipariş Dokümantasyonu](https://doc.avcicms.com/api/finance/order) sayfasını ziyaret edin.

