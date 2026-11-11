# Slider API: Slide Detay ve Yapı

Belirli bir slider'ın içindeki tüm slide'lara (görsel, metin, link) erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Slug ile Slider Getir
`GET /v1/slider/:slug`

Slider'ı, içindeki tüm sıralanmış ve yayındaki slide'larla birlikte döndürür.

**Örnek Slide Yapısı:**
```json
{
  "title": "Yaz Kampanyası",
  "slideType": "basic",
  "order": 0,
  "image": { "url": "...", "width": 1920, "height": 600 },
  "mobileImage": { "url": "...", "width": 768, "height": 400 },
  "CTA": { "title": "Keşfet", "url": "/urunler" }
}
```

---

## 🖼️ Slide Tipleri
- `basic`: Başlık, alt başlık, görsel ve CTA butonu.
- `video`: Arka planda video URL desteği.
- `advanced`: Özel layout tasarımları için ek metadata alanları.

---

## 📱 Mobil Desteği
Eğer `mobileImage` tanımlanmışsa, mobil cihazlarda performans ve görünüm için bu görsel kullanılmalıdır. Tanımlanmamışsa ana `image` fallback olarak kullanılabilir.
