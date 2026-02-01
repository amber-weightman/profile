# CSS Best Practices - 2026

## Modern CSS Architecture

### CSS Custom Properties (Variables)
Define design tokens using CSS custom properties for maintainability:

```css
:root {
    /* Colors */
    --color-primary: #2563eb;
    --color-secondary: #7c3aed;
    --color-text: #1f2937;
    --color-text-light: #6b7280;
    --color-background: #ffffff;
    --color-surface: #f9fafb;
    
    /* Spacing Scale (based on 8px grid) */
    --space-xs: 0.5rem;   /* 8px */
    --space-sm: 1rem;     /* 16px */
    --space-md: 1.5rem;   /* 24px */
    --space-lg: 2rem;     /* 32px */
    --space-xl: 3rem;     /* 48px */
    --space-2xl: 4rem;    /* 64px */
    
    /* Typography */
    --font-sans: system-ui, -apple-system, 'Segoe UI', sans-serif;
    --font-mono: 'SF Mono', Monaco, 'Cascadia Code', monospace;
    
    --text-xs: 0.75rem;   /* 12px */
    --text-sm: 0.875rem;  /* 14px */
    --text-base: 1rem;    /* 16px */
    --text-lg: 1.125rem;  /* 18px */
    --text-xl: 1.25rem;   /* 20px */
    --text-2xl: 1.5rem;   /* 24px */
    --text-3xl: 1.875rem; /* 30px */
    --text-4xl: 2.25rem;  /* 36px */
    
    /* Line Heights */
    --leading-tight: 1.25;
    --leading-normal: 1.5;
    --leading-relaxed: 1.75;
    
    /* Border Radius */
    --radius-sm: 0.25rem;
    --radius-md: 0.5rem;
    --radius-lg: 1rem;
    --radius-full: 9999px;
    
    /* Shadows */
    --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
    --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1);
    --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1);
    
    /* Transitions */
    --transition-fast: 150ms ease;
    --transition-base: 250ms ease;
    --transition-slow: 350ms ease;
    
    /* Breakpoints (for container queries or custom media) */
    --bp-sm: 640px;
    --bp-md: 768px;
    --bp-lg: 1024px;
    --bp-xl: 1280px;
}

/* Dark mode support */
@media (prefers-color-scheme: dark) {
    :root {
        --color-text: #f9fafb;
        --color-text-light: #d1d5db;
        --color-background: #111827;
        --color-surface: #1f2937;
    }
}
```

## CSS Reset / Normalization

### Modern CSS Reset
```css
/* Box sizing reset */
*,
*::before,
*::after {
    box-sizing: border-box;
}

/* Remove default margins */
* {
    margin: 0;
}

/* Improve text rendering */
html {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

/* Set core body defaults */
body {
    min-height: 100vh;
    line-height: var(--leading-normal);
    font-family: var(--font-sans);
    color: var(--color-text);
    background-color: var(--color-background);
}

/* Make images easier to work with */
img,
picture,
svg {
    max-width: 100%;
    height: auto;
    display: block;
}

/* Inherit fonts for form controls */
input,
button,
textarea,
select {
    font: inherit;
}

/* Remove animations for people who prefer reduced motion */
@media (prefers-reduced-motion: reduce) {
    *,
    *::before,
    *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
    }
}
```

## Layout Patterns

### Flexbox Patterns
```css
/* Center content */
.flex-center {
    display: flex;
    justify-content: center;
    align-items: center;
}

/* Space between items */
.flex-between {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

/* Stack with gap */
.flex-stack {
    display: flex;
    flex-direction: column;
    gap: var(--space-md);
}
```

### CSS Grid Patterns
```css
/* Responsive grid - auto-fit columns */
.grid-auto {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(min(250px, 100%), 1fr));
    gap: var(--space-md);
}

/* 12-column grid system */
.grid-12 {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: var(--space-md);
}

/* Center content with max width */
.container {
    width: min(100% - var(--space-lg), 1200px);
    margin-inline: auto;
}
```

## Responsive Design

### Mobile-First Approach
```css
/* Base styles (mobile) */
.element {
    font-size: var(--text-base);
    padding: var(--space-sm);
}

/* Tablet and up */
@media (min-width: 768px) {
    .element {
        font-size: var(--text-lg);
        padding: var(--space-md);
    }
}

/* Desktop and up */
@media (min-width: 1024px) {
    .element {
        font-size: var(--text-xl);
        padding: var(--space-lg);
    }
}
```

### Container Queries (Modern)
```css
.card-container {
    container-type: inline-size;
}

.card {
    padding: var(--space-sm);
}

@container (min-width: 400px) {
    .card {
        padding: var(--space-md);
        display: grid;
        grid-template-columns: auto 1fr;
    }
}
```

