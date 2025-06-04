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

### Global Improved Styling

**Description:**  
Modifies the global styling to match other headers for a seamless and appealing structure.
Modifies the GEO Template hero section subtitle for consistency.

**Usage:**  
Apply the `.h4sans` class to any heading or element to resize its text content.
also applies a specific font style to the subtitle in the hero section of the GEO template.

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

.fci-cstyle1 {
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
	--grid-column-width: calc(8.33333vw - var(--grid-gutter-width)*2/12 - var(--grid-column-gap)*11/12);
	--grid-max-width-main: calc(var(--breakpoint-max-width) - var(--grid-gutter-width, 0px)*2);
	--grid-max-width-column: calc((var(--grid-max-width-main) - 11*var(--grid-column-gap))/12);
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
		--grid-gutter-width: calc((100vw - var(--grid-max-width-main))/2);
		--grid-max-width-main: calc(var(--breakpoint-min-width) - var(--breakpoint-gap)*2)
		}
	}

```

### Image linking in devhub and twig
**Description:**
This section provides a method to link images in the DevHub site using Twig syntax, ensuring that images can be dynamically linked to their respective pages or sections via cloud.


**Example:**
`src="${asset_url_prefix}/img/upload/img_9262-1.jpg"`

**Useage**
```html
${asset_url_prefix}
```

### Template Changes
**GEO Template Changes**

on GEO Template Page in hero section I added a class called `geo_hero` to <section> with class name `heroBranch`.


---

## Copy / Paste Content

**Description:**
This section provides pre-defined HTML snippets for easy copy and paste into the DevHub site, ensuring consistent styling and functionality.

---
## Header & Footer Twig Code

### Header Code

```html
{% if site.locations[0] %} 
{% set location = site.locations[0] %} 
{% endif %} 
{% set fallback_data = get_object('sites', 1985801) %} 
<section class="heroBranch">
   <div class="heroBranch__wrapper">
      <div class="heroBranch__content">
         <h1 class="heroBranch__title"> 
            <span class="heroBranch__subtitle hero__subtitle hero__subtitle--tight">Plano Tile</span> 
            Installation Services 
            <span class="heroBranch__subtitle hero__subtitle hero__subtitle--tight"></span> 
         </h1>
         <div class="heroBranch__assets">
            <div class="heroBranch__imageWrap"> 
               {% if site.custom_fields['branch_hero_left_image'] %} 
               <img decoding="async" class="heroBranch__image" src="${asset_url_prefix}{{ site.custom_fields['branch_hero_left_image']}}" alt="{{ site.custom_fields['branch_hero_left_image_alt'] }}"> 
               {% else %} 
               <img decoding="async" class="heroBranch__image fallback" src="${asset_url_prefix}{{ fallback_data.custom_fields['branch_hero_left_image']}}" alt="{{ site.custom_fields['branch_hero_left_image_alt'] }}"> 
               {% endif %} 
            </div>
            <div class="heroBranch__imageWrap"> 
               {% if site.custom_fields['branch_hero_right_image'] %} 
               <img decoding="async" class="heroBranch__image fallback" src="${asset_url_prefix}{{ site.custom_fields['branch_hero_right_image']}}" alt="{{ site.custom_fields['branch_hero_right_image_alt'] }}"> 
               {% else %} 
               <img decoding="async" class="heroBranch__image" src="${asset_url_prefix}{{ fallback_data.custom_fields['branch_hero_right_image']}}" alt="{{ site.custom_fields['branch_hero_right_image_alt'] }}"> 
               {% endif %} 
            </div>
         </div>
      </div>
      <div class="heroBranch__contact">
         <h2 class="heroBranch__subtitle">Your local team 
            <span class="heroBranch__subtitle--accent">{{ site.custom_fields['location_name'] }}</span> 
         </h2>
         <address class="heroBranch__address">
            <div class="heroBranch__infoWrap">
               <div class="heroBranch__icon">
                  <a href="tel:${phone}" aria-label="Call us">
                     <svg class="heroBranch__svg">
                        <use xlink:href="#icon-phone"></use>
                     </svg>
                  </a>
               </div>
               <div class="heroBranch__info">
                  <p class="heroBranch__phone"> 
                     <span class="heroBranch__address--block heroBranch__eyebrow eyebrow">Give us a call</span> 
                     <a class="heroBranch__number" href="tel:${phone}" aria-label="Phone number">${phone}</a> 
                  </p>
               </div>
            </div>
            <div class="heroBranch__infoWrap">
               <div class="heroBranch__icon">
                  <svg class="heroBranch__svg">
                     <use xlink:href="#icon-location"></use>
                  </svg>
               </div>
               <div class="heroBranch__info">
                  {% if not site.custom_fields['service_area_only']|lazy_boolean %} 
                  <span class="heroBranch__address--block heroBranch__street">{{ site.custom_fields['address_line_1'] }} {% if location.street2 %}{{ site.custom_fields['suiteunit'] }}{% endif %}</span>{% endif %} 
                  <span class="heroBranch__address--block heroBranch__city"> ${city}, ${state} ${postal_code}</span> 
                  <span class="heroBranch__address--block heroBranch__hours eyebrow">
                     {% if location.hours_by_type.primary %} 
                     {% set hours = location.hours_by_type.primary|hours_formatter %} 
                     <div> 
                        {% for day in hours.filtered_days(group_days=True) %} 
                        <span class="heroBranch__address--block heroBranch__hours eyebrow"> 
                        {{ day.label }} {{ day.content }} 
                        </span> 
                        {% endfor %} 
                     </div>
                     {% endif %}  
                  </span>
               </div>
            </div>
         </address>
         <div class="heroBranch__actions"> 
            <a href="${base_directory}schedule/" class="heroBranch__button button">Schedule An In-Home Consultation</a> 
            <a href="${base_directory}contact/" class="heroBranch__button button -styleOutline">Tell Us About Your Project</a> 
         </div>
      </div>
      <div class="heroBranch__state">
         <svg width="225" height="225">
            <use href="#${state}-icon"></use>
         </svg>
      </div>
      {% if page.custom_fields['light_blue_bar_promo_text'] %} 
      <div class="heroBranch__promo">
         <div class="promo-image-wrapper"> 
            <img src="{{ page.custom_fields['light_blue_bar_promo_image'] }}" alt="{{ page.custom_fields['light_blue_bar_promo_image_alt'] }}"> 
         </div>
         <div class="promo-text-wrapper">
            <em>{{ page.custom_fields['light_blue_bar_promo_subheading'] }}</em> 
            <p>{{ page.custom_fields['light_blue_bar_promo_text'] }}</p>
         </div>
      </div>
      {% endif %} 
   </div>
