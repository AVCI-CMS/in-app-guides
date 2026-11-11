# Haber API: Liste Kılavuzu

Haber API; duyurular, basın bültenleri ve sektör güncellemelerine erişim sağlar. Hem platform içi içerikleri hem de harici haber kaynaklarını destekler.

---

## 📡 Liste Endpointler

### 1. Haberleri Listele
`GET /v1/news`

Haberleri sayfalamalı olarak döndürür.

**Sorgu Parametreleri:**
- `page`: Sayfa numarası
- `limit`: Sayfa başı öğe sayısı
- `category`: Kategori slug'ı
- `language`: Dil kodu (`en`, `tr`)
- `type`: `INTERNAL` (Dahili) veya `EXTERNAL` (Harici)

---

### 2. Son Haberleri Getir
`GET /v1/news/new`

En güncel 10 haber öğesini getirir.

---

## 🚦 Haber Türleri

| Tür | Açıklama |
| :--- | :--- |
| `INTERNAL` | Doğrudan AVCI-CMS üzerinde barındırılan içerikler. |
| `EXTERNAL` | Harici haber sitelerine yönlendiren özetler ve bağlantılar. |
