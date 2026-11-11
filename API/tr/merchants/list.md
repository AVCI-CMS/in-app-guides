# Satıcı (Merchant) API: Liste Kılavuzu

Satıcı API, platformdaki ticari işletmelerin ve tedarikçilerin yasal ve ticari profillerini yönetir. Markalardan farklı olarak, "Satıcı" satış, vergilendirme ve lojistikten sorumlu tüzel kişiliktir.

---

## 📡 Liste Endpointler

### 1. Satıcıları Listele
`GET /v1/merchant`

Aktif olan tüm satıcıları sayfalamalı olarak döndürür.

**Sorgu Parametreleri:**
- `page`: Sayfa numarası
- `limit`: Öğe sayısı
- `search`: İsim veya açıklama ile arama

---

### 📍 Konum Servisleri
- `GET /v1/merchant/location`: Harita üzerinde gösterim için tüm aktif satıcıların koordinatlarını döner.

---

## 🚦 Satıcı Durumları
- `ACTIVE`: Onaylanmış ve satışa açık.
- `PENDING`: Başvuru inceleme aşamasında.
- `DRAFT`: Profil bilgileri eksik.
