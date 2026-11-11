# Proje API: Detay Kılavuzu

Bir projenin tam profiline, ekip yapısına ve medya bağlantılarına erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Proje Detaylarını Getir
`GET /v1/project/:slug`

Projenin tüm içeriğini, ekip üyelerini ve sosyal medya bağlantılarını döndürür.

**Örnek Yanıt:**
```json
{
  "id": "proj_uuid",
  "title": "Nehir Kıyısı Şehir Parkı",
  "slug": "nehir-kiyisi-sehir-parki",
  "date": "2024-05-12T00:00:00Z",
  "category": [ { "name": "Kentsel Tasarım", "slug": "kentsel" } ],
  "team": [
    {
      "name": "Tasarım Ekibi",
      "members": [ { "name": "Ayşe Yılmaz", "role": "Baş Mimar" } ]
    }
  ],
  "socialMedia": [
    { "platform": "Instagram", "url": "..." }
  ],
  "images": ["url_1", "url_2"]
}
```

---

## 🔗 İlişkili Servisler
- `/v1/project/category`: Proje kategorileri.
- `/v1/project/attribute`: Teknik öznitelikler (Yıl, Konum vb.).
- `/v1/project/like/:slug`: Favorilere ekleme.
- `/v1/project/share/:slug`: Sosyal paylaşım kaydı.
