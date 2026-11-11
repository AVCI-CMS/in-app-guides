# Yorum ve Puanlama API: Kullanım Kılavuzu

Yorum ve Puanlama API; ürünler, etkinlikler ve blog yazıları için kullanıcı geri bildirimlerini ve 1-5 arası yıldız puanlamalarını yönetir.

---

## 📡 Liste ve Gönderim Endpointleri

### 1. Yorumları Listele
`GET /v1/comment/:type/:id`

Belirli bir öğe (Ürün, Etkinlik vb.) için onaylanmış tüm yorumları ve puanları döndürür.
**Tipler:** `product`, `event`, `blog`, `collection`.

---

### 2. Yorum Gönder
`POST /v1/comment/:type/:id`

Yeni bir yorum ve/veya puanlama gönderir.
**İstek Gövdesi:**
```json
{
  "content": "Harika bir ürün!",
  "rating": 5,
  "images": ["resim_id_1"]
}
```

---

### 📈 Puan İstatistikleri
- `GET /v1/comment/:type/rating/stats`: Puan dağılımını (5 yıldız kaç tane, 4 yıldız kaç tane vb.) döndürür.

---

## 🚦 Onay Süreci
Tüm yorumlar sistem ayarlarınıza bağlı olarak "Onay Bekliyor" durumunda düşebilir. Public API üzerinden sadece onaylanmış yorumlar listelenir.
