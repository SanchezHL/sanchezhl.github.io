# AGENTS.md - Coding Guidelines for sanchezhl.github.io

This is a static personal website repository containing HTML, CSS, and vanilla JavaScript files. No build system or framework is currently configured.

## 1. Build, Lint, and Test Commands

### HTML Validation

```bash
# Validate a single HTML file using W3C Validator
npx html-validate index.html

# Validate all HTML files
find . -name "*.html" -exec npx html-validate {} \;
```

### CSS Linting

```bash
# Lint CSS files with Stylelint
npx stylelint "**/*.css"

# Fix automatically fixable issues
npx stylelint "**/*.css" --fix
```

### JavaScript Linting

```bash
# Lint JavaScript files with ESLint
npx eslint "**/*.js"

# Fix automatically fixable issues
npx eslint "**/*.js" --fix

# Lint a single JavaScript file
npx eslint script.js
```

### Browser Testing

```bash
# Test HTML files render correctly (basic check)
# Open files in browser and verify:
# - Responsive design (mobile/desktop)
# - Navigation links work
# - No console errors
```

### Initialize Project Tools (First Time Setup)

```bash
# Initialize npm and install linting tools
npm init -y
npm install --save-dev eslint stylelint html-validate

# Initialize configurations
npx eslint --init
npx stylelint --init
```

## 2. Code Style Guidelines

### HTML Conventions

- Use semantic elements (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`)
- Always include `lang` attribute on `<html>`: `<html lang="en">`
- Include viewport meta tag for responsive design
- Use kebab-case for IDs and classes (e.g., `nav-links`, `menu-toggle`)
- Place `<script>` tags before `</body>` to avoid render blocking
- Use lowercase for all HTML tags and attributes

### CSS Conventions

- Use meaningful class names that describe content/function, not appearance
- Follow BEM-lite naming: `block__element--modifier` pattern
- Organize properties alphabetically within rules
- Use CSS custom properties (variables) for colors: `--primary-color: #f5c6e0;`
- Keep selectors short and specific
- Use flexbox for layout (current pattern used in `nav` and `.nav-links`)
- Group related styles logically: layout, typography, colors, effects

### JavaScript Conventions

- Use `const` by default, `let` only when reassignment is necessary
- Use camelCase for variables and function names: `menuToggle`, `navLinks`
- Use descriptive names that indicate purpose: `DOMContentLoaded` over `ready`
- Add null checks before accessing DOM elements:
  ```javascript
  const menuToggle = document.getElementById("menuToggle");
  if (menuToggle) {
    menuToggle.addEventListener("click", handleMenuToggle);
  }
  ```
- Use arrow functions for simple callbacks
- Keep functions focused and under 30 lines when possible

### Naming Conventions

| Type                  | Convention       | Example                    |
| --------------------- | ---------------- | -------------------------- |
| HTML IDs/Classes      | kebab-case       | `nav-links`, `menu-toggle` |
| JavaScript variables  | camelCase        | `menuToggle`, `navLinks`   |
| JavaScript constants  | UPPER_SNAKE_CASE | `MAX_RETRIES`              |
| CSS custom properties | kebab-case       | `--primary-color`          |
| File names            | kebab-case       | `script.js`, `styles.css`  |

### Error Handling

- Always check if DOM elements exist before manipulating them
- Wrap DOM queries in conditional checks:
  ```javascript
  const navLinks = document.getElementById("navLinks");
  if (navLinks) {
    navLinks.classList.add("loaded");
  }
  ```
- Add console.error for unexpected states during development
- Ensure navigation links have valid href attributes

### Imports and Dependencies

- This project uses vanilla JavaScript with no external dependencies
- Scripts are loaded directly via `<script>` tags (see index.html)
- If adding libraries, use CDN links in `<head>` or `<body>`
- Avoid bundlers unless complexity increases significantly

### Formatting

- Indent with 2 spaces (matching existing codebase)
- Use double quotes for strings: `"navLinks"`
- Add trailing commas in multi-line objects/arrays
- Limit line length to 100 characters

### Accessibility

- Use descriptive link text (avoid "click here")
- Include alt text for images (when added)
- Ensure color contrast meets WCAG AA standards
- Use semantic HTML for screen readers

## File Structure

```
sanchezhl.github.io/
├── index.html          (main landing page)
├── blog.html           (blog listing)
├── thisblog.html       (blog post page)
├── projects.html       (projects showcase)
├── script.js           (JavaScript utilities)
├── styles.css          (main stylesheet)
├── assets/             (images, icons, static assets)
└── AGENTS.md           (this file)
```

## Browser Compatibility

- Target modern browsers (Chrome, Firefox, Safari, Edge)
- Include vendor prefixes for edge cases (already present in styles.css for -ms-overflow-style)
- Test responsive behavior on mobile and desktop viewports
