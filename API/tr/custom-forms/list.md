# Özel Form (Custom Form) API: Hızlı Referans

> 💡 **Detaylı şemalar, SDK kod örnekleri ve hata kodları için:**  
> Kapsamlı dokümantasyona [AVCI CMS Geliştirici Portalı](https://doc.avcicms.com/docs/api/communication/custom-form) üzerinden ulaşabilirsiniz.

Özel Form API; dinamik form şablonlarını, satıcı/marka onboarding başvurularını, anketleri ve başvuru onay süreçlerini yönetir.

---

## 📡 Temel Endpointler

### 1. Formları Listele (Yönetim)
* `GET /api/v1/customForm`
* **Query Parametreleri:** `page` (varsayılan: 1), `limit` (varsayılan: 10)
* **Header:** `x-avci-client: <client-id>`, `Authorization: Bearer <token>`
* Sistemdeki aktif form tanımlarını, alan sayılarını ve başvuru amaçlarını sayfalamalı döner.

### 2. Yeni Form Oluştur
* `POST /api/v1/customForm`
* Alanlar, doğrulama kuralları ve onay aksiyonları ile yeni bir dinamik form tanımlar.

---

## 🚦 Form Amaçları (Purposes)

| Amaç | Tanım ve Onay Aksiyonu |
| :--- | :--- |
| `STANDARD` | Genel veri toplama, iletişim ve özel talepler. |
| `MERCHANT_APPLICATION` | Pazar yeri satıcı başvurusu. Onaylandığında otomatik `Merchant` oluşturur. |
| `BRAND_APPLICATION` | Marka tescil başvurusu. Onaylandığında `Brand` oluşturur. |
| `ORGANIZATION_APPLICATION` | Çatı kurum / kooperatif başvurusu. Onaylandığında `Organization` oluşturur. |
| `SURVEY` | İstatistik ve dönüşüm oranları takip edilen müşteri anketleri. |

---

## ⚡ Hızlı İpucu
Storefront vitrininde form alanlarını render etmek için `GET /api/v1/customForm/:formId` uç noktasını `x-avci-client` başlığıyla çağırabilirsiniz.

> 📖 **Detaylı Dokümantasyon:** [Özel Form Geliştirici Rehberi](https://doc.avcicms.com/docs/api/communication/custom-form)
