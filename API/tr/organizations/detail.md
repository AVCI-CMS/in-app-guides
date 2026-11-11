# Kurum (Organization) API: Detay Kılavuzu

Bir kurumun tüm kurumsal profiline, iletişim bilgilerine, banka verilerine ve ekip yapısına erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Kurum Detaylarını Getir
`GET /v1/organization/slug/:slug`

Kurumun tüm resmi kimliğini ve operasyonel bilgilerini döndürür.

**Örnek Yanıt:**
```json
{
  "name": "Zanaatkarlar Derneği",
  "slug": "zanaatkarlar-dernegi",
  "corporateName": "Ulusal Zanaat Grubu LTD",
  "description": "Yerel çömlekçiliği destekleyen kar amacı gütmeyen kuruluş...",
  "logo": { "url": "..." },
  "email": "iletisim@...",
  "website": "zanaat.org",
  "bank": {
    "bankName": "Örnek Banka",
    "iban": "TR..."
  },
  "team": [ { "name": "Mert", "role": "Direktör" } ]
}
```

---

## 💬 Etkileşimler
- `/v1/organization/category`: Kurum kategorileri.
- `/v1/organization/like/:slug`: Kurumu takibe al veya beğen.
- `/v1/organization/view/:slug`: Profil görüntülenme kaydı.
- `/v1/organization/question/:slug`: Kuruma özel Soru-Cevap.
- `/v1/organization/share/:slug`: Paylaşım sayılarını takip et.
