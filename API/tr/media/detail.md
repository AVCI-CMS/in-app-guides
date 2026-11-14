# Medya (Media) API: Teknik Standartlar ve Anlık Boyutlandırma (`resizeonfly`)

Sistem içindeki görsellerin türlerine göre nasıl organize edildiği ve `resizeonfly` motoru ile nasıl anlık olarak işlendiği hakkında detaylı bilgi sağlar.

---

## 📁 Görsel Türleri (Types)
Görseller, ilişkili oldukları modüllere göre klasörlenir:
- `product`: Ürün küçük resimleri ve galeri fotoğrafları.
- `blog`: Makale kapakları ve zengin metin içi görseller.
- `avatar`: Kullanıcı ve ekip üyesi profil fotoğrafları.
- `category`: Kategori kapak ve simge grafikleri.
- `cover`: 21:9 geniş kapak ve sayfa banner'ları.
- `brand` / `merchant`: Kurumsal logolar ve satıcı vitrin görselleri.
- `place`: Mekan salon ve dış cephe fotoğrafları.

---

## 📐 Anlık Boyutlandırma Parametreleri (`resizeonfly`)
Herhangi bir görsel adresine (`GET /v1/:tenant/images/:type/:filename`) sorgu parametresi eklenerek anında dönüştürme sağlanır:
- `w`: Piksel cinsinden genişlik (`?w=400`). Yükseklik orantılı hesaplanır.
- `h`: Piksel cinsinden yükseklik (`?h=300`). Genişlik orantılı hesaplanır.
- `q`: Sıkıştırma kalitesi (1-100, Varsayılan: `85`).
- `f`: Hedef format (`webp`, `avif`, `jpeg`, `png`, `auto`).
- `fit`: Boyutlandırma stratejisi (`inside` [varsayılan - oranı korur], `cover`, `contain`).
- `auto`: `auto=true` ile cihaz tespiti yapılarak otomatik boyutlandırma sağlanır.

**Örnek İstek:**
```http
GET /v1/demo/images/product/ayakkabi.jpg?w=400&fit=inside&f=webp
```

---

## 🔐 Performans ve Önbellek Başlıkları
- `Cache-Control: public, max-age=31536000, immutable`: CDN ve tarayıcıda 1 yıllık değişmez önbellekleme.
- `X-Image-Width` ve `X-Image-Height`: İşlenmiş gerçek boyut bilgisi.
- `Cross-Origin-Resource-Policy: cross-origin`: Tarayıcılar arası güvenlik politikalarına takılmadan tüm platformlarda (Web, Mobil, React Native) sorunsuz yüklenme sağlar.
