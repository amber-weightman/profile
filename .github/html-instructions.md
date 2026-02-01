# HTML Best Practices - 2026

## HTML5 Semantic Structure
Use semantic HTML elements to convey meaning and improve accessibility:

```html
<header>   - Site header, navigation
<nav>      - Navigation links
<main>     - Primary content (one per page)
<section>  - Thematic grouping of content
<article>  - Self-contained content
<aside>    - Tangentially related content
<footer>   - Site footer, copyright, links
```

## Document Structure Template
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="[Clear, concise description 150-160 chars]">
    <meta name="author" content="Amber Weightman">
    
    <!-- Open Graph / Social Media -->
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://amberweightman.com/">
    <meta property="og:title" content="[Page Title]">
    <meta property="og:description" content="[Description]">
    <meta property="og:image" content="[Image URL]">
    
    <!-- Twitter Card -->
    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:title" content="[Page Title]">
    <meta name="twitter:description" content="[Description]">
    <meta name="twitter:image" content="[Image URL]">
    
    <!-- Favicon -->
    <link rel="icon" type="image/svg+xml" href="/favicon.svg">
    <link rel="icon" type="image/png" href="/favicon.png">
    
    <title>[Page Title] | Amber Weightman</title>
    
    <!-- Preconnect to external domains -->
    <link rel="preconnect" href="https://fonts.googleapis.com" crossorigin>
    
    <style>
        /* Critical CSS inline for performance */
    </style>
</head>
<body>
    <!-- Content here -->
</body>
</html>
```

## Accessibility Best Practices

### Heading Hierarchy
- Use one `<h1>` per page for the main heading
- Follow logical hierarchy: h1 → h2 → h3 (no skipping levels)
- Headings should describe the content that follows

### Links and Buttons
```html
<!-- External links -->
<a href="https://example.com" target="_blank" rel="noopener noreferrer">
    Link Text
</a>

<!-- Links with icons - always include text or aria-label -->
<a href="https://github.com/username" aria-label="GitHub Profile">
    <svg><!-- icon --></svg>
</a>

<!-- Skip to main content link for keyboard users -->
<a href="#main" class="skip-link">Skip to main content</a>
```

### Images
```html
<!-- Always include alt text -->
<img src="image.jpg" alt="Descriptive text of image content" width="800" height="600">

<!-- Decorative images use empty alt -->
<img src="decoration.svg" alt="" role="presentation">

<!-- Use loading="lazy" for below-fold images -->
<img src="image.jpg" alt="Description" loading="lazy">
```

### Forms (if needed)
```html
<form>
    <label for="email">Email Address</label>
    <input 
        type="email" 
        id="email" 
        name="email" 
        required 
        aria-describedby="email-help"
        autocomplete="email"
    >
    <small id="email-help">We'll never share your email.</small>
</form>
```

## Performance Optimization

### Resource Hints
```html
<!-- DNS prefetch for external domains -->
<link rel="dns-prefetch" href="https://fonts.googleapis.com">

<!-- Preconnect for critical external resources -->
<link rel="preconnect" href="https://fonts.googleapis.com" crossorigin>

<!-- Preload critical resources -->
<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>
```

### Responsive Images
```html
<!-- Use srcset for different resolutions -->
<img 
    src="image-800.jpg" 
    srcset="image-400.jpg 400w, image-800.jpg 800w, image-1200.jpg 1200w"
    sizes="(max-width: 600px) 400px, (max-width: 1200px) 800px, 1200px"
    alt="Description"
>

<!-- Use picture for art direction -->
<picture>
    <source media="(max-width: 600px)" srcset="mobile.jpg">
    <source media="(max-width: 1200px)" srcset="tablet.jpg">
    <img src="desktop.jpg" alt="Description">
</picture>
```

## Modern HTML Features

### Native Dialog
```html
<dialog id="my-dialog">
    <h2>Dialog Title</h2>
    <p>Dialog content</p>
    <button onclick="this.closest('dialog').close()">Close</button>
</dialog>
```

### Details/Summary (Accordion)
```html
<details>
    <summary>Click to expand</summary>
    <p>Hidden content revealed when expanded.</p>
</details>
```

## SEO Essentials
- Use descriptive, unique `<title>` tags (50-60 characters)
- Include meta description (150-160 characters)
- Use semantic HTML for better content understanding
- Include structured data (Schema.org) when relevant
- Ensure proper URL structure
- Use descriptive link text (avoid "click here")

## Code Quality
- Validate HTML with W3C validator
- Use lowercase for element names and attributes
- Always quote attribute values
- Close all elements properly (even void elements like `<img />`)
- Indent consistently (2 or 4 spaces)
- Use meaningful IDs and class names
- Avoid inline styles (except critical CSS)
- Keep nesting logical and not too deep

## Security
- Always use `rel="noopener noreferrer"` for `target="_blank"` links
- Sanitize any user input (if applicable)
- Use HTTPS for all resources
- Set proper Content Security Policy headers (via GitHub Pages config if possible)

## Social Media Integration
Include proper meta tags for link previews:
- Open Graph (Facebook, LinkedIn)
- Twitter Cards
- Provide high-quality preview images (1200x630px recommended)
- Use absolute URLs for images
