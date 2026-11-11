# Sepet (Basket) API: Kullanım Kılavuzu

Sepet API, kullanıcıların hem ürün hem de etkinlik biletlerini içeren alışveriş sepetlerini yönetmesini sağlar. Ürün adetlerini, fiyat hesaplamalarını ve sepet kilitleme (rezervasyon) süreçlerini takip eder.

---

## 📡 Temel Endpointler

### 1. Sepetimi Getir
`GET /v1/basket`

Giriş yapmış kullanıcının aktif sepetini, içindeki ürünleri ve toplam tutarı döndürür.

### 2. Sepete Öğe Ekle
`POST /v1/basket/add`

Sepete yeni ürün veya etkinlik bileti ekler.
**İstek Gövdesi:**
```json
{
  "items": [
    { "id": "urun_uuid", "quantity": 2, "itemType": "product" }
  ]
}
```

### 3. Adet Güncelle / Sil
- `PUT /v1/basket/update/:itemId/increase`: Sayıyı artırır.
- `PUT /v1/basket/update/:itemId/decrease`: Sayıyı azaltır.
- `DELETE /v1/basket`: Sepeti tamamen boşaltır.

---

## 🎟️ Bilet ve Rezervasyon (Önemli)
- **Kapasite Kilidi:** Etkinlik veya biletli ürünler sepete eklendiğinde, platform kapasiteyi geçici olarak (Örn: 10 dk) rezerve edebilir.
- **Katılımcı Bilgisi:** Sepette `event` veya `route` (rota) öğeleri varsa, ödeme aşamasında katılımcı bilgilerinin toplanması zorunludur.
