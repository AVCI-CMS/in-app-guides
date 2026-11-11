# İletişim Formu (Contact) API: Kullanım Kılavuzu

İletişim Formu API, ziyaretçilerin veya müşterilerin genel sorularını, destek taleplerini veya iş birliği mesajlarını platform yöneticilerine iletmelerini sağlar.

---

## 📡 Gönderim Endpointi

### 1. Mesaj Gönder
`POST /v1/contact-form`

Sisteme yeni bir iletişim mesajı kaydeder.

**İstek Gövdesi:**
```json
{
  "name": { "first": "Ayşe", "last": "Yılmaz" },
  "email": "ayşe@ornek.com",
  "tel": 5551234567,
  "subject": "İş Birliği Hakkında",
  "message": "Sizinle potansiyel bir iş birliği konusunu görüşmek istiyorum..."
}
```

---

## 🚦 Mesaj Durumları (Dahili)
Gelen mesajlar panel üzerinde şu aşamalardan geçer:
- `UNREAD`: Yeni gelen, henüz açılmamış mesaj.
- `READEN`: Yönetici tarafından okunmuş mesaj.
- `REPLYED`: Kullanıcıya cevap verilmiş veya işlenmiş mesaj.
