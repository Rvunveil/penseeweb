# Structured Data & Schema.org Audit: PenseeWeb

**Target Site:** PenseeWeb (SaaS / EdTech Platform)  
**Evaluator:** claude-seo Schema Specialist Agent  
**Schema Compliance Standard:** Schema.org v26.0 / Google Search Central Rich Results (May 2026)  
**Current Schema Coverage:** 0% (0 / 10 pages contain structured data)  
**Structured Data Health:** 0 / 100 (Critical Void)

---

## 1. Executive Summary

Google and AI answer engines (ChatGPT Search, Perplexity, Gemini) rely heavily on Schema.org JSON-LD to understand entity relationships, pricing, brand identity, and topical authority.
Currently, **not a single page on PenseeWeb has any Schema.org markup** (no Microdata, no RDFa, no JSON-LD).

### What PenseeWeb Is Missing
1. **Google Knowledge Graph Entity**: Google does not have an explicit `Organization` declaration linking PenseeWeb to its social profiles, founders, or product category.
2. **SoftwareApplication Rich Snippet**: Searchers cannot see pricing (₹9 - ₹350), application category ("EducationalApplication"), or platform features directly on the SERP.
3. **Article / NewsArticle Rich Cards**: Five rich educational guides in `/resources/` cannot appear in Google News, Top Stories, or AI Overviews with author/publisher attribution.
4. **BreadcrumbList Navigation**: SERPs show raw ugly URLs instead of structured breadcrumbs (`Home > Resources > Article Name`).

---

## 2. Page-by-Page Schema Blueprint

### 2.1 Homepage (`index.html`)
- **Primary Entities:** `Organization`, `WebSite`, `WebApplication`, `BreadcrumbList`.
- **High-Leverage Properties:**
  - `applicationCategory`: `EducationalApplication`
  - `offers`: Concrete tiered pricing (Freemium: ₹0, Pay-per-map: ₹9–₹15, Subscriptions: ₹100/wk, ₹350/mo, ₹2,800/yr).
  - `operatingSystem`: `All modern web browsers (Desktop & Mobile)`
  - `sameAs`: Social media profile links.

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://penseeweb.netlify.app/#organization",
      "name": "PenseeWeb",
      "url": "https://penseeweb.netlify.app",
      "logo": "https://penseeweb.netlify.app/images/46f963da-8a3b-4910-83d0-4f154756.avif",
      "description": "India's premier AI-powered visual learning and mindmapping platform for students, competitive exam aspirants, and educators.",
      "sameAs": [
        "https://www.linkedin.com/in/penseeweb",
        "https://twitter.com/penseeweb",
        "https://instagram.com/penseeweb",
        "https://youtube.com/@penseeweb"
      ]
    },
    {
      "@type": "WebSite",
      "@id": "https://penseeweb.netlify.app/#website",
      "url": "https://penseeweb.netlify.app",
      "name": "PenseeWeb",
      "publisher": {
        "@id": "https://penseeweb.netlify.app/#organization"
      }
    },
    {
      "@type": "SoftwareApplication",
      "@id": "https://penseeweb.netlify.app/#app",
      "name": "PenseeWeb AI Mindmap Generator",
      "applicationCategory": "EducationalApplication",
      "operatingSystem": "Web",
      "url": "https://penseeweb.netlify.app",
      "offers": [
        {
          "@type": "Offer",
          "name": "Freemium Tier",
          "price": "0",
          "priceCurrency": "INR",
          "description": "3 free mindmaps on signup, then 2 free maps per month."
        },
        {
          "@type": "Offer",
          "name": "Pay-Per-Map",
          "price": "9",
          "priceCurrency": "INR",
          "description": "₹9-15 per map from user notes."
        },
        {
          "@type": "Offer",
          "name": "Monthly Pro",
          "price": "350",
          "priceCurrency": "INR",
          "description": "50 mindmaps per month with full AI features."
        }
      ],
      "featureList": [
        "AI-Powered Mindmap Generation from PDF, Notes, and Audio",
        "Syllabus-Aligned Hierarchies for Indian Exams (NEET, JEE, UPSC, CA)",
        "Panic Button™ Predictive Revision Highlight",
        "Multilingual Note Ingestion (English, Hindi, Regional)"
      ]
    }
  ]
}
```

### 2.2 Product Page (`product-page.html`)
- **Entities:** `SoftwareApplication`, `Product`, `BreadcrumbList`.
- Details features, neuro-study capabilities, and customer targeting.

### 2.3 About Page (`about.html`)
- **Entities:** `AboutPage`, `Organization`, `BreadcrumbList`.
- Connects founder leadership, team mission, and company origin.

### 2.4 Resources Hub (`resources.html`)
- **Entities:** `CollectionPage`, `BreadcrumbList`.

### 2.5 Resource Articles (`resources/*.html`)
- **Entities:** `Article` / `NewsArticle`, `BreadcrumbList`.
- Mandatory properties:
  - `headline` (matching the actual article headline, not generic "PenseeWeb Studio")
  - `description` (unique abstract)
  - `image` (featured header banner)
  - `datePublished` (valid ISO 8601, e.g., `2025-01-29`)
  - `dateModified` (ISO 8601)
  - `author`: `{"@type": "Organization", "name": "PenseeWeb Editorial Team"}`
  - `publisher`: `{"@id": "https://penseeweb.netlify.app/#organization"}`

---

## 3. Implementation Plan
- Inject server-rendered JSON-LD into the `<head>` of all 10 HTML files.
- Validate with Google's Rich Results Test guidelines.
- **Note on Quality Gates:** Avoid deprecated `HowTo` schema and retired `FAQPage` rich snippets (Google retired FAQ rich snippets globally in May 2026). Focus on high-yield `SoftwareApplication` and `Article` entities.
