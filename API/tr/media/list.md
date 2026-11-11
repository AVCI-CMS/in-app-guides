# Medya (Media) API: Liste ve İşleme Kılavuzu

Medya API, görsel varlıkların (resimler, logolar, ikonlar) yüksek performanslı bir şekilde sunulmasını ve dinamik olarak işlenmesini sağlar.

---

## 📡 Liste ve Erişim Endpointleri

### 1. Görsel İşleme ve Dönüştürme
`GET /v1/:tenant/images/:type/:filename`

Görselleri belirtilen boyutlarda ve kalitede gerçek zamanlı olarak işler.

**Sorgu Parametreleri:**
- `w`: Genişlik (px)
- `h`: Yükseklik (px)
- `q`: Kalite (1-100, Varsayılan: `80`)
- `f`: Hedef format (`webp`, `jpeg`, `png`)
- `fit`: Boyutlandırma türü (`cover`, `contain` vb.)

**Örnek:**
`GET /my-workspace/images/product/item-01.jpg?w=800&f=webp`

---

## 🚀 Kurumsal Görseller
Oturum açmış çalışma alanı için otomatik çözümlenen endpointler:
- `GET /v1/logo`: Kurumun resmi logosu.
- `GET /v1/favicon`: Kurumun tarayıcı ikonı.

---

## 🚦 Teknik Detaylar
- **Global Erişim:** Tüm görseller `CORS: *` başlığı ile servis edilerek her türlü frontend ortamına uyum sağlar.
- **Optimizasyon:** Görseller bulut üzerinde otomatik olarak optimize edilir ve ön belleğe (Cache) alınır.
