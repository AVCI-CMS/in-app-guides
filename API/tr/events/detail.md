# Etkinlik API: Detay Kılavuzu

Tek bir etkinliğin tarih, kapasite, konum ve satıcı bilgilerine erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Etkinlik Detaylarını Getir
`GET /v1/event/:slug`

Etkinliğin tüm içeriğini, kurallarını ve biletleme verilerini döndürür.

**Örnek Yanıt Yapısı:**
```json
{
  "id": "event_uuid",
  "name": "İleri Seviye Cam Üfleme Atölyesi",
  "slug": "ileri-seviye-cam-ufleme",
  "date": {
    "start": "2024-07-15T10:00:00Z",
    "end": "2024-07-15T17:00:00Z"
  },
  "price": {
    "amount": 1500.00,
    "sale": 1200.00,
    "discount": { "percentage": 20 }
  },
  "capacity": { "min": 5, "max": 15 },
  "place": { "name": "Zanaat Stüdyosu A", "address": "..." },
  "rules": ["18 yaş sınırı", "Malzemeler dahildir"]
}
```

---

## 🌍 Etkinlik Türleri
- `PHYSICAL`: Fiziksel bir konumda gerçekleşen etkinlik.
- `VIRTUAL`: Online (Zoom, YouTube vb.) üzerinden gerçekleşen etkinlik.
- `HYBRID`: Hem fiziksel hem online katılımın olduğu etkinlik.

---

## 💬 Etkileşimler
- `/v1/event/like/:slug`: Etkinliği favorilere ekle.
- `/v1/event/comment/:slug`: Kullanıcı değerlendirmeleri.
- `/v1/event/question/:slug`: Organizatöre soru sor.
