# Kupon API: Doğrulama ve Kullanım

Kupon kodlarının belirli bir sepet ve kullanıcı için geçerliliğini doğrulamak için kullanılır.

---

## 📄 Doğrulama Endpointi

### 1. Kuponu Doğrula
`POST /v1/coupon/validate`

Kupon kodunu sepet tutarı ve kullanıcı bazlı olarak valide eder.

**İstek Parametreleri:**
- `code`: Doğrulanacak kod.
- `cartTotal`: Mevcut sepet toplamı.
- `customerId`: Kullanıcı ID'si (kullanım limitlerini kontrol etmek için).

**Yanıt:**
```json
{
  "valid": true,
  "discount": 100.00,
  "message": "Kupon başarıyla uygulandı"
}
```

---

## 🎟️ İndirim Türleri
- `PERCENTAGE`: Yüzdesel indirim (Örn: %20).
- `FIXED`: Sabit tutar indirimi (Örn: 50 TL).
- `FREE_SHIPPING`: Kargo ücretini sıfırlar.

---

## ⚖️ Kullanım Kısıtlamaları
- **minOrderAmount:** Kuponun kullanılabilmesi için gereken minimum sepet tutarı.
- **availableUsageCount:** Bu kuponun dünya genelinde kaç kez daha kullanılabileceği.
- **appliesTo:** Kupon sadece belirli **Ürünler** veya **Kategoriler** için geçerli olabilir (Validasyon işlemi bunu otomatik kontrol eder).
