# Sözlük (Word) API: Liste Kılavuzu

Sözlük API; kavramlar, terimler ve dil bilimsel veriler için kapsamlı bir sözlük hizmeti sağlar. Etimoloji, telaffuz ve sözcük türü gibi detayları destekler.

---

## 📡 Liste Endpointler

### 1. Kelimeleri Listele
`GET /v1/word`

Sözlükteki tüm kelimeleri sayfalamalı olarak döndürür.

**Sorgu Parametreleri:**
- `page`: Sayfa numarası
- `limit`: Öğe sayısı
- `category`: Sözlük kategorisi
- `language`: Dil kodu (`en`, `tr`)
- `search`: Kelime veya tanım içinde arama

---

## 🚦 Temel Durumlar
- `PUBLISHED`: Yayında ve sözlükte görünür.
- `HIDDEN`: Sadece doğrudan linkle erişilebilir.
- `DRAFT`: Hazırlık aşamasında.
