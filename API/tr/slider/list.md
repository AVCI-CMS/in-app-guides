# Slider API: Liste Kılavuzu

Slider API; web sitesi ve mobil uygulamalardaki kayan görsel (carousel) yapılarını yönetir. "Hero" alanları, duyuru bantları ve kampanya vitrinleri için kullanılır.

---

## 📡 Liste Endpointler

### 1. Sliderları Listele
`GET /v1/slider`

Aktif olan tüm slider'ların özet listesini (isim, slug, tip) döndürür.

**Gerekli Header:**
- `x-avci-workspace`: Tenant workspace ID (zorunlu).

**Örnek Yanıt:**
```json
{
  "data": [
    {
      "title": "Ana Sayfa Hero",
      "slug": "ana-sayfa-hero",
      "type": "hero"
    }
  ]
}
```

---

## 🚦 Slider Durumları
Sadece `PUBLISHED` durumundaki slider ve slide içerikleri public API üzerinden döner.
