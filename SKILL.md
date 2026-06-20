---
name: homepage-improver
description: |
  Analyze and improve existing homepages and landing pages for UI/UX, performance, accessibility, and SEO.
  Use when: (1) User wants to improve/optimize an existing website, (2) User asks for homepage/landing page review,
  (3) User wants UI/UX analysis, (4) User asks about performance or accessibility improvements,
  (5) User mentions "homepage improvement", "landing page optimization", "website makeover",
  (6) User provides a URL or HTML/CSS code for review, (7) User asks to make a page more modern or responsive.
---

# Homepage Improver

Systematically analyze and improve existing homepages/landing pages through a structured workflow.

## Workflow Overview

```
1. Capture Current State
   └─> Screenshot or code analysis

2. Multi-dimensional Analysis
   ├─> UI/UX Analysis
   ├─> Performance Audit
   ├─> Accessibility Check
   └─> SEO Review

3. Prioritized Improvements
   └─> Quick wins → Medium effort → Major refactors

4. Iterative Implementation
   └─> Implement → Preview → Refine
```

## Step 1: Capture Current State

### For Live URLs
Use WebFetch to analyze the page structure:
```
WebFetch: [URL]
Prompt: "Extract the complete HTML structure, CSS classes used, and key UI components"
```

### For Local Files
Read the HTML/CSS/JS files directly using Read tool.

### For Screenshots
If user provides a screenshot, analyze visually and identify:
- Layout structure (header, hero, features, footer, etc.)
- Color scheme and typography
- Component patterns
- Responsive breakpoints

## Step 2: Multi-dimensional Analysis

Run all four analyses in parallel for efficiency.

### 2.1 UI/UX Analysis

Check against modern standards:

| Category | Check Items |
|----------|-------------|
| **Layout** | Visual hierarchy, whitespace, grid consistency, content flow |
| **Typography** | Font pairing, size scale, line height, readability |
| **Colors** | Contrast ratios, brand consistency, emotional impact |
| **Components** | Button styles, card designs, form usability, navigation |
| **Interactions** | Hover states, animations, micro-interactions, loading states |
| **Mobile** | Touch targets (min 44px), thumb zones, responsive breakpoints |

### 2.2 Performance Audit

Identify performance bottlenecks:

| Issue | Solution Pattern |
|-------|------------------|
| Large images | Suggest WebP/AVIF, lazy loading, responsive images |
| Render blocking | Defer non-critical CSS/JS, inline critical CSS |
| Too many requests | Bundle assets, use sprites, reduce dependencies |
| No caching | Add cache headers, service worker suggestions |
| Heavy fonts | Subset fonts, use system font stack, font-display: swap |

### 2.3 Accessibility Check (WCAG 2.1)

| Level | Requirements |
|-------|--------------|
| **A** | Alt text, keyboard navigation, skip links, form labels |
| **AA** | Color contrast 4.5:1, focus indicators, error identification |
| **AAA** | Enhanced contrast 7:1, sign language, extended audio |

### 2.4 SEO Review

| Element | Best Practice |
|---------|---------------|
| Meta tags | Title (50-60 chars), description (150-160 chars) |
| Headings | Single H1, logical hierarchy |
| Images | Alt text, descriptive filenames |
| Structure | Schema.org markup, semantic HTML |
| Speed | Core Web Vitals (LCP, FID, CLS) |

## Step 3: Prioritized Improvement Plan

Categorize findings into actionable tiers:

### Quick Wins (< 30 min each)
- Fix contrast issues
- Add missing alt text
- Optimize meta tags
- Fix heading hierarchy
- Add missing ARIA labels

### Medium Effort (1-2 hours each)
- Implement responsive improvements
- Refactor component styling
- Add loading states
- Improve form validation UX
- Optimize images

### Major Refactors (> 2 hours)
- Redesign navigation structure
- Implement design system
- Add dark mode support
- Full accessibility overhaul
- Performance architecture changes

## Step 4: Implementation

### Modern Tech Stack Recommendations

