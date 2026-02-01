# GitHub Copilot Instructions - amberweightman.com

## Project Overview
This is a simple, single-page portfolio website hosted on GitHub Pages at amberweightman.com.

**Purpose:**
- Index to official online socials and publications representing personal brand
- Domain splash page
- Minimal technical showcase using HTML/CSS only (no JavaScript frameworks)

**Tech Stack:**
- Pure HTML5 (semantic markup)
- Pure CSS3 (modern features, CSS Grid, Flexbox)
- No build tools or frameworks required
- Optimized for performance and accessibility

## Design Principles
- **Simplicity**: Clean, minimal design that loads fast
- **Accessibility**: WCAG 2.2 Level AA compliant
- **Responsiveness**: Mobile-first, works on all devices
- **Performance**: Minimal dependencies, optimized assets
- **Modern**: Use latest HTML/CSS features with graceful degradation

## Code Guidelines
1. Use semantic HTML5 elements appropriately
2. Implement responsive design with CSS Grid and Flexbox
3. Follow BEM or logical CSS naming conventions
4. Ensure full keyboard navigation support
5. Include proper meta tags for SEO and social sharing
6. Use modern CSS features (custom properties, container queries where appropriate)
7. Optimize for Core Web Vitals (LCP, FID, CLS)
8. Include proper alt text for images
9. Use relative units (rem, em) for scalability
10. Ensure proper color contrast ratios

## HTML Formatting
- Keep lines under 80 characters when possible
- Break long HTML elements across multiple lines when they exceed line length
- Use one attribute per line for elements with many attributes or when line length requires it
- Keep simple elements on a single line when concise
- Indent nested elements consistently (2 spaces recommended)
- Examples:
  ```html
  <!-- Simple, short element - keep on one line -->
  <meta property="og:type" content="website" />
  
  <!-- Complex element with many attributes - break to multiple lines -->
  <a
    href="https://example.com"
    target="_blank"
    rel="noopener noreferrer"
    aria-label="Example link that has a long description">
    Link Text
  </a>
  ```

## File Organization
- `index.html` - Main HTML file
- CSS should be organized logically (reset, variables, layout, components, utilities)
- Keep inline CSS minimal, prefer external stylesheets or `<style>` blocks for small projects

## Browser Support
- Modern evergreen browsers (Chrome, Firefox, Safari, Edge)
- Graceful degradation for older browsers
- Progressive enhancement approach

## Performance Targets
- First Contentful Paint < 1.5s
- Largest Contentful Paint < 2.5s
- Cumulative Layout Shift < 0.1
- Total page weight < 100KB (excluding images)

## Accessibility Requirements
- Semantic HTML structure
- Proper heading hierarchy (h1-h6)
- ARIA labels where appropriate
- Keyboard navigation support
- Screen reader friendly
- Sufficient color contrast (4.5:1 for normal text, 3:1 for large text)
- Focus indicators visible and clear

## Social Links Best Practices
- Use `rel="noopener noreferrer"` for external links
- Include aria-labels for icon-only links
- Ensure hover and focus states are clear
- Consider using SVG icons for crisp rendering

## Deployment
- Hosted on GitHub Pages
- Custom domain: amberweightman.com
- Ensure proper CNAME configuration
- HTTPS enabled by default
