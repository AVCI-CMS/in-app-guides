# Slider API

Tenant platformlarının slider ve slide verilerine erişmesi için **public** endpointler.

> [!IMPORTANT]
> - Tüm istekler `x-avci-workspace: {ID}` header'ı içermelidir (tenant seçimi için zorunlu).
> - Yalnızca `status: PUBLISHED` olan slider ve slide'lar döner.

**Base URL (tenant için):** `/api/v1/slider`

Tüm endpoint örnekleri bu base altında düşünülmelidir:

- Tüm slider listesi: `GET /api/v1/slider`
- Slug ile slider: `GET /api/v1/slider/:slug`
- ID ile slider: `GET /api/v1/slider/id/:_id`

---

## Endpoints

### 1. Tüm Slider Listesi

**`GET /api/v1/slider`**

Aktif tenant workspace’e ait tüm **PUBLISHED** slider’ların **özet** listesini döner.

**Headers**

| Header             | Tip    | Açıklama                          |
|--------------------|--------|-----------------------------------|
| `x-avci-workspace` | string | Tenant workspace ID (zorunlu)    |

**Query Params**

Yok – tüm published slider’lar döner (backend’de pagination yok).

**Response `200`**

```json
{
  "status": "success",
  "data": [
    {
      "_id": "665f...",
      "title": "Ana Sayfa Hero",
      "slug": "ana-sayfa-hero",
      "type": "hero",
      "description": "Ana sayfa için hero slider"
    }
  ]
}
```

> [!NOTE]
> Bu endpoint yalnızca slider özet bilgilerini döner; slide listesi içermez.

---

### 2. Slug ile Slider Getir

**`GET /api/v1/slider/:slug`**

Belirtilen `slug`’a sahip slider’ı, içindeki tüm **PUBLISHED** slide’larla birlikte döner.

**Headers**

| Header             | Tip    | Açıklama                          |
|--------------------|--------|-----------------------------------|
| `x-avci-workspace` | string | Tenant workspace ID (zorunlu)    |

**Path Params**

| Parametre | Tip    | Açıklama               |
|-----------|--------|------------------------|
| `slug`    | string | Slider'ın slug değeri  |

**Response `200`**

```json
{
  "status": "success",
  "data": {
    "_id": "665f...",
    "title": "Ana Sayfa Hero",
    "slug": "ana-sayfa-hero",
    "type": "hero",
    "status": "PUBLISHED",
    "slides": [
      {
        "_id": "abc1...",
        "title": "Yaz Kampanyası",
        "subtitle": "Sezon indirimleri başladı",
        "text": "Tüm ürünlerde %30'a varan indirim",
        "slideType": "basic",
        "order": 0,
        "image": {
          "_id": "img1...",
          "url": "https://storage.googleapis.com/...",
          "width": 1920,
          "height": 600
        },
        "mobileImage": {
          "_id": "img2...",
          "url": "https://storage.googleapis.com/...",
          "width": 768,
          "height": 400
        },
        "CTA": {
          "title": "Hemen Keşfet",
          "url": "/urunler",
          "target": "_self"
        }
      }
    ]
  }
}
```

**Response `404`**

```json
{ "status": "error", "message": "Slider not found" }
```

---

### 3. ID ile Slider Getir

**`GET /api/v1/slider/id/:_id`**

Slug yerine MongoDB `_id` ile slider getirmek için kullanılır. Yine yalnızca **PUBLISHED** slider döner.

**Headers**

| Header             | Tip    | Açıklama                          |
|--------------------|--------|-----------------------------------|
| `x-avci-workspace` | string | Tenant workspace ID (zorunlu)    |

**Path Params**

| Parametre | Tip    | Açıklama      |
|-----------|--------|---------------|
| `_id`     | string | Slider ID'si  |

**Response `200`**

Response yapısı `/api/v1/slider/:slug` endpoint’i ile **aynıdır**:

- `data` içinde slider objesi
- `slides` alanı altında **PUBLISHED** slide’lar

**Response `404`**

```json
{ "status": "error", "message": "Slider not found" }
```

---

## Slide Tipleri

Backend’de `slideType` alanı aşağıdaki enum değerlerini kullanır:

| `slideType` | Açıklama                                                 |
|-------------|----------------------------------------------------------|
| `basic`     | Başlık, açıklama, görsel ve CTA                          |
| `advanced`  | Özel layout ve ek alanlar (özelleştirilebilir kullanım)  |
| `video`     | `videoUrl` alanı aktif, görsel opsiyonel                 |

---

## Davranış & Notlar

- Slider’lar ve slide’lar yalnızca `status: PUBLISHED` ise public endpoint’lerden döner.
- Slide’lar slider detayında **`order` alanına göre küçükten büyüğe** sıralı döner.
- `mobileImage` varsa mobil cihazlar için öncelikle bu görsel kullanılmalı; yoksa `image` fallback olarak kullanılabilir.
- `CTA.target` değeri `_self` veya `_blank` olabilir.
- `image` ve `mobileImage` alanları, `Image` koleksiyonundan `lookup` ile zenginleştirilmiş nesnelerdir (url, boyutlar vb.).
