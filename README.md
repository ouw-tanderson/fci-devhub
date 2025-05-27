# FCI DevHub HTML & CSS Styling Documentation

Documentation for custom HTML and CSS used on the DevHub site, including class names, code snippets, and usage instructions for consistent and robust layout and styling.

## Table of Contents

- [CSS Additions/Modifications](#css-additionsmodifications)
  - [H4 Improved Styling](#h4-improved-styling)
- [CSS Utility Classes](#css-utility-classes)
  - [Button Options](#button-options)
  - [One Column List Style](#one-column-list-style)
  - [Two Column List Style](#two-column-list-style)
  - [Two-Column Split Layout](#two-column-split-layout)

---

## CSS Additions/Modifications

### H4 Improved Styling

**Description:**  
Modifies the `<h4>` styling to match other headers for a seamless and appealing structure.

**Usage:**  
Apply the `.h4sans` class to any heading or element to resize its text content.

**How to Add:**  
1. From the Main Dashboard, select **Projects**.
2. In the left navigation, click **Templates**.
3. Click **Template Editor**.
4. In the editor, select the site dropdown at the top center, then choose **Settings**.
5. In the pop-up, click **header/footer**.
6. Scroll to the **Extra CSS** section to add or edit global site CSS.

**CSS:**
```css

.heroBranch.geo_hero .hero__subtitle {
	font-style: normal;
	}

.h4sans,
.richText h4,
.html-block h4 {
	font-family: var(--font-sans);
	font-weight: var(--font-weight-medium);
	font-size: var(--size-fluid-3);
	}

```

### Template Changes
**GEO Template Changes**

on GEO Template Page in hero section I added a class called `geo_hero` to <section> with class name `heroBranch`.


---

## CSS Utility Classes

Pre-defined class names brought over from the original WordPress site for consistency.

### Button Options

**Description:**  
Two styled buttons for use in HTML editors, with predefined links and text.

**Green Button:**
```html
<a href="${base_directory}schedule/" class="button">Schedule An In-Home Consultation</a>
```

**Transparent Outline Button:**
```html
<a href="${base_directory}contact/" class="button -styleOutline">Tell Us About Your Project</a>
```

---

### One Column List Style

**Description:**  
Styled list (ordered or unordered) with spacing and red dashes or numbers.

**Example:**
```html
<ul class="list">
  <li class="productFacts__benefit">Great for any surface</li>
  <li class="productFacts__benefit">Available with stain-resistant grout for high-traffic areas</li>
  <li class="productFacts__benefit">Easy to clean</li>
  <li class="productFacts__benefit">Assorted types, sizes, colors, and patterns</li>
  <li class="productFacts__benefit">Simple to maintain</li>
  <li class="productFacts__benefit">Creates a one-of-a-kind design for any room</li>
</ul>
```

---

### Two Column List Style

**Description:**  
Styled two-column list (ordered or unordered) with spacing and red dashes or numbers.

**Example:**
```html
<ul class="list productFacts__benefits">
  <li class="productFacts__benefit">Great for any surface</li>
  <li class="productFacts__benefit">Available with stain-resistant grout for high-traffic areas</li>
  <li class="productFacts__benefit">Easy to clean</li>
  <li class="productFacts__benefit">Assorted types, sizes, colors, and patterns</li>
  <li class="productFacts__benefit">Simple to maintain</li>
  <li class="productFacts__benefit">Creates a one-of-a-kind design for any room</li>
</ul>
```

---

### Two-Column Split Layout

**Description:**  
Creates a split layout with two columns side by side.

**Example:**
```html
<div class="split">
  <div>Column 1 HTML &amp; content here</div>
  <div>Column 2 HTML &amp; content here</div>
</div>
```
