# Arama (Search) API: Global Erişim Kılavuzu

Arama API, tüm modülleri (Ürün, Blog, Marka vb.) kapsayan merkezi bir keşif köprüsü sağlar. Regex tabanlı esnek arama ve hızlı öneri sistemlerini destekler.

---

## 📡 Liste ve Arama Endpointleri

### 1. Evrensel Arama
`GET /v1/search`

Belirtilen anahtar kelimeyi tüm platform içeriğinde arar. Case-insensitive (Büyük/Küçük harf duyarsız) regex eşleşmesi kullanır.

**Sorgu Parametreleri:**
- `query`: Aranacak terim (Zorunlu).

**Örnek Yanıt:**
```json
{
  "label": "Geleneksel Çömlekçilik Atölyesi",
  "type": "artist",
  "slug": "geleneksel-comlekcilik-atolyesi",
  "description": "...",
  "tumbnail": "resim-url"
}
```

---

### 2. Hızlı Arama (Autocomplete)
`GET /v1/search/short`

Kullanıcı yazarken anlık öneriler sunmak için optimize edilmiş, hafif arama endpointidir.

---

## 🚦 Sonuç Türleri (Types)

| Tür | Kaynak Modül | Açıklama |
| :--- | :--- | :--- |
| `artist` | `Brand` | Sanatçı, zanaatkar veya marka profilleri. |
| `artwork` | `Product` | Ürünler, eserler veya eşyalar. |
| `editorial` | `Blog` | Makaleler ve blog yazıları. |
| `news` | `News` | Haberler ve duyurular. |
