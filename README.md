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
File: `css/extra_css.css`

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

### Phone Link Short Code
**Description:**
This section provides a short code for creating a phone link that can be used in HTML editors.

````html
<a href="tel:${phone}">${phone}</a>
````

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

### Custom Gallery

**Description:**
This section provides a custom gallery layout for displaying images in a grid format.

**Example:**``
```html
<section class="photo-gallery">
	<h2>Our Recent Laminate Projects</h2>
	<div class="gallery-grid">
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-1.jpg" alt="Close-up of laminate flooring showing realistic wood grain and texture." class="gallery-image lazyload">
			<p class="caption">Laminate flooring delivers the rich look of real wood with impressive accuracy. From natural grain patterns to authentic textures, it combines style with durability, making it a versatile and cost-effective choice for any space.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-2.jpg" alt="Close-up of laminate flooring showing realistic wood grain and texture." class="gallery-image lazyload">
			<p class="caption">Laminate flooring delivers the rich look of real wood with impressive accuracy. From natural grain patterns to authentic textures, it combines style with durability, making it a versatile and cost-effective choice for any space.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-3.jpg" alt="Professional installing laminate flooring with precision tools for seamless finish." class="gallery-image lazyload">
			<p class="caption">Proper installation is crucial for the longevity and performance of laminate flooring. With precision tools and expert technique, we ensure flawless seams, secure locking systems, and a smooth, professional finish—maximizing durability and beauty in every project.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-4.jpg" alt="Laminate flooring installed on stairs, providing a modern wood-look finish." class="gallery-image lazyload">
			<p class="caption">Laminate is a great way to refresh stairs with a modern, durable finish. It provides the look of real wood while offering added resistance to wear and tear. Our expertise ensures precise installation, creating seamless transitions and a polished, professional result.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-5.jpg" alt="Clean laminate floor surface, easy to maintain and resistant to stains." class="gallery-image lazyload">
			<p class="caption">Laminate flooring is designed for effortless maintenance—just a quick sweep or mop keeps it looking fresh. Its smooth, sealed surface resists stains and dirt, making it a hassle-free choice for busy homes and businesses.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-6.jpg" alt="Laminate flooring being installed over existing tile for a refreshed look." class="gallery-image lazyload">
			<p class="caption">Laminate flooring can be installed directly over existing tile, eliminating the need for messy and costly demolition. This makes it a convenient, budget-friendly option for refreshing spaces with minimal disruption. Our expert installation ensures a seamless fit, giving your floors a fresh, polished look without the hassle.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-7.jpg" alt="Floating laminate floor panels being clicked together without glue or nails." class="gallery-image lazyload">
			<p class="caption">Most laminate floors are installed as floating systems, meaning they don’t require glue or nails—just a secure, click-lock design. This makes installation quick and efficient, minimizing downtime while delivering a flawless, professional finish.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-8.jpg" alt="Laminate flooring in a home with children and pets, showing scratch resistance." class="gallery-image lazyload">
			<p class="caption">Laminate flooring is perfect for homes with kids and pets, thanks to its durability and scratch resistance. Its tough wear layer protects against spills, claws, and everyday wear, making it a practical and stylish choice for busy households.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-9.jpg" alt="Installer cutting laminate flooring outdoors to minimize dust during installation." class="gallery-image lazyload">
			<p class="caption">Laminate flooring installation is quick and hassle-free, thanks to its simple click-lock system. Any cutting or adjustments are done outside, keeping dust and mess away from your home. The result? A clean, efficient process and a beautifully finished floor without the disruption.</p>
		</div>
	</div>
</section>

<style>
	.photo-gallery {
		max-width: 1200px;
		margin: 2em auto;
		padding: 0 1em;
		text-align: center;
		}

	.gallery-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		gap: 1em;
		}

	.gallery-item {
		display: flex;
		flex-direction: column;
		align-items: center;
		}

	.gallery-item img {
		width: 100%;
		height: auto;
		border-radius: 8px;
		object-fit: cover;
		box-shadow: 0 2px 6px rgba(0,0,0,0.1);
		transition: transform 0.3s ease;
		}

	.gallery-item img:hover {
		transform: scale(1.02);
		}

	.caption {
		margin-top: 0.5em;
		font-size: 0.875rem;
		color: #333;
		text-align: left;
		}
</style>
```
