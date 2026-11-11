# Soru-Cevap (Question) API: Kullanım Kılavuzu

Soru-Cevap API, kullanıcıların satıcılara veya belirli ürünlere yönelik doğrudan soru sormasını ve cevap almasını sağlar.

---

## 📡 Liste ve Gönderim Endpointleri

### 1. Soruları Listele
`GET /v1/question/:type/:id`

Belirli bir öğe veya satıcı için cevaplanmış tüm soruları döndürür.
**Tipler:** `product`, `merchant`, `brand`.

---

### 2. Soru Sor
`POST /v1/question/:type/:id`

Müşterinin yeni bir soru sormasını sağlar.
**İstek Gövdesi:**
```json
{
  "message": "Bu ürünün başka renkleri gelecek mi?"
}
```

---

## 🚦 İşleyiş Mantığı
- Sorular direkt olarak satıcıya (Merchant/Brand) yönlendirilir.
- Sadece satıcı tarafından cevaplanan sorular public API'da ("answered" durumunda) listelenir.
