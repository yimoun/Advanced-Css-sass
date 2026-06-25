# Learning Notes — Natours Project

## Overview
This document captures what I learned while building the Natours project as part of the Advanced CSS & Sass course. It is organized by section and highlights the core concepts, best practices, and workflow decisions that helped me grow as a frontend developer.

## Section 2: Core CSS Skills
- Learned advanced layout techniques such as `clip-path`.
- Mastered centering any element using `transform`, `top`, and `left`.
- Built animations using `@keyframes` and the `animation` property.
- Used pseudo-classes and pseudo-elements like `::after` to add decorative content.
- Created interactive hover states with `transition`.
- Applied these techniques in the `<header>` of the final page.

> Whenever I needed deeper understanding, I checked the official documentation.

## Section 3: Frontend Foundations
### The three pillars of strong frontend code
1. Responsive design
   - fluid layouts
   - media queries
   - responsive images
   - correct use of units
   - desktop-first vs mobile-first approach
2. Maintainable, scalable CSS
   - clean and easy-to-read code
   - reusable components
   - good file organization
   - meaningful class naming
   - structured HTML
3. Performance
   - fewer HTTP requests
   - less code
   - compress assets
   - use a CSS preprocessor (Sass)
   - optimize and compress images

### How CSS works in the browser
- Browser loads HTML and builds the DOM.
- External CSS is loaded and parsed.
- The cascade resolves conflicts between styles.
- The browser constructs the CSSOM (CSS Object Model).
- DOM and CSSOM combine into the render tree.
- The render tree is used to paint the final page.

### Cascade and specificity
- `!important` increases specificity but usually signals the need to refactor.
- The cascade resolves conflicts based on source order, importance, and specificity.
- Specificity order:
  1. inline styles
  2. IDs
  3. classes, pseudo-classes, attributes
  4. elements and pseudo-elements
- Specificity is calculated category by category, not as a single number.
- To fix a selector that is not applying, increase specificity only where necessary.

### CSS value processing
CSS values go through these steps:
1. Declared value
2. Cascaded value
3. Specified value
4. Computed value
5. Used value
6. Actual value

### Units review
- `%` for fonts references parent computed font-size; for lengths it references parent width.
- `em` for font sizes references parent computed font-size; for other lengths it references the current element’s computed font-size.
- `rem` is always relative to the root font-size, usually `16px`.
- `vh` and `vw` are relative to viewport height and width.

### Inheritance and keywords
- `inherit` forces a property to inherit from its parent.
- `initial` resets a property to its initial value.
- Text-related properties such as `font-family`, `font-size`, and `color` inherit by default.

## Section 4: Sass and NPM
### What Sass brings
- Sass is a CSS preprocessor that adds power and elegance to vanilla CSS.
- It solves common CSS problems and adds features that plain CSS does not provide.

### Key Sass features learned
- Variables for reusable values: colors, spacing, font sizes.
- Nesting to organize selectors hierarchically.
- Operators for calculations inside stylesheets.
- Partials to split code into multiple files.
- Mixins for reusable rules.
- Functions for value generation.
- `@extend` for shared declarations.
- Control directives for conditionals and loops.

### Sass syntax
- Two syntaxes exist: the indented Sass syntax and the SCSS syntax.
- This project uses SCSS because it preserves the familiar CSS structure.

### Workflow
- Install Sass locally with npm.
- Use `npm run compile:sass` to compile `sass/main.scss` to `css/style.css`.
- Use a local development server for live preview.

## Section 5: Natours project learnings
### Responsive design principles
- Fluid layouts should adapt to viewport width using `%`, `vh`, and `vw`.
- Prefer `max-width` instead of fixed `width` for responsive containers.
- Use `rem` for scalable typography and spacing.
- Make images flexible with `width: 100%` and `max-width`.
- Use media queries for layout changes at breakpoints.

### Layout techniques
- Float-based layouts remain useful for learning and legacy behavior.
- Flexbox is ideal for one-dimensional component layouts.
- CSS Grid is the best choice for two-dimensional page layouts.
- This project focuses on modern CSS while understanding the float layout pattern.

### Common layout patterns
- Use a clearfix when floated children collapse the parent container.
- Use the checkbox hack for responsive navigation without JavaScript.
- Set `box-sizing: border-box` so widths include padding and border.

## Architecture and workflow
### Component-driven approach
- Build interfaces as modular, reusable components.
- Keep components independent to improve reuse.
- Plan the layout before writing code.

### BEM methodology
- Block: a standalone component.
- Element: a part of a block with no standalone meaning.
- Modifier: a variant of a block or element.
- Example:
  - `.block {}`
  - `.block__element {}`
  - `.block__element--modifier {}`

### Sass architecture: 7-1 pattern
- One main file imports all partials.
- Seven folder types: `abstracts`, `base`, `components`, `layout`, `pages`, `themes`, `vendors`.
- This structure supports modularity, reuse, and maintainability.

## Project-specific notes
### Header and layout
- Decide before coding which Sass file should own each selector.
- Use Emmet to speed up HTML and CSS authoring.
- Create utility classes for small reusable behaviors.

### Features and cards
- Use `perspective` and `backface-visibility` for 3D card effects.
- Use `box-decoration-break` when styling inline elements across lines.

### Stories section
- Use `shape-outside` to wrap text around floated shapes.
- Use image filters to create subtle visual effects.
- Use `object-fit` for media that should cover a container.

### Booking section
- Use solid-color gradients for polished backgrounds.
- Use `clip-path` to create custom shapes.
- Use the adjacent sibling combinator (`+`) to style an element that follows another.
- Always define `content` and `display` for pseudo-elements.

### Navigation and footer
- The checkbox hack enables mobile navigation without JavaScript.
- Understand the difference between `linear-gradient` and `radial-gradient`.

## Final mindset
- Write clean, modular code.
- Think in terms of reusable components, not only individual pages.
- Use architectural structure and naming consistency.
- Keep performance, readability, and scalability in mind.

---

> These notes are my current summary of the skills I have built while working on the Natours project. I am continuing to refine my workflow and grow toward senior frontend development.
