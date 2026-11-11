# Blog API: Makale Detay Kılavuzu

Tek bir makalenin tam içeriğine, SEO verilerine ve etkileşimlerine erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Blog Detaylarını Getir
`GET /v1/blog/:slug`

Makalenin tam içeriğini (HTML/Markdown) ve tüm metadata bilgilerini getirir.

**Yanıt Şeması:**
```json
{
  "id": "blog-uuid",
  "title": "Makale Başlığı",
  "content": "İçerik Metni...",
  "featuredImage": "kapak-resmi-url",
  "gallery": ["resim-1", "resim-2"],
  "metadata": {
    "author": "Yazar Adı",
    "seo": { "title": "SEO Başlığı", "description": "SEO Açıklaması" }
  }
}
```

---

## 💬 Etkileşimler
Detay sayfası ile ilişkili işlemler:
- `/v1/blog/like/:slug`: Beğeni sayısını artırır.
- `/v1/blog/comment/:slug`: Yorumları yönetir.
- `/v1/blog/share/:slug`: Paylaşım sayılarını günceller.
