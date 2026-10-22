# Image SEO & Media Optimization Audit: PenseeWeb

**Target Site:** PenseeWeb  
**Evaluator:** claude-seo Images Specialist Agent  
**Image SEO Health:** 76 / 100

---

## 1. Overview
PenseeWeb has done an admirable job adopting the next-generation **AVIF** format across the majority of site visuals, cutting raw payload by over 60% compared to traditional PNG/JPEG files.

However, several critical Image SEO and OpenGraph preview issues exist:

---

## 2. Findings & Diagnostics

### 2.1 Social Preview / Open Graph Images
- **Issue:** `index.html` sets:
  ```html
  <meta content="images/screenshot-202025-05-06-20215342.avif" property="og:image"/>
  <meta content="images/screenshot-202025-05-06-20215342.avif" property="twitter:image"/>
  ```
- **Severity: High.**
  1. Major social platforms (WhatsApp, LinkedIn, Twitter/X, Facebook, Slack) require **fully qualified absolute HTTPS URLs** (e.g., `https://penseeweb.in/images/...`).
  2. The OpenGraph specification and most social crawlers **do NOT render AVIF images** in social cards (only JPG, PNG, and GIF are universally supported). When shared on WhatsApp or Twitter, PenseeWeb shows a blank grey card or broken link preview!
  3. *Fix:* Provide an absolute `.jpg` or `.png` fallback for `og:image` and `twitter:image`.

### 2.2 Missing Alt Text on Key Visuals
- `images/picsart_25-04-04_23-02-19-993.jpg` (featured news banner on homepage and resources hub) has `alt=""`.
- Decorative arrow icons lack `aria-hidden="true"`.
- *Fix:* Provide descriptive, keyword-rich alt text for content images:
  - `alt="PenseeWeb AI Mindmapping interface demonstrating automated node generation for exam revision"`

### 2.3 Responsive `srcset` Consistency
- The hero image and mindmap samples use extensive `srcset` covering 500w to 4144w. This is great for mobile performance.
