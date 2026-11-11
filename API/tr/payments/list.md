# Ödeme (Payment) API: Kullanım Kılavuzu

Ödeme API, kredi kartı (3D Secure), banka havalesi ve kripto para ödemeleri dahil olmak üzere tüm finansal işlemleri yönetir.

---

## 📡 Ödeme Metodları

### 1. Kredi Kartı (3D Secure)
`POST /v1/payment/3ds`

Güvenli ödeme (3DS) sürecini başlatır ve tarayıcıyı banka onay sayfasına yönlendirecek HTML içeriğini döner.

**Örnek İstek Parametreleri:**
- `orderId`: Sipariş UUID'si.
- `paymentCard`: Kart bilgileri (No, Skt, Cvc).
- `callbackUrl`: 3DS sonrası dönülecek adres.

---

### 2. Banka Havalesi / EFT
`POST /v1/payment/bank-transfer`

Ödeme için gerekli banka hesap detaylarını ve referans kodunu döner. İşlem, banka onayı sonrası manuel olarak `COMPLETED` olarak işaretlenmelidir.

---

### 3. Kripto Para Ödemesi
`POST /v1/payment/crypto`

Belirli bir cüzdan adresine yapılacak transfer işlemini başlatır.

---

## 🚦 İşlem Durumları
- `PENDING`: Ödeme onayı bekleniyor.
- `SUCCESS`: Ödeme başarıyla alındı.
- `FAILED`: Ödeme reddedildi veya hata oluştu.
