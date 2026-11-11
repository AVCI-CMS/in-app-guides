# Etkinlik API: Liste Kılavuzu

Etkinlik API; biletli veya biletsiz atölye çalışmaları, sergiler ve sanal toplantılar gibi aktiviteleri yönetir. Karmaşık zamanlama ve kapasite yönetimini destekler.

---

## 📡 Liste Endpointler

### 1. Etkinlikleri Listele (Sayfalamalı)
`GET /v1/event`

**Sorgu Parametreleri:**
- `page`: Sayfa numarası (Varsayılan: `1`)
- `limit`: Sayfa başı öğe (Varsayılan: `10`)
- `status`: Durum filtresi (Örn: `PUBLISHED`)
- `category`: Kategori ID veya slug'ı
- `minPrice` / `maxPrice`: Fiyat aralığı

---

### 📅 Filtrelenmiş Listeler
- `GET /v1/event/new`: Yeni eklenen etkinlikler.
- `GET /v1/event/upcoming`: Yaklaşan etkinlikler.
- `GET /v1/event/passed`: Geçmiş etkinlik arşivi.

---

## 🚦 Etkinlik Durumları

| Durum | Açıklama |
| :--- | :--- |
| `PUBLISHED` | Etkinlik yayında ve bilet alınabilir. |
| `SOLD_OUT` | Kapasite dolmuş, bilet satışı kapalı. |
| `PASSED` | Etkinlik gerçekleşti ve sona erdi. |
| `PRE_REQUEST` | Satışın henüz başlamadığı, ön talep aşaması. |
