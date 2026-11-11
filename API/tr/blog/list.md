# Blog API: Liste Kılavuzu

CMS üzerinde kayıtlı olan blog yazılarını listelemek, filtrelemek ve arama yapmak için kullanılır.

---

## 📡 Liste Endpointler

### 1. Blog Yazılarını Listele
`GET /v1/blog`

Tüm yayınlanmış makaleleri sayfalamalı olarak döndürür.

**Sorgu Parametreleri:**
- `page`: Sayfa numarası (Varsayılan: `1`)
- `limit`: Sayfa başı öğe sayısı (Maks: `100`)
- `category`: Kategori slug'ına göre filtreleme
- `language`: Dil kodu (`en`, `tr`)
- `status`: Yayın durumu (Sadece public API'da `PUBLISHED`)

---

### 2. Yeni Yazıları Getir
`GET /v1/blog/new`

En son yayınlanan 5-10 makaleyi hızlı erişim için döner.

---

## 🚦 Önemli Statüler
Blog yazılarının durumları şunlardır:
- `PUBLISHED`: Yayında
- `DRAFT`: Taslak (Listede görünmez)
- `HIDDEN`: Yayında değil (Listede görünmez)
