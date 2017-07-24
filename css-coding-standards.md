CSS Coding Standards
====================

CSS Coding Standards you must conform to when writing CSS in Saffire projects.

## Table of contents

- [Overview](#overview)
- [Naming conventions](#naming-conventions)
- [Brackets](#brackets)
- [Indentation](#indentation)
- [Selectors](#selectors)
- [Property Order](#property-order)
- [Font Embedding](#font-embedding)
- [Font Stacks](#font-stacks)
- [Values](#values)
- [Multiple selectors](#multiple-selectors)
- [Shorthand properties](#shorthand-properties)
- [Properties with multiple values](#properties-with-multiple-values)
- [Positioning](#positioning)
- [Clearing Floats](#clearing-floats)
- [Document Flow](#document-flow)
- [TODO Comments](#todo-comments)
- [Classes & IDs](#classes-&-ids)
- [Preprocessors](#preprocessors)

## Overview

The standards herein are a guide to keep developers at the Saffire interoperable amongst each other and able to produce the highest quality code given the timeline.

Always aim to meet the standards knowing you'll have to break the rules at some point. Be thoughtful about when you deviate and check with a senior developer for guidance if necessary.


### Expectations

- Understand and follow the standards outlined in this document.
- Write code knowing that someone else might be maintaining it.

### Goals

Strive to make your code:

- semantic
- accessible
- predictable
- reusable
- flexible
- understandable
- scalable
- performant
- maintainable
- interoperable

## Naming Conventions

Always use hyphens in class names. Do not use underscores or CamelCase notation.

```css
/* Correct */
.sec-nav

/* Wrong */
.sec_nav
.SecNav
```

## Brackets

Place the opening curly-bracket of each rule block on the same line as the last selector.
Place the closing curly-bracket of each rule block on its own line after the final property of the rule block.

```css
.selector {
  color: #000;
  font-family: Times, "Times New Roman", serif;
}
```

## Indentation

Use 2 spaces for indenting.

```css
.selector {
  color: #000;
  font-family: Times, "Times New Roman", serif;
}
```

## Selectors

Selectors should be on a single line, with a space after the selector, followed by an opening brace. A selector should end with a closing brace on the next line. Next selector should be on the next line with one additional line space between them.

```css
.nav li {
}

.nav a {
}
```

## Property Order

CSS properties should be grouped by commonality (display, then box-model, then positioning, then background/color, then typography, then misc/etc).

```css
.selector {
  display: block;
  width: 400px;
  height: 222px;
  padding: 4px;
  margin: 2px;
  position: absolute;
  top: 22px;
  left: -12px;
  color: #ffffff;
  font: 12/1.2 normal Helvetica, Arial, san-serif;
  text-transform: uppercase;
  text-indent: 0;
}
```

## Font Embedding

Use `@font-face` to embed custom fonts.

Font services like TypeKit or the Google Font API may be used. If embedding from a third party site is required, opt to use a CSS method over one that requires JavaScript.


```css
@font-face {
  font-family: 'FontAwesome';
  src: 	url('fonts/fontawesome-webfont.eot?v=4.6.1');
  src: 	url('fonts/fontawesome-webfont.eot?#iefix&v=4.6.1') format('embedded-opentype'),
  		url('fonts/fontawesome-webfont.woff2?v=4.6.1') format('woff2'),
  		url('fonts/fontawesome-webfont.woff?v=4.6.1') format('woff'),
  		url('fonts/fontawesome-webfont.ttf?v=4.6.1') format('truetype'),
  		url('fonts/fontawesome-webfont.svg?v=4.6.1#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
```

**Resources**

- <http://www.google.com/fonts/>
- <http://www.fontsquirrel.com/>
- <https://typekit.com/>


## Font Stacks

Choose font stacks with care, being mindful to ensure all bases are covered. Good font stacks generally have 2-4 font fallbacks declared and set the browser default serif or sans-serif last in the stack.

```css
/* Correct */
.selector {
  font-family: "open_sans_regular", Arial, Helvetica, sans-serif;
}
/* Wrong */
.selector {
  font-family: "open_sans_regular";
}
```

**Resources**

- <http://nicewebtype.com/notes/2009/04/23/css-font-stacks/>
- <http://www.cssfontstack.com/>

## Values

Shorten hexidecimal color values to 3 digits when possible:

```css
background: #fff;
```

Do not use unit with a value of 0.

```css
/* Correct */
.nav a {
  padding: 5px 0 5px 2px;
}

/* Wrong */
.nav a {
  padding: 5px 0px 5px 2px;
}
```

## Multiple selectors

Multiple selectors should each be on a single line, with no space after each comma.

```css
.faqs a.open,
.faqs a.close {
}
```


## Shorthand properties

Use shorthand properties wherever possible.

```css
/* Correct */
.nav a {
  padding: 5px 0;
}

/* Wrong */
.nav a {
  padding-top: 5px;
  padding-left: 0;
  padding-bottom: 5px;
  padding-right: 0;
}
```

## Properties with multiple values

When properties can have multiple values, each value should be separated with a comma then one space.

```css
.selector {  
  font-family: "Lucida Grande", "Lucida Sans Unicode", Verdana, lucida, sans-serif;
}
```

## Positioning

Do not use absolute positioning to layout the main sections of a page. When using positioning in CSS, leave a comment describing the context.

```html
<div class="carousel">
  <ul class="carousel-slides">
    ...
  </ul>
  <ul class="carousel-nav">
    ...
  </ul>
</div>
```

```css
.carousel {
  position: relative; /* A positioning reference for .carousel-nav */
}

.carousel-nav {
  position: absolute; /* Positioned against .carousel base class */
  right: 20px;
  bottom: 20px;
}
```

## Clearing Floats

All floats should be cleared using the micro clearfix syntax.

```html
<ul class="nav">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```

```css
.nav:after {
  content: " ";
  display: table;
  clear: both;
}

.nav > li {
  float: left;
}
```

**Resources**

- <http://nicolasgallagher.com/micro-clearfix-hack/>
- <https://css-tricks.com/all-about-floats/>

## Document Flow

Take advantage of the natural document flow when spacing content by using *only* margin bottom on content elements so they can easily be interchanged while keeping a predictable document flow and avoiding margin collapsing issues.

Additionally use padding on containers to keep a consistent "edge".

```html
<div class="box">
    <div class="user-content">
        <h2>All About Cats</h2>
        <p> ... </p>
        <p> ... </p>
        <h3> Nocturnal Habits</h3>
        <p> ... </p>
        <p> ... </p>
    </div>
</div>
```

```css
.box {
  padding: 20px;
  background: #ffffff;
}

.user-content h2 {
  font-size: 24px;
  color: #333333;
  margin-bottom: 12px;
}

.user-content h3 {
  font-size: 20px;
  color: #333333;
  margin-bottom: 12px;
}

.user-content p {
  font-size: 12px;
  margin-bottom: 12px;
}
```


### TODO Comments

Mark todos and action items with a comment that includes `TODO`. Be sure that `TODO` is always uppercase.

```css
/* TODO - Review content styles */
.selector {
    color: #ff0000;
}
```

### Classes & IDs

**Do not** use `id` for styling purposes

Acceptable uses for `id` include:

* JavaScript selection
* Assigning form labels to inputs
* Jump links between sections of a page

```html
<div class="carousel" id="js-carousel"> ... </div>
```

```html
<label for="first-name">First Name</label>
<input type="text" id="first-name" class="input input-txt" />
```

```html
<a href="#main-content">Skip to Main Content</a>

...

<div class="content" id="main-content"> ... </div>
```

## Preprocessors

### Property Order
- Always place `@extend` statements on the first lines of a declaration block.
- Where possible, group `@include` statements at the top of a declaration block, after any `@extend` statements.
- Nested classes are always last.

```scss
.selector {
  @extend .other-rule;
  @include clearfix();
  @include box-sizing(border-box);
  margin: 10px;
  padding: 10px;
  &:hover {
    background: DarkCyan;
  }
  &::before {
    content: "";
    display: block;
  }
  > h3 {
    @include transform(rotate(90deg));
    border-bottom: 1px solid white;
  }
}
```

### Nesting
Limit nesting to 3 level deep. This prevents overly-specific CSS selectors.
- Avoid large numbers of nested rules. Avoid nesting that spreads over more than 50 lines.

```scss
.selector {
  .other-rule {
    li {
      // no more!
    }
  }
}
```

### Comments

Comments in all scss files should be done with `//` syntax so they are not compiled into production code.