```
CSS Framework: Tailwind CSS (utility-first, responsive)
Component Library: Shadcn/UI, Radix UI (accessible primitives)
Icons: Lucide, Heroicons (consistent, optimized)
Animations: Framer Motion, CSS transitions
```

### Implementation Pattern

1. **Start with structure**: Fix semantic HTML first
2. **Apply styling**: Use consistent design tokens
3. **Add interactions**: Progressive enhancement
4. **Test responsiveness**: Mobile-first approach
5. **Validate**: Run accessibility/performance checks

### Code Quality Checklist

- [ ] Semantic HTML5 elements
- [ ] BEM or utility-first CSS naming
- [ ] CSS custom properties for theming
- [ ] Responsive images with srcset
- [ ] Keyboard navigation support
- [ ] Screen reader tested
- [ ] Reduced motion support

## Output Format

Present findings in this structure:

```markdown
## Current State Summary
[Screenshot analysis or code overview]

## Analysis Results

### UI/UX Score: X/10
- Strengths: ...
- Issues: ...

### Performance Score: X/10
- Strengths: ...
- Issues: ...

### Accessibility Score: X/10 (WCAG Level)
- Strengths: ...
- Issues: ...

### SEO Score: X/10
- Strengths: ...
- Issues: ...

## Improvement Plan

### Quick Wins
1. [Issue] → [Fix]
2. ...

### Medium Effort
1. [Issue] → [Approach]
2. ...

### Major Refactors
1. [Issue] → [Strategy]
2. ...

## Recommended Next Step
[Most impactful single improvement to start with]
```

## Common Patterns

### Hero Section Improvement
```html
<!-- Before: Generic hero -->
<div class="hero">
  <h1>Welcome</h1>
  <p>Description</p>
  <button>Click</button>
</div>

<!-- After: Engaging hero -->
<section class="relative min-h-[80vh] flex items-center">
  <div class="container mx-auto px-4">
    <h1 class="text-4xl md:text-6xl font-bold tracking-tight">
      Clear Value Proposition
    </h1>
    <p class="mt-6 text-xl text-muted-foreground max-w-2xl">
      Compelling subheadline that explains the benefit
    </p>
    <div class="mt-8 flex gap-4">
      <button class="px-8 py-3 bg-primary text-primary-foreground rounded-lg
                     hover:bg-primary/90 transition-colors">
        Primary CTA
      </button>
      <button class="px-8 py-3 border border-input rounded-lg
                     hover:bg-accent transition-colors">
        Secondary CTA
      </button>
    </div>
  </div>
</section>
```

### Responsive Navigation
```html
<nav class="sticky top-0 z-50 bg-background/80 backdrop-blur-sm border-b">
  <div class="container mx-auto px-4 h-16 flex items-center justify-between">
    <a href="/" class="font-bold text-xl">Logo</a>

    <!-- Desktop nav -->
    <ul class="hidden md:flex gap-8">
      <li><a href="#" class="hover:text-primary transition-colors">Link</a></li>
    </ul>

    <!-- Mobile menu button -->
    <button class="md:hidden p-2" aria-label="Toggle menu">
      <svg>...</svg>
    </button>
  </div>
</nav>
```

### Accessible Card Component
```html
<article class="group rounded-xl border bg-card p-6
                hover:shadow-lg transition-shadow">
  <img src="..." alt="Descriptive alt text"
       class="rounded-lg aspect-video object-cover" loading="lazy">
  <h3 class="mt-4 text-xl font-semibold group-hover:text-primary transition-colors">
    Card Title
  </h3>
  <p class="mt-2 text-muted-foreground">
    Card description text...
  </p>
  <a href="#" class="mt-4 inline-flex items-center text-primary hover:underline">
    Learn more
    <svg class="ml-1 w-4 h-4" aria-hidden="true">...</svg>
  </a>
</article>
```

## Reference Files

- See `references/design-tokens.md` for consistent spacing, colors, typography scales
- See `references/accessibility-checklist.md` for detailed WCAG compliance checks
- See `references/performance-budget.md` for Core Web Vitals targets
