# Kurum (Organization) API: Liste Kılavuzu

Kurum API, platformdaki tüzel kişilerin, kurumların ve çatı organizasyonların profillerini yönetir. Detaylı kurumsal meta veriler, ekip yapıları ve operasyonel veriler sağlar.

---

## 📡 Liste Endpointler

### 1. Kurumları Listele
`GET /v1/organization`

Tüm aktif kurumları sayfalamalı olarak döndürür.

**Sorgu Parametreleri:**
- `page`: Sayfa numarası
- `limit`: Öğe sayısı
- `search`: İsim veya açıklama ile arama

---

## 🚦 Kurum Durumları
- `ACTIVE`: Tam kayıtlı ve aktif kurumsal profil.
- `DRAFT`: Geliştirme aşamasındaki profil.

---

## 🏗️ Veri Yapısı Özet
| Alan | Tip | Açıklama |
| :--- | :--- | :--- |
| `name` | `string` | Kurumun ticari veya birincil adı. |
| `corporateName` | `string` | Yasal kayıtlı unvan. |
| `corporationType` | `string` | Şirket türü (Örn: Limited, Anonim). |
| `website` | `string` | Resmi web sitesi. |
