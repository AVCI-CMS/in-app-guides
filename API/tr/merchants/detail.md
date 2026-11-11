# Satıcı (Merchant) API: Detay Kılavuzu

Bir satıcının tam ticari profiline, banka bilgilerine ve operasyonel ayarlarına erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Satıcı Detaylarını Getir
`GET /v1/merchant/:slug`

Satıcının kurumsal verilerini, vergi bilgilerini ve iletişim adreslerini döndürür.

**Örnek Yanıt:**
```json
{
  "name": "Zanaat Kolektifi",
  "corporateName": "Zanaat Ürünleri LTD",
  "slug": "zanaat-kolektifi",
  "taxNumber": 123456789,
  "taxOffice": "Kadıköy VD",
  "address": { "city": "İstanbul", "street": "..." },
  "badges": [ { "title": "En İyi Satıcı" } ]
}
```

---

### 🃏 Kart Görünümü
- `GET /v1/merchant/card/:slug`: UI kartları ve liste ögeleri için optimize edilmiş, kısa profil verilerini döndürür.

---

## 💬 Etkileşimler
- `/v1/merchant/follow/:slug`: Satıcıyı takibe al.
- `/v1/merchant/like/:slug`: Satıcı profilini beğen.
- `/v1/merchant/view/:slug`: Profil görüntülenme sayısını artır.
- `/v1/merchant/question/:slug`: Satıcıya doğrudan soru sor.
