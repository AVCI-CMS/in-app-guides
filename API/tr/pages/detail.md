# Sayfa API: Detay Kılavuzu

Belirli bir sayfanın tam içeriğine, form bağlantılarına ve SEO verilerine erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Sayfa Detaylarını Getir
`GET /v1/page/:slug`

Sayfanın içeriğini, ilişkili formları ve meta verilerini getirir.

**Örnek Yanıt:**
```json
{
  "id": "page_uuid",
  "title": "Bize Ulaşın",
  "slug": "iletisim",
  "content": "<h1>İletişime Geçin</h1>...",
  "form": "form_uuid",
  "agreement": "sozlesme_uuid",
  "metadata": { "seo": { ... } }
}
```

---

## 🔗 Entegrasyonlar
- **Form Bağlantısı:** Eğer `form` alanı varsa, sayfanın altında ilgili [Formun](./communication/form_api.md) gösterilmesi önerilir.
- **Sözleşme Bağlantısı:** Bir yasal metinle ilişkili ise `agreement` alanı üzerinden [Yasal Metin](./services/terms_api.md) detaylarına ulaşılabilir.

---

## 💬 Etkileşimler
- `/v1/page/like/:slug`: Sayfayı favorilere ekle.
- `/v1/page/share/:slug`: Paylaşım sayılarını takip et.
