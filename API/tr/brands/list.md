# Marka (Brand) API: Liste Kılavuzu

Marka API, platformdaki yaratıcıların, zanaatkarların ve üreticilerin kimliklerini ve genel görünürlüklerini yönetir.

---

## 📡 Liste Endpointler

### 1. Markaları Listele
`GET /v1/brand`

Tüm aktif markaları sayfalamalı olarak döndürür.

**Sorgu Parametreleri:**
- `page`: Sayfa numarası
- `limit`: Öğe sayısı
- `category`: Kategori slug'ı
- `search`: İsim veya açıklama ile arama

---

## 🚦 Marka Durumları
- `ACTIVE`: Herkese açık marka profili.
- `PENDING`: İnceleme altındaki marka.
- `DRAFT`: Hazırlık aşamasındaki profil.

---

## 🏗️ Veri Yapısı Özet
| Alan | Tip | Açıklama |
| :--- | :--- | :--- |
| `name` | `string` | Marka adı. |
| `logo` | `object` | Marka logosu. |
| `owner` | `object` | Marka sahibi (Kullanıcı). |
| `techniques` | `array` | Markanın kullandığı uzmanlık teknikleri. |
