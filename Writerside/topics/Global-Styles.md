# Global Styles

**Description:**  
Modifies the global styling to match other headers for a seamless and appealing structure.
Modifies the GEO Template hero section subtitle for consistency.

**Usage:**  
All h4 elements and elements with the `.h4sans` class automatically use the consistent font family, weight, and size defined in the global styles. The subtitle in the GEO template hero section also inherits this style for visual consistency. No additional class is required for standard h4 headings.

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

.fci-cstyle1,
.htmlcontent_inner p {
	line-height: var(--size-3);
	font-weight: var(--font-weight-regular);
	font-size: var(--size-125);
	font-family: var(--font-serif);
	}


.htmlcontentPage {
	position: relative
	}

.htmlcontentarea {
	--grid-columns: 12;
	--grid-column-gap: var(--column-gap, 0px);
	--grid-row-gap: var(--row-gap, 1.5rem);
	--grid-gutter-width: 1.75rem;
	--grid-column-width: calc(8.33333vw - var(--grid-gutter-width) * 2 / 12 - var(--grid-column-gap) * 11 / 12);
	--grid-max-width-main: calc(var(--breakpoint-max-width) - var(--grid-gutter-width, 0px) * 2);
	--grid-max-width-column: calc((var(--grid-max-width-main) - 11 * var(--grid-column-gap)) / 12);
	grid-column-gap: 0;
	grid-column-gap: var(--grid-column-gap);
	-moz-column-gap: 0;
	column-gap: 0;
	-moz-column-gap: var(--grid-column-gap);
	column-gap: var(--grid-column-gap);
	display: grid;
	grid-row-gap: 1.5rem;
	grid-row-gap: var(--grid-row-gap);
	grid-template-columns: [wide-start] 1.75rem [main-start] repeat(6, minmax(0, var(--grid-max-width-column))) [center] repeat(6, minmax(0, var(--grid-max-width-column))) [main-end] 1.75rem [wide-end];
	grid-template-columns: [wide-start] var(--grid-gutter-width) [main-start] repeat(6, minmax(0, var(--grid-max-width-column))) [center] repeat(6, minmax(0, var(--grid-max-width-column))) [main-end] var(--grid-gutter-width) [wide-end];
	row-gap: 1.5rem;
	row-gap: var(--grid-row-gap);
	--column-gap: max(var(--size-1), min(3vw, var(--size-3)));
	overflow: hidden;
	position: relative
	}

.htmlcontent_inner {
	grid-column: main-start/main-end;
	margin: 0 auto;
	position: relative;
	width: 100%;
	z-index: 1
	}


@media screen and (min-width: 1600px) {
	.htmlcontentarea {
		--grid-gutter-width: calc((100vw - var(--grid-max-width-main)) / 2);
		--grid-max-width-main: calc(var(--breakpoint-min-width) - var(--breakpoint-gap) * 2)
		}
	}
```
