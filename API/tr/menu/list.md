# Menü API: Liste Kılavuzu

Menü API, web sitesi ve mobil uygulamalardaki hiyerarşik navigasyon yapılarını (Header, Footer, Sidebar vb.) yönetmek için kullanılır.

---

## 📡 Liste Endpointler

### 1. Menüleri Listele
`GET /v1/menu`

Çalışma alanındaki tüm kayıtlı menülerin (ana navigasyon, footer vb.) listesini döndürür.

**Örnek Yanıt:**
```json
{
  "menus": [
    {
      "name": "Ana Navigasyon",
      "slug": "main-nav",
      "location": "header",
      "isActive": true
    }
  ]
}
```

---

## 🚦 Yerleşim Alanları (Locations)
- `header`: Üst bilgi alanı.
- `footer`: Sayfa altı alanı.
- `sidebar`: Yan panel navigasyonu.
- `custom`: Özel yerleşim alanları.
