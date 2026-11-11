# Ürün API: Detay Kılavuzu

Tek bir ürünün tüm teknik özelliklerine, satıcı bilgilerine ve medya ögelerine erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Ürün Detaylarını Getir
`GET /v1/product/:slug`

Ürünün fiyat, stok, varyant ve açıklama gibi tüm verilerini döndürür.

**Örnek Veri Yapısı:**
```json
{
  "id": "prod_uuid",
  "name": "El Yapımı Seramik Vazo",
  "sku": "SER-001",
  "price": {
    "amount": 850.00,
    "sale": 750.00,
    "discount": 10
  },
  "brand": { "name": "KilSanat", "slug": "kilsanat" },
  "stock": { "amount": 12, "min": 2 },
  "attributes": [
    { "label": "Renk", "value": "Mavi" },
    { "label": "Boy", "value": "20", "unit": "cm" }
  ],
  "images": ["url_1", "url_2"]
}
```

---

## 🔗 İlişkili Servisler
- `/v1/product/category`: Ürünle ilgili kategoriler.
- `/v1/product/attribute`: Aranabilir teknik özellikler.
- `/v1/product/comment/:slug`: Kullanıcı yorumları ve puanlar.
- `/v1/product/question/:slug`: Ürünle ilgili Soru-Cevap.
