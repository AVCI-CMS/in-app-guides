# Medya (Media) API: Detay ve Teknik Standartlar

Sistem içindeki görsellerin türlerine göre nasıl organize edildiği ve teknik kısıtlamalar hakkında detaylı bilgi sağlar.

---

## 📁 Görsel Türleri (Types)
Görseller, ilişkili oldukları modüllere göre klasörlenir:
- `product`: Ürün resimleri.
- `blog`: Makale görselleri.
- `avatar`: Kullanıcı profil resimleri.
- `category`: Kategori kapak resimleri.
- `brand` / `merchant`: Kurumsal logolar.

---

## 📐 Boyutlandırma Standartları
Maksimum performans için önerilen `fit` değerleri:
- `cover`: Görüntüyü kırparak belirtilen alanı tamamen doldurur (En çok kullanılan).
- `contain`: Görüntüyü sığdırır, boş kalan yerleri şeffaf bırakır.

---

## 🔐 Güvenlik ve CORS
Her görsel isteği `Cross-Origin-Resource-Policy: cross-origin` başlığı ile döner. Bu sayede tarayıcılar arası güvenlik politikalarına takılmadan her platformda (Web, Mobil, React Native) sorunsuz çalışır.
