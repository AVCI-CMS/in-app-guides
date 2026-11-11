# Kampanya API: Liste Kılavuzu

Kampanya API, çalışma alanındaki promosyon faaliyetlerini, indirimleri ve pazarlama kampanyalarını yönetir. Belirli ürünlere, kategorilere veya müşteri segmentlerine hedeflenebilir.

---

## 📡 Liste Endpointler

### 1. Kampanyaları Listele
`GET /v1/campaign`

Tüm halka açık kampanyaları sayfalamalı olarak döndürür.

**Sorgu Parametreleri:**
- `page`: Sayfa numarası
- `limit`: Öğe sayısı
- `status`: `ACTIVE`, `INACTIVE` veya `EXPIRED` (Süresi dolmuş) filtresi.
- `isActive`: Sadece aktif olanları listele (`true`/`false`).

---

### 🔥 Aktif Kampanyalar
- `GET /v1/campaign/active`: Şu an yürürlükte olan tüm kampanyaları getiren kısa yoldur.

---

## 🚦 Kampanya Durumları

| Durum | Açıklama |
| :--- | :--- |
| `ACTIVE` | Kampanya şu an yürürlükte ve kullanılabilir. |
| `INACTIVE` | Kampanya manuel olarak devre dışı bırakılmış. |
| `EXPIRED` | Kampanyanın bitiş tarihi (endDate) geçmiş. |
