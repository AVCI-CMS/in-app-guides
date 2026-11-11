# Media API: Detail and Technical Standards

Provides detailed information about how images are organized by types and technical constraints.

---

## 📁 Image Types
Images are categorized by their related modules:
- `product`: Product images.
- `blog`: Article visuals.
- `avatar`: User profile pictures.
- `category`: Category cover images.
- `brand` / `merchant`: Corporate logos.

---

## 📐 Resizing Standards
Recommended `fit` values for maximum performance:
- `cover`: Crops the image to fill the specified area (Most common).
- `contain`: Fits the image within the area, leaving whitespace where necessary.

---

## 🔐 Security and CORS
Every image request returns with `Cross-Origin-Resource-Policy: cross-origin` header, ensuring it works seamlessly across different platforms (Web, Mobile, React Native).
