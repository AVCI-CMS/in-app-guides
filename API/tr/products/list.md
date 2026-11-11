# Ürün API: Liste Kılavuzu

Ürün API, AVCI-CMS kataloğunun merkezidir. Fiziksel dijital ve hizmet tabanlı ürünlere kapsamlı erişim sağlar.

---

## 📡 Liste Endpointler

### 1. Ürünleri Listele (Sayfalamalı)
`GET /v1/product`

**Sorgu Parametreleri:**
- `page`: Sayfa numarası (Örn: `1`)
- `limit`: Sayfa başı öğe (Örn: `20`)
- `category`: Kategori slug'ı veya ID'si
- `brand`: Marka slug'ı
- `merchant`: Satıcı slug'ı
- `minPrice` / `maxPrice`: Fiyat aralığı
- `search`: Anahtar kelime arama

---

### 🛍️ Özel Listeleme Grupları
- `GET /v1/product/new`: Yeni eklenen ürünler.
- `GET /v1/product/popular`: En çok etkileşim alan/satılan ürünler.
- `GET /v1/product/random/:amount`: Rastgele ürün seçkisi.

---

## 🚦 Ürün Durumları

| Durum | Açıklama |
| :--- | :--- |
| `PUBLISHED` | Ürün yayında ve satın alınabilir. |
| `OUT_OF_STOCK` | Stok tükenmiş. |
| `SOLD_OUT` | Ürün artık mevcut değil (tekil ürünler için). |
| `HIDDEN` | Ürün aramadan ve listelerden gizlenmiş. |
