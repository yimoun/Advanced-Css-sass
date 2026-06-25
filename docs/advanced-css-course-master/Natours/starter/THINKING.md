# THINKING

## SECTION 2
In this first section I learned a lot:

- CSS properties such as `clip-path`.
- The easiest way to center anything with `transform`, `top`, and `left`.
- How to create CSS animations with `@keyframes` and the `animation` property.
- How and why to use pseudo-classes and pseudo-elements such as `::after`.
- How to create a custom hover animation using `transition`.

All of these concepts were explored, learned, and applied in the `<header>` section of the final HTML page.

Whenever I needed to deepen what I was seeing, I read the relevant documentation.

## SECTION 3
In this second section I learned a lot:

### The three pillars of good frontend web development
1. Responsive design
   - fluid layouts
   - media queries
   - responsive images
   - correct units
   - desktop-first vs mobile-first
2. Maintainable and scalable code
   - clean
   - easy to understand
   - growth-ready
   - reusable
   - how to organize files
   - how to name classes
   - how to structure HTML
3. Web performance (faster and better)
   - fewer HTTP requests
   - less code
   - compressed code
   - use a CSS preprocessor, for example Sass
   - optimize images
   - compress images

### HOW CSS WORKS BEHIND THE SCENES
1. Load HTML.
2. Parse HTML.
    - Load CSS.
        - Parse CSS.
            - cascade: resolve conflicting CSS declarations.
            - compute final CSS values.
        - Final CSS is also stored in the CSSOM (CSS Object Model).
3. Document Object Model (DOM): the browser creates the DOM, which describes the document as a tree.
4. DOM and CSSOM are combined into the render tree.
    - this leads to website rendering with the visual formatting model,
      and finally the final rendered website appears.

### THE CASCADE AND SPECIFICITY
`!important` gives a selector greater specificity, and this usually indicates the code needs refactoring.

Cascade: the process of combining different stylesheets and resolving conflicts between CSS rules when more than one rule applies to the same element.

Different sources of CSS declarations:
- Author: the developer himself.
- User.
- Browser (default).

The cascade resolves conflicts by considering importance, specificity, and source order.

Specificity: from smallest to largest:
1. inline style
2. IDs
3. classes, pseudo-classes, attributes
4. elements, pseudo-elements

Specificity is not really a single number; it is a number for each of the four categories.
For each category, count occurrences in the selector.
When selectors have the same importance, compare specificity numbers category by category from left to right.
If one selector has fewer occurrences in a category, it loses.

In practice, when a declaration is not working, I start with the selector that has the highest specificity in the category that differs and increase the occurrences in that category only enough so the declaration works.

### HOW CSS IS PARSED
CSS values are processed in 6 steps:
1. Declared value: author declarations.
2. Cascaded value: after the cascade.
3. Specified value: defaulting if there is no cascaded value.
4. Computed value: converting relative values to absolute values according to the unit used.
5. Used value: final calculations based on layout.
6. Actual value: after browser and device restrictions.

Unit references:
- `%` unit: for fonts, the reference is the parent’s computed font-size; for lengths such as height, padding, margin, the reference is always the parent element width.
- `em` unit: for font sizes, the reference is the parent computed font-size. For lengths, the reference is the current element computed font-size.
- `rem` unit: always relative to the root font-size, which is usually `16px`.
- `vh` unit: 1% of the viewport height.
- `vw` unit: 1% of the viewport width.

## HERITANCE IN CSS
`inherit` forces inheritance on a property. Some properties cannot be inherited.
`initial` resets a property to its initial value.
For example, text-related properties are inherited: `font-family`, `font-size`, `color`, etc.

## CONVERTING PX TO REM: AN EFFECTIVE WORKFLOW
Note: `rem` is not supported by Internet Explorer 9, but it is supported by almost every other browser.

How and why we use `rem` units in our project: ideally we do it at the beginning of the project.
A good workflow for converting `px` to `rem`: set the root `font-size` at the beginning of the project using a percentage of `16px`.

## HOW CSS RENDERS A WEBSITE: THE VISUAL FORMATTING MODEL
The visual formatting model is the algorithm that calculates boxes and determines the layout of these boxes for each element in the render tree.
It uses parameters like:
- box dimensions: the box model;
- box type: inline, block, inline-block;
- positioning scheme: floats and positioning;
- stacking contexts;
- other elements in the render tree;
- viewport size, image dimensions, etc.

Using `box-sizing: border-box`, height and width are defined for the entire box, including padding and border, not just the content area.

### Display modes
- `display: block`:
  - elements are formatted visually as blocks.
  - occupy 100% of the parent’s width.
  - stack vertically.
  - height and width apply.
- `display: inline`:
  - content is distributed in lines.
  - occupies only the content’s space.
  - no line breaks.
  - height and width do not apply.
  - padding and margins apply only horizontally.
- `display: inline-block`:
  - a mix of block and inline.
  - occupies only the content’s space.
  - no line break.
  - box model applies.

## POSITIONING SCHEMES: NORMAL FLOW, ABSOLUTE, AND FLOATS
- Normal flow using `position: relative`: default positioning scheme.
  - not floated;
  - not absolutely positioned;
  - elements are laid out according to source order.
- Floats: `float: left`, `float: right`.
- Absolute/fixed positioning:
  - the element is removed from normal flow;
  - it has no impact on surrounding content;
  - use `top`, `bottom`, `left`, and `right` to offset it relative to its container.

