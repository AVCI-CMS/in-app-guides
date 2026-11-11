# Proje API: Liste Kılavuzu

Proje API, mimari, tasarım veya iş projelerini sergilemek için kullanılır. Proje detayları, ekip üyeleri ve müşteri bilgilerini gösteren zengin bir yapı sunar.

---

## 📡 Liste Endpointler

### 1. Projeleri Listele (Sayfalamalı)
`GET /v1/project`

**Sorgu Parametreleri:**
- `page`: Sayfa numarası
- `limit`: Sayfa başı öğe
- `category`: Kategori slug'ı
- `year`: Proje yılına göre filtrele
- `search`: Başlık veya özet üzerinden arama

---

## 🚦 Proje Durumları

| Durum | Açıklama |
| :--- | :--- |
| `ACTIVE` | Proje yayında ve herkese açık. |
| `ARCHIVED` | Tamamlanmış ve referans olarak tutulan geçmiş proje. |
