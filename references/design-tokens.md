# Design Tokens Reference

Consistent design tokens for modern, professional websites.

## Spacing Scale

```css
--space-1: 0.25rem;   /* 4px */
--space-2: 0.5rem;    /* 8px */
--space-3: 0.75rem;   /* 12px */
--space-4: 1rem;      /* 16px */
--space-5: 1.5rem;    /* 24px */
--space-6: 2rem;      /* 32px */
--space-8: 3rem;      /* 48px */
--space-10: 4rem;     /* 64px */
--space-12: 6rem;     /* 96px */
--space-16: 8rem;     /* 128px */
```

## Typography Scale

```css
--text-xs: 0.75rem;    /* 12px */
--text-sm: 0.875rem;   /* 14px */
--text-base: 1rem;     /* 16px */
--text-lg: 1.125rem;   /* 18px */
--text-xl: 1.25rem;    /* 20px */
--text-2xl: 1.5rem;    /* 24px */
--text-3xl: 1.875rem;  /* 30px */
--text-4xl: 2.25rem;   /* 36px */
--text-5xl: 3rem;      /* 48px */
--text-6xl: 3.75rem;   /* 60px */
```

### Line Heights

```css
--leading-none: 1;
--leading-tight: 1.25;
--leading-snug: 1.375;
--leading-normal: 1.5;
--leading-relaxed: 1.625;
--leading-loose: 2;
```

### Font Weights

```css
--font-light: 300;
--font-normal: 400;
--font-medium: 500;
--font-semibold: 600;
--font-bold: 700;
```

## Color System

### Neutral Palette (Light Mode)

```css
--background: 0 0% 100%;        /* #ffffff */
--foreground: 240 10% 3.9%;     /* #0a0a0b */
--muted: 240 4.8% 95.9%;        /* #f4f4f5 */
--muted-foreground: 240 3.8% 46.1%;  /* #71717a */
--border: 240 5.9% 90%;         /* #e4e4e7 */
--input: 240 5.9% 90%;          /* #e4e4e7 */
--card: 0 0% 100%;              /* #ffffff */
--card-foreground: 240 10% 3.9%;
```

### Neutral Palette (Dark Mode)

```css
--background: 240 10% 3.9%;     /* #0a0a0b */
--foreground: 0 0% 98%;         /* #fafafa */
--muted: 240 3.7% 15.9%;        /* #27272a */
--muted-foreground: 240 5% 64.9%;  /* #a1a1aa */
--border: 240 3.7% 15.9%;       /* #27272a */
--input: 240 3.7% 15.9%;        /* #27272a */
--card: 240 10% 3.9%;           /* #0a0a0b */
--card-foreground: 0 0% 98%;
```

### Semantic Colors

```css
/* Primary - Brand color */
--primary: 221.2 83.2% 53.3%;     /* #3b82f6 */
--primary-foreground: 210 40% 98%;

/* Secondary - Subtle actions */
--secondary: 210 40% 96.1%;
--secondary-foreground: 222.2 47.4% 11.2%;

/* Accent - Highlights */
--accent: 210 40% 96.1%;
--accent-foreground: 222.2 47.4% 11.2%;

/* Destructive - Errors, delete */
--destructive: 0 84.2% 60.2%;     /* #ef4444 */
--destructive-foreground: 210 40% 98%;

/* Success */
--success: 142.1 76.2% 36.3%;     /* #22c55e */
--success-foreground: 355.7 100% 97.3%;

/* Warning */
--warning: 45.4 93.4% 47.5%;      /* #eab308 */
--warning-foreground: 26 83.3% 14.1%;
```

## Border Radius

```css
--radius-sm: 0.25rem;   /* 4px */
--radius: 0.5rem;       /* 8px */
--radius-md: 0.75rem;   /* 12px */
--radius-lg: 1rem;      /* 16px */
--radius-xl: 1.5rem;    /* 24px */
--radius-full: 9999px;  /* Pill shape */
```

## Shadows

```css
--shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
--shadow: 0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1);
--shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
--shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
--shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
```

## Transitions

```css
--transition-fast: 150ms cubic-bezier(0.4, 0, 0.2, 1);
--transition-base: 200ms cubic-bezier(0.4, 0, 0.2, 1);
--transition-slow: 300ms cubic-bezier(0.4, 0, 0.2, 1);
--transition-slower: 500ms cubic-bezier(0.4, 0, 0.2, 1);
```

## Z-Index Scale

```css
--z-dropdown: 1000;
--z-sticky: 1020;
--z-fixed: 1030;
--z-modal-backdrop: 1040;
--z-modal: 1050;
--z-popover: 1060;
--z-tooltip: 1070;
```

## Breakpoints

```css
/* Mobile first approach */
--sm: 640px;   /* Small tablets */
--md: 768px;   /* Tablets */
--lg: 1024px;  /* Laptops */
--xl: 1280px;  /* Desktops */
--2xl: 1536px; /* Large screens */
```

## Container Widths

```css
--container-sm: 640px;
--container-md: 768px;
--container-lg: 1024px;
--container-xl: 1280px;
--container-2xl: 1400px;
```
