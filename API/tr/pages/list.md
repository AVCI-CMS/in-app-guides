# Sayfa API: Liste Kılavuzu

Sayfa API; "Hakkımızda", "Gizlilik Politikası" veya özel kampanya sayfaları gibi statik ve dinamik içerikleri yönetir.

---

## 📡 Liste Endpointler

### 1. Sayfaları Listele
`GET /v1/page`

Tüm aktif sayfaları liste halinde döndürür.

**Sorgu Parametreleri:**
- `page`: Sayfa numarası
- `limit`: Öğe sayısı
- `language`: Dil kodu (`en`, `tr`)
- `category`: Sayfa grubu

---

## 🚦 Sayfa Durumları

| Durum | Açıklama |
| :--- | :--- |
| `PUBLISHED` | Sayfa yayında ve erişilebilir. |
| `HIDDEN` | Sayfa sadece doğrudan link ile erişilebilir, listelerde görünmez. |
| `DRAFT` | Sayfa hazırlık aşamasındadır. |
