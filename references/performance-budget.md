# Performance Budget Reference

Core Web Vitals targets and optimization strategies.

## Core Web Vitals Targets

| Metric | Good | Needs Improvement | Poor |
|--------|------|-------------------|------|
| **LCP** (Largest Contentful Paint) | ≤2.5s | 2.5s–4s | >4s |
| **INP** (Interaction to Next Paint) | ≤200ms | 200ms–500ms | >500ms |
| **CLS** (Cumulative Layout Shift) | ≤0.1 | 0.1–0.25 | >0.25 |

## Resource Budgets

### JavaScript
| Type | Budget |
|------|--------|
| Total JS | <200KB gzipped |
| Main bundle | <100KB gzipped |
| Per-route chunk | <50KB gzipped |
| Third-party JS | <50KB total |

### CSS
| Type | Budget |
|------|--------|
| Total CSS | <50KB gzipped |
| Critical CSS | <14KB (inline) |
| Per-component | <5KB |

### Images
| Type | Budget |
|------|--------|
| Hero image | <200KB |
| Thumbnail | <30KB |
| Icon/Logo | <10KB |
| Total page images | <1MB |

### Fonts
| Type | Budget |
|------|--------|
| Total fonts | <100KB |
| Per font family | <50KB |
| Variable font | <150KB |

## Page Load Budgets

| Metric | Target |
|--------|--------|
| Time to First Byte (TTFB) | <200ms |
| First Contentful Paint (FCP) | <1.8s |
| Largest Contentful Paint (LCP) | <2.5s |
| Time to Interactive (TTI) | <3.8s |
| Total Page Size | <1.5MB |
| HTTP Requests | <50 |

## Optimization Strategies

### LCP Optimization

```html
<!-- Preload hero image -->
<link rel="preload" as="image" href="hero.webp" fetchpriority="high">

<!-- Use responsive images -->
<img src="hero.webp"
     srcset="hero-400.webp 400w,
             hero-800.webp 800w,
             hero-1200.webp 1200w"
     sizes="100vw"
     alt="Hero image"
     loading="eager"
     fetchpriority="high">

<!-- Preconnect to critical origins -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://cdn.example.com" crossorigin>
```

### INP Optimization

```javascript
// Break up long tasks
function processLargeDataset(data) {
  const chunks = splitIntoChunks(data, 100);

  function processChunk(index) {
    if (index >= chunks.length) return;

    processData(chunks[index]);

    // Yield to main thread
    setTimeout(() => processChunk(index + 1), 0);
  }

  processChunk(0);
}

// Use requestIdleCallback for non-urgent work
requestIdleCallback(() => {
  analytics.track('page_view');
});
```

### CLS Optimization

```css
/* Reserve space for images */
img, video {
  aspect-ratio: 16 / 9;
  width: 100%;
  height: auto;
}

/* Reserve space for ads/embeds */
.ad-container {
  min-height: 250px;
}

/* Prevent font swap layout shift */
@font-face {
  font-family: 'CustomFont';
  src: url('font.woff2') format('woff2');
  font-display: optional; /* or swap with size-adjust */
  size-adjust: 100.5%;
}
```

### Critical CSS

```html
<head>
  <!-- Inline critical CSS -->
  <style>
    /* Above-the-fold styles only */
    :root { --primary: #3b82f6; }
    body { margin: 0; font-family: system-ui; }
    .hero { min-height: 100vh; display: flex; align-items: center; }
    /* ... */
  </style>

  <!-- Defer non-critical CSS -->
  <link rel="preload" href="styles.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
  <noscript><link rel="stylesheet" href="styles.css"></noscript>
</head>
```

### Image Optimization

```html
<!-- Modern formats with fallback -->
<picture>
  <source srcset="image.avif" type="image/avif">
  <source srcset="image.webp" type="image/webp">
  <img src="image.jpg" alt="Description" loading="lazy">
</picture>

<!-- Lazy loading for below-fold images -->
<img src="image.webp" alt="Description" loading="lazy" decoding="async">
```

### Font Optimization

```css
/* System font stack (zero load time) */
font-family: system-ui, -apple-system, BlinkMacSystemFont,
             'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;

/* If custom fonts needed */
@font-face {
  font-family: 'Inter';
  src: url('inter.woff2') format('woff2');
  font-display: swap;
  unicode-range: U+0000-00FF; /* Latin only subset */
}
```

### Code Splitting

```javascript
// React lazy loading
const Dashboard = lazy(() => import('./Dashboard'));

// Route-based splitting
const routes = [
  {
    path: '/dashboard',
    component: lazy(() => import('./pages/Dashboard'))
  }
];

// Dynamic imports for features
button.addEventListener('click', async () => {
  const { processData } = await import('./heavy-module');
  processData();
});
```

## Monitoring Checklist

- [ ] Set up Real User Monitoring (RUM)
- [ ] Configure Lighthouse CI in pipeline
- [ ] Set performance budgets in bundler
- [ ] Monitor Core Web Vitals in Search Console
- [ ] Alert on performance regressions

## Quick Audit Commands

```bash
# Lighthouse CLI
lighthouse https://example.com --only-categories=performance

# WebPageTest
# Use https://www.webpagetest.org/

# Bundle analyzer (webpack)
npx webpack-bundle-analyzer stats.json
```
