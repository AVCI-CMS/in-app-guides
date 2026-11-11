# Destek Talebi (Ticket) API: Kullanım Kılavuzu

Destek Talebi API, müşteriler ve çalışma alanı personeli arasındaki resmi iletişimi sağlar. Kategorize edilmiş talepleri, öncelik seviyelerini ve mesaj dizilerini yönetir.

---

## 📡 Talepler ve Mesajlaşma

### 1. Yeni Talep Oluştur
`POST /v1/ticket`

Müşterinin belirli bir konu (Sipariş, İade, Teknik vb.) hakkında destek talebi açmasını sağlar.
**İstek Gövdesi:**
```json
{
  "category": "ORDER",
  "priority": "HIGH",
  "message": "Siparişim henüz elime ulaşmadı."
}
```

---

### 2. Mesaj Gönder ve Listele
- `POST /v1/ticket/message`: Mevcut bir talebe yeni mesaj ekler (Ek dosya desteği mevcuttur).
- `GET /v1/ticket/message/ticket/:id`: Bir talebe ait tüm mesajlaşma geçmişini döndürür.

---

## 🚦 Talep Durumları
| Durum | Açıklama |
| :--- | :--- |
| `NEW` | Yeni oluşturulmuş, inceleme bekliyor. |
| `IN_PROGRESS` | Personel talep üzerinde çalışıyor. |
| `WAITING_CUSTOMER` | Müşteriden yanıt veya ek bilgi bekleniyor. |
| `RESOLVED` | Sorun çözüldü. |
| `CLOSED` | Talep kapatıldı (Yeni mesaj yazılamaz). |
