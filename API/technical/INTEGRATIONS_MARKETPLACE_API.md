# Entegrasyon ve Pazaryeri (Marketplace) API Rehberi

Bu doküman, AVCI-CMS üzerinde tenantların (workspace sahipleri) kendi uygulamalarını yönetmeleri, entegrasyon kataloguna erişmeleri ve üçüncü parti servisleri (Ödeme, E-posta, SMS vb.) yapılandırmaları için gerekli endpointleri kapsar.

> [!NOTE]
> Bu rehberdeki tüm işlemler için ilgili workspace üzerinde `Workspaces:Settings` iznine sahip olunması gerekmektedir.

## 🔑 Temel Kavramlar

### Authentication
Tüm yönetimsel endpoint'ler Bearer Token gerektirir:
`Authorization: Bearer <ACCESS_TOKEN>`

### Workspace Kimliği
Tüm requestlerde ilgili workspace'in ID'si header olarak gönderilmelidir:
`x-avci-workspace: <WORKSPACE_ID>`

---

## 📡 Entegrasyon Kataloğu (Marketplace)

Kullanıcıların mevcut uygulamaları görebileceği ve detaylarını inceleyebileceği endpointlerdir.

### 1. Katalog Listesini Getir
Sistemde tanımlı tüm aktif entegrasyonları getirir.

**Endpoint:** `GET /v1/workspace/v2/integrations/management/:id/catalog`

**Response:**
```typescript
{
  "status": "success",
  "data": [
    {
      "_id": "65f...",
      "name": "mailjet",
      "displayName": "Mailjet",
      "category": "EMAIL",
      "description": "...",
      "logo": "/images/...",
      "fields": [...] // Gerekli olan ayar alanları
    },
    ...
  ]
}
```

### 2. Belirli Bir Katalog Öğesini Getir
Belirli bir uygulamanın kurulum adımlarını, özelliklerini ve gereksinimlerini getirir.

**Endpoint:** `GET /v1/workspace/v2/integrations/management/:id/catalog/:catalogId`

---

## ⚙️ Entegrasyon Yönetimi

Tenant'ın kendi workspace'ine özel yapılandırmaları yönettiği bölümdür.

### 1. Aktif Entegrasyonları Listele
Workspace'te kurulu olan tüm entegrasyonların durumunu getirir.

**Endpoint:** `GET /v1/workspace/v2/integrations/management/:id`

**Response:**
```typescript
{
  "status": "success",
  "data": [
    {
      "type": "MAILJET",
      "category": "EMAIL",
      "enabled": true,
      "configured": true,
      "lastTested": "2024-03-14T...",
      "lastTestResult": { "success": true, "message": "OK" }
    }
  ]
}
```

### 2. Entegrasyonu Yapılandır / Güncelle
Bir uygulamayı aktif etmek veya ayarlarını (API Key, Secret vb.) güncellemek için kullanılır.

**Endpoint:** `PATCH /v1/workspace/v2/integrations/management/:id/:type`

**Request Body (Örnek: Mailjet):**
```json
{
  "enabled": true,
  "settings": {
    "apiKey": "your-api-key",
    "apiSecret": "your-api-secret",
    "fromEmail": "noreply@domain.com",
    "fromName": "Şirket Adı"
  }
}
```

### 3. Bağlantıyı Test Et
Yapılandırılan uygulamanın API bağlantısının doğru olup olmadığını doğrular.

**Endpoint:** `POST /v1/workspace/v2/integrations/management/:id/:type/test`

### 4. Durumu Değiştir (Enable/Disable)
Entegrasyonu silmeden geçici olarak durdurmak veya yeniden başlatmak için kullanılır.

- **Aktif Et:** `POST /v1/workspace/v2/integrations/management/:id/:type/enable`
- **Durdur:** `POST /v1/workspace/v2/integrations/management/:id/:type/disable`

---

## 🛠️ Desteklenen Entegrasyon Tipleri

Aşağıdaki tipler uygulamaları tanımlamak için `type` parametresi olarak kullanılır:

| Tip | Kategori | Açıklama |
| :--- | :--- | :--- |
| `MAILJET` | EMAIL | E-posta gönderim servisi |
| `RESEND` | EMAIL | Modern e-posta API servisi |
| `IYZICO` | PAYMENT | Ödeme sistemi altyapısı |
| `VERIMOR` | SMS | SMS gönderim servisi |
| `SLACK` | NOTIFICATION | Kanal bildirimleri |

---

## 🚀 Kendi Uygulamanızı Bağlama (Custom App)

Eğer tenant kendi geliştirdiği bir mobil uygulamayı veya web sitesini AVCI-CMS'e bağlamak istiyorsa:

1. **API Key Alımı:** Workspace ayarlarından API anahtarları oluşturun (Geliştirme aşamasında).
2. **Public API Kullanımı:** Storefront/App işlemleri için [Public API](./INTRODUCTION.md) dokümanlarını takip edin.
3. **Webhooks:** Sistemdeki olayları (sipariş verildi, stok bitti vb.) takip etmek için 'Notification' entegrasyonları altında custom webhook yapılandırması yapılabilir.
