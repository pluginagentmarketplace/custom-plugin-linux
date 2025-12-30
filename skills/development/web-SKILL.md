---
name: web-fundamentals
description: Web development fundamentals - HTML, CSS, JavaScript, responsive design
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [build, style, optimize, debug, responsive] }
    focus: { type: string, enum: [html, css, javascript, all] }
  required: [task]

output_schema:
  type: object
  properties:
    code: { type: string }
    best_practices: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 30000
---

# Web Fundamentals Skill

## PURPOSE
Core web development with HTML, CSS, and JavaScript.

## CORE COMPETENCIES
```
HTML5:
├── Semantic markup
├── Forms & validation
├── Accessibility (ARIA)
└── SEO best practices

CSS:
├── Flexbox & Grid
├── Responsive design
├── CSS Variables
├── Animations
└── Tailwind/modern frameworks

JavaScript:
├── ES2024+ features
├── DOM manipulation
├── Event handling
├── Async/await
└── Modules
```

## CODE PATTERNS

### Semantic HTML
```html
<article>
  <header>
    <h1>Article Title</h1>
    <time datetime="2024-01-15">January 15, 2024</time>
  </header>
  <main>
    <p>Content here...</p>
  </main>
  <footer>
    <nav aria-label="Article navigation">
      <a href="/prev">Previous</a>
      <a href="/next">Next</a>
    </nav>
  </footer>
</article>
```

### Responsive CSS Grid
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1rem;
}

@media (max-width: 768px) {
  .grid {
    grid-template-columns: 1fr;
  }
}
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Layout broken | Box model | Check margin, padding, border-box |
| Not responsive | Fixed widths | Use relative units, media queries |
| Accessibility | Missing ARIA | Add labels, roles, focus states |
