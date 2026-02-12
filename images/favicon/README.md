# Favicon

- **favicon.svg** – Source mark (rounded square with site gradient). Used as the main favicon in modern desktop browsers.
- **safari-pinned-tab.svg** – Same shape, single color; Safari tints it with `color="#3d5a80"` for pinned tabs.

## Full coverage (iOS, Android, etc.)

The SVG alone does **not** cover all cases:

| Scenario | What’s used | Status |
|----------|-------------|--------|
| Desktop tab | `favicon.svg` | ✅ In place |
| iOS Safari tab | Often uses PNG (16×32) | ⚠️ Replace PNGs with gradient mark |
| iOS Add to Home Screen | `apple-touch-icon.png` (120×120) | ⚠️ Replace with gradient mark |
| Android / PWA | Icons in `site.webmanifest` | ⚠️ Replace and fix paths |

To get the gradient mark everywhere:

1. **Export PNGs from the SVG**  
   Use [realfavicongenerator.net](https://realfavicongenerator.net/): upload `favicon.svg` (or a 512×512 PNG exported from it), then generate and download the package.

2. **Replace these files** with the generated ones:
   - `favicon.ico`
   - `favicon-16x16.png`
   - `favicon-32x32.png`
   - `apple-touch-icon.png` (and 180×180 if generated)
   - `android-chrome-96x96.png` (and any 192×192 / 512×512 if you want them)
   - `mstile-150x150.png` (optional, Windows tile)

3. **Fix the web manifest**  
   In `site.webmanifest`, set icon paths to match where you put the PNGs (e.g. `"/images/favicon/android-chrome-96x96.png"`) and set `name`, `short_name`, `theme_color`, and `background_color` to match the site.

After that, the same gradient mark will be used for desktop, iOS (tab + home screen), and Android/PWA.
