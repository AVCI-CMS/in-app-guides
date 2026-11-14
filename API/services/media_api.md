# Media API & On-The-Fly Resizing (`resizeonfly`)

The Media API provides dynamic, real-time image processing (`resizeonfly`) and direct access to tenant-specific visual assets like logos and favicons. It transforms images on-demand using libvips/Sharp without pre-generating static files.

## Base URL
`GET /v1/images`

---

## On-The-Fly Image Transformation
`GET /v1/:tenant/images/:type/:filename`

Processes and streams an image according to dimension, format, and fit parameters.

**Path Parameters:**
- `tenant`: The workspace ID or slug (e.g., `avci`, `my-store`).
- `type`: Category of the image (`product`, `blog`, `avatar`, `cover`, `event`, `general`).
- `filename`: The unique name of the stored image.

**Query Parameters:**
| Parameter | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `w` | `number` | - | Width in pixels (e.g. `?w=400`). Height is computed automatically. |
| `h` | `number` | - | Height in pixels (e.g. `?h=300`). Width is computed automatically. |
| `q` | `number` | `85` | Quality (`1` to `100`). |
| `f` | `string` | `auto` | Target format (`webp`, `avif`, `jpeg`, `png`, `auto`). Auto negotiates via `Accept` header. |
| `fit` | `string` | `inside` | Fitting strategy: `inside` (default), `cover`, `contain`, `fill`, `outside`. |
| `auto` | `boolean` | `false` | When `true`, automatically detects device type (mobile/desktop) and adapts width & quality. |

**Practical Examples:**
- **Product Listing Thumbnail:**
  `GET /v1/my-store/images/product/item-01.jpg?w=300&f=webp`
- **Hero Cover Banner (21:9 Fixed Crop):**
  `GET /v1/my-store/images/cover/banner.jpg?w=1200&h=514&fit=cover&f=webp&q=90`
- **Device-Adaptive Delivery:**
  `GET /v1/my-store/images/blog/post-hero.jpg?auto=true`

---

## Global Identity Assets
These endpoints automatically resolve the active workspace from session or headers and support all resize query parameters.

### Get Logo
`GET /v1/logo` or `GET /v1/logo/:tenant/:filename`
Example: `GET /v1/logo?w=200&f=webp`

### Get Favicon
`GET /v1/favicon` or `GET /v1/favicon/:tenant/:filename`
Example: `GET /v1/favicon?w=64&h=64`

---

## Technical Performance Details
- **Immutable CDN Caching:** All transformed images return `Cache-Control: public, max-age=31536000, immutable`.
- **Dimensions Headers:** Responses include `X-Image-Width` and `X-Image-Height` reporting the rendered resolution.
- **Cross-Origin Accessibility:** Headers `Access-Control-Allow-Origin: *` and `Cross-Origin-Resource-Policy: cross-origin` enable unblocked embedding across web and mobile apps.
