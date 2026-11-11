# NFC Tool API (Client Guide)

Tenant platformlarının (web, mobil uygulama vb.) NFC etiket verilerine erişmesi için **public** endpoint'ler. Bu API, fiziksel NFC etiketlerinin dijital varlıklarla (Ürün, Sayfa, Etkinlik vb.) eşleştirilmesini ve bu bilgilerin son kullanıcılara gösterilmesini sağlar.

> [!IMPORTANT]
> - Tüm istekler `x-avci-workspace: {ID}` header'ını içermelidir (tenant seçimi için zorunlu).
> - Public endpointler güvenlik nedeniyle donanım teknik verilerini (UID kapasite vb.) ve iç denetim (metadata) bilgilerini dönmez.

**Base URL (tenant için):** `/api/v1/tools/nfc`

---

## Veri Tipleri (Types)

### 1. NFC Tag (Public)
Public API üzerinden dönen filtrelenmiş etiket verisi.

```typescript
interface INfcTagPublic {
  tagId: string;       // Etiketin donanım UID'si veya özel ID'si
  title?: string;      // Etiket başlığı
  description?: string; // Etiket açıklaması
  association: {
    targetType: 'PRODUCT' | 'PAGE' | 'EVENT' | 'ORGANIZATION' | 'CUSTOM_URL';
    targetId?: string;     // İlişkili varlığın ID'si (ObjectId)
    customUrl?: string;    // targetType CUSTOM_URL ise yönlendirilecek adres
  };
  customData: Record<string, any>; // Tenant tarafından tanımlanmış özel alanlar
}
```

---

## Endpoints

### 1. Etiket Bilgisi Getir

**`GET /api/v1/tools/nfc/:tagId`**

Belirtilen `tagId`'ye sahip etiketin public bilgilerini döner. Genellikle bir mobil uygulama veya web sayfası bir NFC etiketi okuduğunda, etiketin neye karşılık geldiğini anlamak için bu endpoint'i kullanır.

**Headers**

| Header             | Tip    | Açıklama                          |
|--------------------|--------|-----------------------------------|
| `x-avci-workspace` | string | Tenant workspace ID (zorunlu)    |

**Path Params**

| Parametre | Tip    | Açıklama               |
|-----------|--------|------------------------|
| `tagId`   | string | Etiketin donanım ID'si |

**Response `200`**

```json
{
  "status": "success",
  "data": {
    "tagId": "NFC123456",
    "title": "Ürün Tanıtım Etiketi",
    "description": "Bu etiket özel koleksiyon ürünlerine aittir.",
    "association": {
      "targetType": "PRODUCT",
      "targetId": "65f1234567890abcdef12345"
    },
    "customData": {
      "serialNumber": "SN-2024-001",
      "batch": "Summer-24"
    }
  }
}
```

**Response `404`**

```json
{
  "status": "fail",
  "message": "Tag not found"
}
```

---

## Kullanım Senaryoları

### 1. Dinamik Yönlendirme
Mobil uygulamanız bir etiketi okuduğunda:
1. `GET /api/v1/tools/nfc/:tagId` isteği atılır.
2. `association.targetType` kontrol edilir.
3. Eğer `PRODUCT` ise, uygulama içi ürün detay sayfasına (`/products/:targetId`) yönlendirme yapılır.

### 2. Bilgi Kartı Gösterimi
Etiket okunduğunda, API'den gelen `title`, `description` ve `customData` kullanılarak kullanıcıya bir "Doğrulanmış Ürün" veya "Hızlı Bilgi" kartı gösterilebilir.

### 3. Custom Metadata (Özel Veriler)
Dashboard üzerinden tanımladığınız "Seri No", "Üretim Tarihi" gibi özel alanlar `customData` objesi içinde gelir. Bu alanları sisteminizde dilediğiniz gibi işleyebilirsiniz.

---

## Notlar
- Bu API **read-only** (salt-okunur) çalışır. Etiket oluşturma veya güncelleme işlemleri için yönetim panelini (`/management`) kullanmanız gerekir.
- `customData` içeriği tenant ayarlarında "Public Görünür" olarak işaretlenmiş alanları içerir.
