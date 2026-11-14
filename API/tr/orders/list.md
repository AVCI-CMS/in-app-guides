# Sipariş (Order) API: Liste Kılavuzu

Sipariş API, başarılı ödemelerin ardından oluşan satış kayıtlarını, bilet üretimini ve lojistik süreçlerini yönetir.

---

## 📡 Liste Endpointler

### 1. Siparişlerimi Listele
`GET /v1/order`

Giriş yapmış kullanıcının geçmiş ve aktif tüm siparişlerini döndürür.

**Sorgu Parametreleri:**
- `page`: Sayfa numarası.
- `status`: `PENDING`, `COMPLETED`, `SHIPPED`, `CANCELLED` gibi durum filtreleri.

---

### 🎟️ Biletlerim ve Rezervasyonlar
- `GET /v1/order/tickets`: Sadece satın alınan etkinlik biletlerini ve QR kodlarını dönebilir.
- `GET /v1/order/upcoming`: Gelecek etkinliklere ait sipariş özetleri.

---

### 🛍️ Satıcı Siparişleri (Pazaryeri)
- `GET /v1/order/vendor`: Giriş yapmış satıcı hesabının izole alt siparişlerini listeler.

---

## 🚦 Sipariş Durumları
| Durum | Açıklama |
| :--- | :--- |
| `PENDING` | Ödeme onayı bekleyen veya işleme alınan sipariş. |
| `COMPLETED` | Başarıyla tamamlanmış (Biletler üretilmiş). |
| `SHIPPED` | Fiziksel ürün kargoya verilmiş. |
| `CANCELLED` | İptal edilmiş veya iade edilmiş sipariş. |

---

## 🔗 Dokümantasyon
Detaylı teknik kılavuz için [AVCI CMS Sipariş Dokümantasyonu](https://doc.avcicms.com/api/finance/order) sayfasını ziyaret edin.

