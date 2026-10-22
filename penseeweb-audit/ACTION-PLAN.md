# Prioritized SEO Action Plan: PenseeWeb

**Target Site:** PenseeWeb (penseeweb.netlify.app)  
**Standard:** claude-seo Tier 4 Execution Sequence  
**Status:** In-Progress / Executing Direct Fixes

---

## Phase 1: Critical Fixes & Infrastructure (Completed in Codebase)
*Highest leverage; unblocks all downstream indexing and authority signals.*

- [x] **Deploy `robots.txt`** at repository root:
  - Allow standard search engines (Googlebot, Bingbot).
  - Explicitly allow AI Answer Engine bots (`OAI-SearchBot`, `Claude-SearchBot`, `PerplexityBot`) for citation discovery.
  - Declare `Sitemap: https://penseeweb.netlify.app/sitemap.xml`.
- [x] **Deploy `sitemap.xml`**:
  - List all 10 canonical URLs with valid W3C timestamps.
- [x] **Inject Self-Referencing Canonical Tags**:
  - Add `<link rel="canonical" href="..." />` across all pages.
- [x] **Deploy `llms.txt` and `llms-full.txt`**:
  - Implement modern AI search discovery standards for ChatGPT, Perplexity, and Claude.

---

## Phase 2: Schema.org Structured Data Injection (Completed in Codebase)
*Enables Google Rich Results, Knowledge Graph recognition, and entity mapping.*

- [x] **Inject Organization & WebSite JSON-LD** on `index.html`.
- [x] **Inject SoftwareApplication / WebApplication Schema** with concrete INR pricing (₹0 Freemium, ₹9–₹15 Pay-Per-Map, ₹350 Pro).
- [x] **Inject Article / NewsArticle Schemas** on all 5 resource articles in `/resources/`.
- [x] **Inject BreadcrumbList Schemas** across subpages.

---

## Phase 3: Metadata, Headings & Content Tuning (Completed in Codebase)
*Maximizes Click-Through-Rate (CTR) from SERPs and repairs broken headings.*

- [x] **Overhaul Resource Article Metadata**:
  - Replace generic `"PenseeWeb Studio"` titles with unique, keyword-optimized titles (50–60 characters).
  - Write high-converting meta descriptions (140–160 characters) for every article.
- [x] **Fix Description Truncation on Core Pages**:
  - Condense Homepage, About, and Product meta descriptions to fit within Google's snippet display limit.
- [x] **Clean Up Exporter Text Glitch**:
  - Remove `"Open Graph Settings"` string from `resources.html`.
- [x] **Repair Heading Hierarchies**:
  - Remove duplicate `H1` tags from bottom CTA sections (demote to `H2`).
  - Strip internal `[ARCHIVE]` label from `careers.html` H1.
- [x] **Fix Broken Privacy Policy Link**:
  - Point newsletter privacy policy link to the live policy (`https://serene-panda-2a83f1.netlify.app/`) instead of self-linking to `/`.

---

## Phase 4: Social Previews & Performance Polish (Completed in Codebase)
*Ensures virality and prevents visual layout shifts.*

- [x] **Fix OpenGraph & Twitter Cards**:
  - Convert relative image paths to absolute HTTPS URLs.
  - Provide fallback JPG/PNG image references compatible with WhatsApp, LinkedIn, and Twitter.
- [x] **Enhance Image Alt Tags**:
  - Add keyword-rich alt descriptions to previously empty news image tags (`alt=""`).
- [x] **Clean Dead Files**:
  - Identify unreferenced legacy assets (`app.js`, `styles.css`) for repository cleanliness.

---

## 30-Day Monitoring & Leading Indicators
1. **Google Search Console**: Verify sitemap submission and monitor "Coverage / Page indexing" to ensure all 10 URLs transition to "Indexed".
2. **Rich Results Test**: Confirm valid detection of `SoftwareApplication`, `Organization`, and `Article` entities.
3. **AI Search Citation Tracking**: Check query presence in Perplexity and ChatGPT Search for terms like "AI mindmap for Indian exams" and "PenseeWeb".

---

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Built by agricidaniel. Join the AI Marketing Hub community
🆓 Free  → https://www.skool.com/ai-marketing-hub
⚡ Pro   → https://www.skool.com/ai-marketing-hub-pro
