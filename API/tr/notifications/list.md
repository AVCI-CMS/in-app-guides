# Bildirim (Notification) API: Kullanım Kılavuzu

Bildirim API, kullanıcı uyarılarını ve sistem mesajlarını (E-posta, Push, In-App) yönetir. Cihazlar arası okundu/görüldü durumlarını senkronize eder.

---

## 📡 Liste ve Yönetim Endpointleri

### 1. Bildirimleri Listele
`GET /v1/notification/management/all`

Giriş yapmış kullanıcıya ait tüm bildirimleri (Sipariş, Takip, Yorum vb.) döndürür.

---

### 2. Okunmadı Sayıları
`GET /v1/notification/management/unread/menu-list`

Arayüzdeki "Çan" ikonu veya menüler için okunmamış bildirim sayılarını döndürür.

---

### 3. Durum Güncelleme
- `PUT /v1/notification/management/read/:id`: Belirli bir bildirimi **"Okundu"** olarak işaretler.
- `PUT /v1/notification/management/seen/`: Tüm yeni bildirmleri **"Görüldü"** (Yeni etiketi kalkar) olarak işaretler.
- `PUT /v1/notification/management/hide/:id`: Bildirimi listeden gizler.

---

## 🚦 Kategoriler
- **İşlemsel:** `ORDER` (Sipariş), `PAYMENT` (Ödeme), `SHIPMENT` (Kargo).
- **Etkileşim:** `COMMENT` (Yorum), `LIKE` (Beğeni), `FOLLOW` (Takip).
- **Sistem:** `PENALTY` (Ceza/Uyarı), `MEMBER` (Üyelik).
- **İletişim:** `MESSAGE`, `TICKET`, `NEWSLETTER`.
