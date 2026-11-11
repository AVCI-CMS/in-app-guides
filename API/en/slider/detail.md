# Slider API: Slide Detail and Structure

Used to access all slides (visuals, text, links) within a specific slider.

---

## 📄 Detail Endpoints

### 1. Get Slider by Slug
`GET /v1/slider/:slug`

Returns the slider and its ordered, published slides.

**Sample Slide Structure:**
```json
{
  "title": "Summer Campaign",
  "slideType": "basic",
  "order": 0,
  "image": { "url": "...", "width": 1920, "height": 600 },
  "mobileImage": { "url": "...", "width": 768, "height": 400 },
  "CTA": { "title": "Explore", "url": "/products" }
}
```

---

## 🖼️ Slide Types
- `basic`: Title, subtitle, visual, and CTA button.
- `video`: Supporting video URL in the background.
- `advanced`: Additional metadata fields for custom layout designs.

---

## 📱 Mobile Support
If `mobileImage` is defined, it should be used on mobile devices for performance and display. If undefined, the main `image` can be used as a fallback.
