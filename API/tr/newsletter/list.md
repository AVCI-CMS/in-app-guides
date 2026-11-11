# Haber Bülteni (Newsletter) API: Kullanım Kılavuzu

Haber Bülteni API, e-posta abonelik listelerini yönetir; kullanıcıların pazarlama duyurularına ve platform güncellemelerine abone olmasını veya abonelikten çıkmasını sağlar.

---

## 📡 Abonelik Endpointleri

### 1. Bültene Abone Ol
`POST /v1/newsletter/subscribe`

Yeni bir e-posta adresini abone listesine ekler.

**İstek Gövdesi:**
```json
{
  "email": "kullanici@ornek.com",
  "name": { "first": "Can", "last": "Yılmaz" }
}
```

**Yanıt:**
Abonelik isteği alındığında kullanıcıya bir doğrulama e-postası gönderilir. `isVerified` alanı kullanıcı onay verene kadar `false` kalır.

---

### 2. Abonelikten Çık
`POST /v1/newsletter/unsubscribe`

Belirtilen e-posta adresini aktif gönderim listesinden çıkarır.

---

## 🚦 Abonelik Durumları
- `ACTIVE`: Kullanıcı kayıtlı ve doğrulandı.
- `UNSUBSCRIBED`: Kullanıcı kendi isteğiyle ayrıldı.
- `BOUNCED`: E-posta gönderimi başarısız oldu (Hatalı adres).
