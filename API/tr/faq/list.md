# Sıkça Sorulan Sorular (FAQ) API: Kullanım Kılavuzu

FAQ API, platformun destek kütüphanesine (Knowledge Base) erişim sağlar. Sorular mantıksal gruplara ve hiyerarşik kategorilere ayrılabilir.

---

## 📡 Liste ve Grup Endpointleri

### 1. Tüm S.S.S. Listele
`GET /v1/faq`

Tüm aktif soru ve cevapları düz (flat) bir liste olarak döndürür.

---

### 2. Gruba Göre Soruları Getir
`GET /v1/faq/:slug`

Belirli bir konu grubuna (Örn: "Ödeme", "Teslimat") ait tüm detayları ve altındaki soruları döndürür.

**Örnek Yanıt:**
```json
{
  "title": "Kargo ve Teslimat",
  "questions": [
    {
      "question": "Siparişim ne zaman ulaşır?",
      "answer": "Siparişiniz 3 iş günü içinde kargoya verilir..."
    }
  ]
}
```

---

## 💡 İpucu
Cevaplar (`answer`) zengin metin (Rich Text) içerebilir; bu nedenle frontend tarafında döküman yapısını koruyarak (HTML/Markdown) render edilmesi önerilir.
