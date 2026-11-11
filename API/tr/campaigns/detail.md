# Kampanya API: Detay Kılavuzu

Tek bir kampanyanın kapsamına, indirim oranlarına ve uygulama koşullarına erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Kampanya Detaylarını Getir
`GET /v1/campaign/:id`

Kampanyanın hangi ürünlerde geçerli olduğunu ve katılım şartlarını döndürür.

**Örnek Yanıt:**
```json
{
  "id": "camp_uuid",
  "title": "Yaz İndirimi 2024",
  "startDate": "2024-06-01T00:00:00Z",
  "endDate": "2024-08-31T23:59:59Z",
  "discountPercentage": 20,
  "conditions": ["Minimum 500 TL alışveriş", "Sadece kayıtlı üyeler"],
  "appliesTo": {
    "products": ["prod_uuid_1"],
    "categories": ["cat_uuid_yaz"]
  }
}
```

---

## 📒 Hesaplama Mantığı
- **Yüzdesel İndirim:** `discountPercentage` alanı doluysa toplam tutar üzerinden yüzde düşülür.
- **Sabit İndirim:** `discountAmount` alanı doluysa tutardan sabit bir miktar düşülür.

---

## 🎯 Hedefleme (AppliesTo)
Kampanyalar şunlara hedeflenebilir:
- **Ürünler:** Sadece belirli ürün UUID'leri.
- **Kategoriler:** Belirli kategorilere ait tüm ürünler.
- **Segmentler:** Belirli müşteri grupları (Örn: "Yeni Üyeler").
