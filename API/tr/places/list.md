# Mekan (Place) API: Liste Kılavuzu

Mekan API, fiziksel tesisleri, etkinlik noktalarını ve coğrafi ilgi alanlarını yönetir. Kapasite, çalışma saatleri ve hassas konum verileri gibi lojistik bilgiler sağlar.

---

## 📡 Liste Endpointler

### 1. Mekanları Listele
`GET /v1/place`

Tüm aktif mekanları sayfalamalı olarak döndürür.

**Sorgu Parametreleri:**
- `page`: Sayfa numarası
- `limit`: Öğe sayısı
- `area`: Bölge/Mahalle slug'ına göre filtrele
- `search`: İsim veya açıklama ile arama

---

## 🚦 Mekan Durumları
- `ACTIVE`: Herkese açık ve rezerve edilebilir konum.
- `DRAFT`: Kurulum aşamasındaki mekan.

---

## 🏗️ Veri Yapısı Özet
| Alan | Tip | Açıklama |
| :--- | :--- | :--- |
| `name` | `string` | Mekan adı. |
| `capacity` | `object` | Ziyaretçi limitleri (`min`, `max`). |
| `working` | `array` | Günlük çalışma saatleri (Pazartesi-Pazar). |
| `address` | `object` | Detaylı fiziksel adres ve ilçe bilgisi. |
