# Sepet (Basket) API: Kullanım Kılavuzu

Sepet API, kullanıcıların hem ürün hem de etkinlik biletlerini içeren alışveriş sepetlerini yönetmesini sağlar. Ürün adetlerini, fiyat hesaplamalarını ve sepet kilitleme (rezervasyon) süreçlerini takip eder.

---

## 📡 Temel Endpointler

### 1. Sepetimi Getir
`GET /v1/basket`

Giriş yapmış kullanıcının aktif sepetini, içindeki ürünleri ve toplam tutarı döndürür.

### 2. Sepete Öğe Ekle
`POST /v1/basket/add/:basketId`

Belirtilen sepete yeni ürün veya etkinlik bileti ekler.
**İstek Gövdesi:**
```json
{
  "items": [
    { "id": "urun_uuid", "quantity": 2, "itemType": "product" }
  ]
}
```

### 3. Adet Güncelle / Para Birimi / Temizle
- `PUT /v1/basket/update/:basketId/:itemId/increase`: Sayıyı artırır.
- `PUT /v1/basket/update/:basketId/:itemId/decrease`: Sayıyı azaltır.
- `PUT /v1/basket/currency/:basketId`: Sepetin aktif para birimini günceller.
- `DELETE /v1/basket/clear/:basketId`: Sepeti tamamen boşaltır.

---

## 🎟️ Bilet ve Rezervasyon (Önemli)
- **Kapasite Kilidi:** Etkinlik veya biletli ürünler sepete eklendiğinde, platform kapasiteyi geçici olarak (Örn: 10 dk) rezerve eder.
- **Katılımcı Bilgisi:** Sepette `event` veya `route` (rota) öğeleri varsa, ödeme aşamasında katılımcı bilgilerinin toplanması zorunludur.

---

## 🔗 Dokümantasyon
Detaylı teknik kılavuz için [AVCI CMS Sepet Dokümantasyonu](https://doc.avcicms.com/api/finance/basket) sayfasını ziyaret edin.

