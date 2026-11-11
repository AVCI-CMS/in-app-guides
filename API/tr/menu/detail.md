# Menü API: Detay ve Hiyerarşi

Belirli bir menünün içindeki tüm linklerin (öğelerin) hiyerarşik yapısına ve alt menülerine erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Menü Detaylarını Getir
`GET /v1/menu/:slug`

Menünün içindeki tüm öğeleri (`items`) ve onların alt dökümlerini (`children`) döndürür.

**Örnek Menü Öğesi:**
```json
{
  "title": "Mağaza",
  "url": "/catalog",
  "icon": "icon_name",
  "order": 1,
  "children": [
    {
      "title": "Aksesuarlar",
      "url": "/catalog/accessories",
      "order": 1
    }
  ]
}
```

---

## 🔗 Tüm Öğeleri Listele
- `GET /v1/menu/items`: Tüm menülerdeki öğeleri düz bir liste (flat) olarak döndürür. Sitemap oluştururken veya global aramalarda kullanılabilir.
