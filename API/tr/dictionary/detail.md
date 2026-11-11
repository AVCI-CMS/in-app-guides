# Sözlük (Word) API: Detay Kılavuzu

Tek bir kelimenin tam dil bilimsel, tarihsel ve pedagojik profiline erişmek için kullanılır.

---

## 📄 Detay Endpointler

### 1. Kelime Detaylarını Getir
`GET /v1/word/:slug`

Kelimenin tanımını, telaffuzunu, kökenini ve örnek kullanımlarını döndürür.

**Örnek Yanıt:**
```json
{
  "name": "Çömlekçilik",
  "slug": "comlekcilik",
  "definition": "Toprağı çamur haline getirip şekil verdikten sonra pişirme sanatı.",
  "partOfSpeech": "İsim",
  "phonetic": "/t͡ʃømlekˈt͡ʃilik/",
  "etymology": "Türkçe 'çömlek' isminden türetilmiştir.",
  "synonyms": ["Keramik", "Zanaat"],
  "examples": [
    "Anadolu'da çömlekçilik binlerce yıllık bir gelenektir."
  ]
}
```

---

## 🔗 Dil Bilimsel Alanlar
- `partOfSpeech`: Sözcük türü (İsim, Fiil, Sıfat vb.).
- `phonetic` / `pronunciation`: Kelimenin okunuşu.
- `synonyms` / `antonyms`: Eş anlamlılar ve zıt anlamlılar.

---

## 💬 Etkileşimler
- `/v1/word/category`: Sözlük kategorileri.
- `/v1/word/like/:slug`: Kelimeyi favorilere ekle.
- `/v1/word/share/:slug`: Kelime paylaşım takibi.
