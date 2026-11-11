# Media API: List and Processing Guide

The Media API provides high-performance delivery and dynamic processing of visual assets (images, logos, icons).

---

## 📡 List and Access Endpoints

### 1. Image Transformation
`GET /v1/:tenant/images/:type/:filename`

Processes images in specified dimensions and quality in real-time.

**Query Parameters:**
- `w`: Width (px)
- `h`: Height (px)
- `q`: Quality (1-100, Default: `80`)
- `f`: Target format (`webp`, `jpeg`, `png`)
- `fit`: Resizing type (`cover`, `contain`, etc.)

**Example:**
`GET /my-workspace/images/product/item-01.jpg?w=800&f=webp`

---

## 🚀 Corporate Assets
Automatically resolved endpoints for the authenticated workspace:
- `GET /v1/logo`: Official corporate logo.
- `GET /v1/favicon`: Official browser icon.

---

## 🚦 Technical Details
- **Global Access:** All images are served with `CORS: *` header for seamless integration.
- **Optimization:** Images are automatically optimized and cached on the cloud.
