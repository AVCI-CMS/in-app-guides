# Media API: Technical Standards & On-The-Fly Resizing

Provides detailed specifications on how images are stored, categorized, and dynamically transformed on-the-fly via the `resizeonfly` pipeline.

---

## 📁 Image Types & Directories
Images are categorized by functional module folders:
- `product`: Product gallery and thumbnail images.
- `blog`: Article banners and rich-text editorial inline visuals.
- `avatar`: User and team member profile photos.
- `category`: Category banner and icon graphics.
- `cover`: 21:9 ultra-wide page and header banners.
- `brand` / `merchant`: Merchant showcase logos and verification badges.
- `place`: Physical venue stage and exterior photos.

---

## 📐 On-The-Fly Resizing Parameters (`resizeonfly`)
Append query parameters to any image URL (`GET /v1/:tenant/images/:type/:filename`):
- `w`: Width in pixels (`?w=400`).
- `h`: Height in pixels (`?h=300`).
- `q`: Quality from 1 to 100 (Default: `85`).
- `f`: Format (`webp`, `avif`, `jpeg`, `png`, `auto`).
- `fit`: Sizing strategy (`inside` [default - maintains aspect ratio], `cover`, `contain`).
- `auto`: `auto=true` enables mobile/desktop user-agent adaptive optimization.

**Example Request:**
```http
GET /v1/demo/images/product/sneakers.jpg?w=400&fit=inside&f=webp
```

---

## 🔐 Performance & Caching Headers
- `Cache-Control: public, max-age=31536000, immutable`: Long-term 1-year browser and CDN cache.
- `X-Image-Width` and `X-Image-Height`: Actual rendered dimensions.
- `Cross-Origin-Resource-Policy: cross-origin`: Prevents cross-origin embedding blocking in modern browsers and React Native.
