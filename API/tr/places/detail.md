# Mekan (Place) API: Detay Kılavuzu

Bir mekanın tam profiline, galeri görsellerine, kapasite detaylarına ve haftalık programına erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Mekan Detaylarını Getir
`GET /v1/place/:slug`

Mekanın tüm operasyonel verilerini ve medya ögelerini döndürür.

**Örnek Yanıt:**
```json
{
  "name": "Büyük Atölye",
  "slug": "buyuk-atolye",
  "capacity": { "min": 20, "max": 150 },
  "working": [
    { "day": 1, "hours": { "start": "09:00", "end": "18:00" } }
  ],
  "address": { "city": "İstanbul", "district": "Beşiktaş" },
  "gallery": [ { "url": "..." } ]
}
```

---

### 🃏 Kısa Bilgi (Short)
- `GET /v1/place/short/:slug`: Mobil kartlar ve liste gösterimleri için optimize edilmiş, özet profil verilerini döndürür.

---

## 💬 Etkileşimler
- `/v1/place/category`: Mekan kategorileri (bölge bazlı).
- `/v1/place/like/:slug`: Mekanı favorilere ekle.
- `/v1/place/view/:slug`: Görüntülenme sayısını artır.
- `/v1/place/question/:slug`: Mekana özel Soru-Cevap.
- `/v1/place/share/:slug`: Mekan paylaşım takibi.
