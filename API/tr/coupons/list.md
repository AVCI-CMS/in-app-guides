# Kupon API: Liste Kılavuzu

Kupon API, indirim kodlarının geçerliliğini kontrol etmek ve belirli promosyon teklifleri hakkında bilgi almak için kullanılır.

---

## 📡 Liste Endpointler

### 1. Kupon Bilgisini Kontrol Et
`GET /v1/coupon/check/:code`

Bir kupon kodunun (Örn: `YAZ20`) varlığını ve genel şartlarını kontrol eder.

**Yol Parametreleri:**
- `code`: Alfanümerik kupon kodu.

**Örnek Yanıt:**
```json
{
  "code": "YAZ20",
  "discountType": "PERCENTAGE",
  "discountValue": 20,
  "minOrderAmount": 500,
  "usageTerms": ["Minimum 500 TL alışveriş", "Maksimum 100 TL indirim"]
}
```

---

## 🚦 Kupon Durumları
- `ACTIVE`: Geçerli ve kullanılabilir.
- `INACTIVE`: Manuel olarak devre dışı bırakılmış.
- `EXPIRED`: Geçerlilik tarihi dolmuş.