</section>
```
### Footer Code

```html
{% set fallback_data = get_object('sites', 1985801) %} 
{% if site.locations[0] %} 
{% set location = site.locations[0] %} 
{% endif %} 
<section class="section contactTeam cta">
   <div class="contactTeam__wrapper">
      <div class="contactTeam__intro">
         <h2 class="contactTeam__header">Contact our ${custom_location_display_name} team</h2>
         <p class="contactTeam__blurb"> 
            {{ site.custom_fields['follow_us_body_text'] or fallback_data.custom_fields['follow_us_body_text'] }} 
         </p>
         <a class="contactTeam__phone link--large" href="tel:${phone}">$phone</a> 
      </div>
      <div class="contactTeam__cta">
         <div class="contactTeam__icon">
            <svg class="contactTeam__svg icon">
               <use xlink:href="#icon-phone"></use>
            </svg>
         </div>
         <a class="contactTeam__link link link--cta link--medium" href="${base_directory}contact/">
            Tell us about your project 
            <svg class="link__icon">
               <use xlink:href="#icon-chevron-right"></use>
            </svg>
         </a>
      </div>
      <div class="contactTeam__cta contactTeam__cta--wrap">
         <div class="contactTeam__icon contactTeam__icon--van">
            <svg class="contactTeam__svg icon">
               <use xlink:href="#icon-van"></use>
            </svg>
         </div>
         <a class="contactTeam__link link link--cta link--medium" href="${base_directory}schedule/">
            Schedule a free consultation 
            <svg class="link__icon">
               <use xlink:href="#icon-chevron-right"></use>
            </svg>
         </a>
      </div>
   </div>
   <div class="contactTeam__diamonds cta__diamonds">
      <svg class="contactTeam__diamond cta__diamond" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 461 922" style="enable-background:new 0 0 461 922;" xml:space="preserve">
         <rect x="50.4" y="514.3" transform="matrix(0.7071 -0.7071 0.7071 0.7071 -391.8595 289.9836)" style="fill:#EDF9FB;" width="207.4" height="207.4"></rect>
         <rect x="210.5" y="359.3" transform="matrix(0.7071 -0.7071 0.7071 0.7071 -235.3613 357.7397)" style="fill:#EDF9FB;" width="207.4" height="207.4"></rect>
         <rect x="50.4" y="201.4" transform="matrix(0.7071 -0.7071 0.7071 0.7071 -170.5754 198.3247)" style="fill:#EDF9FB;" width="207.4" height="207.4"></rect>
         <rect x="-105.7" y="356.7" transform="matrix(0.7071 -0.7071 0.7071 0.7071 -326.1361 133.3818)" style="fill:#EDF9FB;" width="207.3" height="207.4"></rect>
         <rect x="-104.1" y="671.6" transform="matrix(0.7071 -0.7071 0.7071 0.7071 -548.3438 226.755)" style="fill:#EDF9FB;" width="207.3" height="207.3"></rect>
         <rect x="-104.1" y="43.2" transform="matrix(0.7071 -0.7071 0.7071 0.7071 -103.9569 42.6838)" style="fill:#EDF9FB;" width="207.3" height="207.4"></rect>
      </svg>
   </div>
</section>
```

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

```html
<ul class="list">
```

```html
<li class="productFacts__benefit">
```

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

```html
<ul class="list productFacts__benefits">
```

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
