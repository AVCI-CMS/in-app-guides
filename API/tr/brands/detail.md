# Marka (Brand) API: Detay Kılavuzu

Bir markanın tüm kimlik bilgilerine, ekibine, iletişim verilerine ve uzmanlık alanlarına erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Marka Detaylarını Getir
`GET /v1/brand/slug/:slug`

Markanın tüm kurumsal kimliğini ve iletişim bilgilerini döndürür.

**Örnek Yanıt:**
```json
{
  "name": "Seramik Kolektifi",
  "slug": "seramik-kolektifi",
  "description": "El yapımı toprak ve seramik işleri.",
  "logo": { "url": "..." },
  "techniques": ["Çarkla Biçimlendirme", "Sırlama"],
  "owner": { "name": { "first": "Can", "last": "Yılmaz" } },
  "contact": { "email": "info@...", "tel": "..." },
  "address": { "city": "İstanbul", "district": "Kadıköy" },
  "team": [ { "name": "Ayşe", "role": "Usta Çömlekçi" } ]
}
```

---

## 💬 Etkileşimler
- `/v1/brand/category`: Marka kategorileri.
- `/v1/brand/like/:slug`: Markayı takibe al veya beğen.
- `/v1/brand/view/:slug`: Profil görüntülenme kaydı.
- `/v1/brand/question/:slug`: Markaya özel Soru-Cevap.
- `/v1/brand/share/:slug`: Paylaşım sayılarını takip et.
