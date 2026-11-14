# Media Management: File Detail, Visual Editor, and Optimization

Manage asset details, crop images to precise presets, rotate, and access optimized CDN addresses.

---

## 🎨 Built-in Visual Editor (`ImageEditor`)
Click the "Edit" button on any selected media to open the canvas editor:
- **Aspect Ratio Presets:** Select from `Free`, `1:1` (Square/Logo), `16:9` (Featured/Video), `21:9` (Cover Banner), or `4:3` (Standard).
- **Rotation & Angle:** Use the 90° flip buttons or the fine rotation slider (-45° to +45°) to straighten tilted photos.
- **Zoom & Pan:** Smoothly zoom from 0.1x to 3.0x to focus on important details.
- **Save Actions:** Use "Save" to update the file in place or "Save as New" to create a transformed duplicate.

---

## 🖼️ Media Explorer & Organization
- **Hierarchical Folders:** Organize large collections with the "New Folder" button (e.g. `/summer-2026/campaign/`).
- **Live Search:** Quickly filter assets by typing the filename or title.
- **One-Click CDN Copy:** Copy the public URL for instant embedding in blogs or emails.

---

## 💡 On-The-Fly Optimization
Every visual uploaded to AVCI CMS is served via the `resizeonfly` engine. When you request an image with dimensions (e.g., `?w=400`), it is dynamically scaled and served in modern **WebP** or **AVIF** format, keeping site load speed lightning fast.
