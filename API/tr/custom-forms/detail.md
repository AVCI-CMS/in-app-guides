# Özel Form (Custom Form) API: Şema, Yanıt & Onay Süreci

> 💡 **Detaylı şemalar, SDK kod örnekleri ve hata kodları için:**  
> Kapsamlı dokümantasyona [AVCI CMS Geliştirici Portalı](https://doc.avcicms.com/docs/api/communication/custom-form) üzerinden ulaşabilirsiniz.

Storefront üzerinde dinamik form alanlarını render etmek, kullanıcı yanıtlarını sisteme kaydetmek ve panelden başvuru inceleme/onaylama süreçlerini yürütmek için kullanılır.

---

## 📡 Temel Endpointler

### 1. Form Şemasını Getir (Storefront)
* `GET /api/v1/customForm/:formId`
* **Header:** `x-avci-client: <client-id>`
* Başlık, amaç ve doğrulama kurallarıyla birlikte dinamik `fields` dizisini döner.

### 2. Formu Gönder (Storefront)
* `POST /api/v1/customForm/submit/:formId`
* **Header:** `x-avci-client: <client-id>`
* **Body:** Form şemasındaki alan adlarıyla eşleşen anahtar-değer nesnesi:
  ```json
  {
    "businessName": "Usta Dericilik Ltd. Şti.",
    "taxId": "1234567890"
  }
  ```

### 3. Başvuru İnceleme & Durum Güncelleme (Yönetim)
* **Başvuru Detayı:** `GET /api/v1/customForm/:formId/submissions/:subId`
* **Durum Güncelle:** `PUT /api/v1/customForm/:formId/submissions/:subId/status`
* **Yaşam Döngüsü Durumları:** `PENDING` &rarr; `UNDER_REVIEW` &rarr; `APPROVED` / `REJECTED` / `CANCELLED`

### 4. Onay İşlemini Yürüt (Approval Process)
* `POST /api/v1/customForm/submissions/:submissionId/process`
* **Aksiyon:** Başvuru türüne göre (`Merchant`, `Brand`, `Organization`) ilgili varlığı otomatik oluşturur, haritalanmış nitelikleri aktarır ve onboarding kurulum aşamasını başlatır.

---

## ⚡ Akıllı Nitelik Haritalama (Smart Mapping)
Formda `mappedAttributeId` ile bir varlık niteliğine bağlanmış alanlar, başvuru onaylandığında otomatik olarak yeni varlığın normalize `attributes` dizisine (`{ attributeId, value, unit }`) dönüştürülür.

> 📖 **Detaylı Dokümantasyon:** [Özel Form Geliştirici Rehberi](https://doc.avcicms.com/docs/api/communication/custom-form)
