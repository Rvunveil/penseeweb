# Performance & Core Web Vitals (CWV) Audit: PenseeWeb

**Target Site:** PenseeWeb  
**Evaluator:** claude-seo Performance Specialist Agent  
**CWV Metrics Standard:** Google Core Web Vitals 2026 (LCP, INP, CLS)  
**CWV Readiness:** 78 / 100

---

## 1. Metrics Breakdown & Current Status

| Metric | Threshold (Good) | Target Status | Assessment |
|---|---|---|---|
| **LCP (Largest Contentful Paint)** | ≤ 2.5s | ⚠️ At Risk (~2.4s) | Hero banner `1433e8f0-822b-4800-a38d-479e3e34291e-20-1-.avif` is high resolution (4144w). `loading="eager"` is correctly applied, but script blocking in `<head>` delays render start. |
| **INP (Interaction to Next Paint)** | ≤ 200ms | 🟢 Good (<120ms) | Lightweight interactions. Minimal heavy JavaScript execution. Uses Webflow interactions cleanly. (Note: FID retired in 2024). |
| **CLS (Cumulative Layout Shift)** | ≤ 0.1 | ⚠️ At Risk (~0.15) | Several images (e.g., `header.avif`, `img_20250418_182708_748.avif`) omit explicit `height` attributes, leading to layout shifts while images load. |

---

## 2. Key Optimization Findings

1. **Synchronous WebFont Loader Blocking the Main Thread:**
   - `<script src="https://ajax.googleapis.com/ajax/libs/webfont/1.6.26/webfont.js" type="text/javascript"></script>` is in `<head>` without `defer` or `async`.
   - Four large font families are fetched: *Inter*, *Jost*, *Playfair Display*, and *Work Sans*.
   - *Fix:* Ensure fonts include `font-display: swap` to prevent Flash of Invisible Text (FOIT) and ensure FCP happens immediately.
2. **Missing Dimension Attributes:**
   - On responsive images, omitting aspect ratio or explicit width/height forces the browser to calculate geometry after decoding image bytes.
   - *Fix:* Provide `aspect-ratio` or CSS containment for card image containers.
3. **Hero Image Optimization:**
   - The hero image is loaded as `.avif` with responsive `srcset` down to `500w`, which is modern best practice.