## STACKING CONTEXTS
Stacking contexts determine the order in which elements are rendered on the page.
A new stacking context can be created by different CSS properties.
The most well-known is `z-index`.
Stacking contexts are like layers: elements at the bottom appear first; elements higher in the stack overlap those below.
The one with the higher `z-index` appears on top.

## CSS ARCHITECTURE, COMPONENTS, AND BEM
It is important to make good decisions from the start to have clean, modular, reusable code that is ready for growth.
Good strategy and mindset: THINK — BUILD — ARCHITECTURE.
- THINK: think about the layout of your page before writing code.
- BUILD: build your layout in HTML and CSS with consistent class naming.
- ARCHITECTURE: create a logical CSS architecture with folders and files.

### Step 1: THINK
#### Component-driven design
- Modular building blocks make up interfaces.
- They are held together by page layout.
- Reusable across a project and between projects.
- Independent, allowing us to use them anywhere on the page.

### Step 2: BUILD
#### BEM (Block Element Modifier)
- BLOCK: standalone component that is meaningful on its own.
- ELEMENT: part of a block that has no standalone meaning.
- MODIFIER: a different version of a block or element.

In code it looks like:
- `.block {}`
- `.block__element {}`
- `.block__element--modifier {}`

### Step 3: ARCHITECTURE
#### The 7-1 PATTERN
Seven folders for partial Sass files, and one main Sass file to import all the other files into a compiled CSS stylesheet.
- The 7 folders: `abstracts/`, `base/`, `components/`, `layout/`, `pages/`, `themes/`, `vendors/`.
- Held together by the layout of the page.
- Reusable across a project and between projects.
- Independent, allowing us to use them anywhere on the page.

## SECTION 4: Introduction to Sass and NPM
### What is SASS?
- A CSS preprocessor, an extension of CSS that adds power and elegance to the base language.
- It is used to solve problems we have with CSS.
- It provides features and tools that CSS by itself does not.

### Sass features
- Variables: for reusable values such as colors, font sizes, spacing.
- Nesting: to nest selectors inside one another, allowing us to write less code.
- Operators: for mathematical operations inside CSS.
- Partials and imports: to write CSS in different files and import them into one file.
- Mixins: to write reusable pieces of CSS.
- Functions: similar to mixins, but they produce a value.
- Extends: to make selectors inherit declarations common to all of them.
- Control directives: for writing complex code with conditionals and loops.

There are two Sass syntaxes: SASS syntax (indentation) and SCSS syntax (preserves normal CSS appearance).

### First steps with Sass: mixins, extends, and functions
- Extensions and mixins seem to work in opposite ways.
- Mixins allow code to be reused by calling them anywhere.
- Extends are useful for selectors that are thematically related, allowing them to share the same declarations.

### Workflow notes
- Install Sass locally with npm.
- Install a local live server and run it in the starter folder.

## SECTION 5: Natours Project — using Advanced CSS and Sass
There are essentially four big responsive web design principles:
- fluid layouts
- responsive units
- flexible images
- media queries

### Fluid layouts
- Allow the page to adapt to the current viewport width (or height).
- Use `%`, `vh`, or `vw` instead of `px` for layout elements.
- Use `max-width` instead of `width`.

### Responsive units
- Use `rem` instead of `px` for most lengths.
- It makes it easier to scale the layout automatically.

### Flexible images
- By default, images don't scale automatically when the viewport changes.
- Use `%` for image dimensions with `max-width`.

### Media queries
- Change styles for specific viewport widths (breakpoints).
- They allow developers to create different versions of the website for different devices.

### Layout types
- FLOAT layouts: the old way to build layouts using `float`; still useful but becoming outdated.
- FLEXBOX: modern way of laying out elements in one dimension; ideal for components.
- CSS GRID: for creating two-dimensional page layouts and complex components.
- This first project focuses on modern CSS techniques and float behavior.
- The second project will focus on Flexbox and the third on CSS Grid.

### Building a custom grid with floats
- When child elements are floated, the parent height collapses.
- Use a clearfix on the parent.

### Building the About section
- Before writing any code, think about architecture and responsive design.
- Ask: which Sass file does this selector belong to?
- Use Emmet for faster HTML and CSS authoring.
- Add a well-written section in the final README describing installed extensions and why they were used.

### Utility classes
- Utility classes are very simple CSS classes with a single goal.
- They should be independent and reusable.
- Always think about making elements reusable and independent for better interfaces.

### Building the Features and Tours sections
- Use linear icons.
- Use `perspective` in CSS.
- Use `backface-visibility`.
- Use `box-decoration-break` when appropriate.
- Absolutely positioned elements are removed from normal flow and overlap other elements.
- The parent height does not include absolutely positioned elements.

### Building the Stories section
- Use `shape-outside` to make text flow around shapes.
- Use `filter` on images.
- Use `object-fit` for videos and images covering a section.

### Building the Booking section
- Implement solid-color gradients.
- Use the right tool for the situation: `clip-path` can be used like a linear gradient to customize background shapes.
- Use the adjacent sibling combinator to style the element after another.
- Every pseudo-element needs `content` and `display`.

### Building the footer and navigation
- Learn how the checkbox hack works.
- Create a creative effect.
- Understand the difference between `linear-gradient` and `radial-gradient`.


# SECTION 5