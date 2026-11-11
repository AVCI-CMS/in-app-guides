# Haber API: Detay Kılavuzu

Tek bir haberin içeriğine veya harici kaynak bilgilerine erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Haber Detaylarını Getir
`GET /v1/news/:slug`

Dahili haberler için tam içerik, harici haberler için ise kaynak meta verilerini getirir.

**Örnek Yanıt (INTERNAL):**
```json
{
  "id": "news_uuid",
  "title": "AVCI-CMS v2.0 Yayınlandı",
  "slug": "avcicms-v2-yayinlandi",
  "newsType": "INTERNAL",
  "content": "Tam metin...",
  "featuredImage": "resim-url",
  "metadata": { ... }
}
```

**Harici Haber Nesnesi (EXTERNAL):**
```json
{
  "url": "https://harici-kaynak.com/haber",
  "source": "Teknoloji Portalı",
  "title": "Haber Başlığı",
  "description": "Kısa özet..."
}
```

---

## 💬 Etkileşimler
- `/v1/news/category`: Haber kategorileri.
- `/v1/news/like/:slug`: Haberi beğen.
- `/v1/news/share/:slug`: Paylaşım sayılarını takip et.
