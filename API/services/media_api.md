# Media API Guide

The Media API provides dynamic image processing and access to workspace-specific visual assets like logos and favicons. It supports high-performance on-the-fly transformations via a dedicated worker.

## Base URL
`GET /v1/images`

---

## Image Transformation
`GET /v1/:tenant/images/:type/:filename`

Processes an image based on the provided tenant and transformation parameters.

**Path Parameters:**
- `tenant`: The workspace ID or slug.
- `type`: Category of the image (e.g., `product`, `blog`, `avatar`).
- `filename`: The unique name of the stored image.

**Query Parameters:**
| Parameter | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `w` | `number` | - | Width in pixels. |
| `h` | `number` | - | Height in pixels. |
| `q` | `number` | 80 | Quality (1-100). |
| `f` | `string` | - | Target format (`webp`, `jpeg`, `png`). |
| `fit` | `string` | `cover` | `cover`, `contain`, `fill`, `inside`, `outside`. |

**Example:**
`GET /v1/my-workspace/images/product/item-01.jpg?w=800&f=webp`

---

## Global Assets
These endpoints automatically resolve the active workspace from the session or headers.

### Get Logo
`GET /v1/logo`

### Get Favicon
`GET /v1/favicon`

*Note: Logo and Favicon endpoints support the same transformation query parameters as standard images.*

---

## Technical Details
- **CORS & CORP**: Every image response includes `Access-Control-Allow-Origin: *` and `Cross-Origin-Resource-Policy: cross-origin` for seamless frontend integration.
- **Cache**: Transformed images follow the workspace's caching policies and are served via a global CDN when enabled.