## Modern CSS Features

### Logical Properties
Use logical properties for better internationalization:
```css
/* Instead of margin-left/right */
.element {
    margin-inline: var(--space-md);
    padding-block: var(--space-sm);
    border-inline-start: 2px solid var(--color-primary);
}
```

### Clamp for Fluid Typography
```css
h1 {
    /* min, preferred (fluid), max */
    font-size: clamp(2rem, 5vw + 1rem, 4rem);
}
```

### Modern Color Functions
```css
.element {
    /* Relative colors */
    background-color: rgb(from var(--color-primary) r g b / 0.1);
    
    /* Color-mix */
    border-color: color-mix(in srgb, var(--color-primary) 50%, white);
}
```

### CSS Nesting (Modern)
```css
.card {
    padding: var(--space-md);
    border-radius: var(--radius-md);
    
    & h2 {
        margin-block-end: var(--space-sm);
    }
    
    & a {
        color: var(--color-primary);
        
        &:hover {
            text-decoration: underline;
        }
    }
}
```

## Accessibility

### Focus Styles
```css
/* Remove default outline and add custom */
*:focus {
    outline: none;
}

*:focus-visible {
    outline: 2px solid var(--color-primary);
    outline-offset: 2px;
    border-radius: var(--radius-sm);
}

/* Skip to main content link */
.skip-link {
    position: absolute;
    top: -100%;
    left: 0;
    padding: var(--space-sm);
    background: var(--color-primary);
    color: white;
    text-decoration: none;
    
    &:focus {
        top: 0;
    }
}
```

### High Contrast Mode Support
```css
@media (prefers-contrast: high) {
    :root {
        --color-primary: #0000ff;
        --color-text: #000000;
    }
}
```

## Performance Optimization

### Content-Visibility
```css
/* Improve rendering performance for off-screen content */
.below-fold-section {
    content-visibility: auto;
    contain-intrinsic-size: 0 500px;
}
```

### Will-Change (Use Sparingly)
```css
/* Only for animations you know will happen */
.animated-element:hover {
    will-change: transform;
}

.animated-element {
    transition: transform var(--transition-base);
}

.animated-element:not(:hover) {
    will-change: auto;
}
```

## Animation Best Practices

### Performant Animations
Only animate opacity and transform for best performance:
```css
.fade-in {
    opacity: 0;
    animation: fadeIn var(--transition-base) forwards;
}

@keyframes fadeIn {
    to {
        opacity: 1;
    }
}

.slide-up {
    transform: translateY(20px);
    transition: transform var(--transition-base);
}

.slide-up.active {
    transform: translateY(0);
}
```

### Respect User Preferences
```css
@media (prefers-reduced-motion: reduce) {
    *,
    *::before,
    *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
    }
}
```

## Utility Classes Pattern

### Common Utilities
```css
/* Visually hidden but accessible to screen readers */
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border-width: 0;
}

/* Text utilities */
.text-center { text-align: center; }
.text-balance { text-wrap: balance; }
.text-pretty { text-wrap: pretty; }

/* Display utilities */
.flex { display: flex; }
.grid { display: grid; }
.hidden { display: none; }
```

## Code Organization

### File Structure
```
styles/
├── reset.css          - CSS reset/normalize
├── variables.css      - CSS custom properties
├── layout.css         - Grid, flexbox, containers
├── components.css     - Reusable components
├── utilities.css      - Utility classes
└── main.css          - Imports and overrides
```

### Naming Conventions (BEM)
```css
/* Block */
.card { }

/* Element */
.card__title { }
.card__content { }

/* Modifier */
.card--featured { }
.card__title--large { }
```

## Browser Support

### Feature Detection with @supports
```css
.element {
    /* Fallback */
    display: flex;
}

@supports (display: grid) {
    .element {
        display: grid;
    }
}
```

## Print Styles
```css
@media print {
    * {
        background: transparent !important;
        color: black !important;
        box-shadow: none !important;
        text-shadow: none !important;
    }
    
    a[href]::after {
        content: " (" attr(href) ")";
    }
    
    @page {
        margin: 2cm;
    }
}
```

## Code Quality
- Validate CSS with W3C CSS Validator
- Use consistent formatting (Prettier recommended)
- Avoid !important unless absolutely necessary
- Keep specificity low
- Use meaningful class names
- Comment complex calculations or browser hacks
- Alphabetize properties within rules (optional but consistent)
- Remove unused CSS
- Minimize nesting depth (max 3-4 levels)
