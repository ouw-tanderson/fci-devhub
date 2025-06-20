# Block Components

---
### Header & Footer Twig Code

**Description:**
This section provides pre-defined HTML snippets for easy copy and paste into the DevHub site, ensuring consistent styling and functionality.

## Header Code 
**Using HTML Block**

```twig
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
## Footer Code
**using HTML Block**

```twig
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

### Financing Components

## Finance Header Block
```twig
<main id="main" class="main siteContent">
            <div class="financingPage">

    <div class="financingHero">
  <div class="financingHero__inner">


    <div class="financingHero__heading">
      <h4 class="financingHero__eyebrow">Financing</h4>
      <h1 class="financingHero__title">Flexible Flooring Financing in Las Vegas</h1>
    </div>
    <h2>Your Dream Floors Made Easy</h2>
    <div class="financingHero__cta">
        
      <p class="financingHero__ctaDescription" style="max-width: 100%;padding-right: 1rem;">
        Flooring is a big investment – it’s important to get exactly what you want so you can enjoy your space for years to come. Our flexible flooring financing options make bringing home the perfect look and materials more accessible. Explore Floor Coverings International® of Las Vegas West’s competitive floor financing plans and get your project started.
      </p>
      <div class="financingHero__ctaLinks" style="flex-direction: column">
        <a href="${base_directory}contact/" target="" class="financingHero__ctaLink button -styleOutline">
          Contact Us for Financing Options
        </a>
        <a href="${base_directory}schedule/" target="" class="financingHero__ctaLink button">
          Schedule a Free Consultation
        </a>
      </div>
    </div>

  </div>
    <div class="financingHero__squares">
    <div class="financingHero__square"></div>
    <div class="financingHero__square"></div>
    <div class="financingHero__square"></div>
    <div class="financingHero__square"></div>
  </div>
</div>



  </div>

  {% set fallback_data = get_object('sites', 1985801) %}
{% if site.locations[0] %}
    {% set location = site.locations[0] %}
{% endif %}
        </main>
```

## Financing Content Block
```html
<div class="htmlcontentPage">
   <div class="htmlcontentarea">
      <div class="htmlcontent_inner">
         <h3>The Right Floors for You, Right Now</h3>
         <p class="fci-cstyle1">We understand that paying for flooring upgrades is a major financial decision, which is why we offer a range of financing options to suit your unique situation. Find the lending party that matches your financing needs, with competitive rates and no money down flooring financing in Las Vegas. Homeowners love our financing program; it’s one of the many reasons we’ve earned hundreds of <a href="https://floorcoveringsinternational.com/locations/us/nv/west-las-vegas/reviews/">positive reviews</a>.</p>
         <h2>Explore Floor Financing in Las Vegas</h2>
         <p class="fci-cstyle1">If you’re ready to explore flooring options for your home, call ${phone} or contact Floor Coverings International® of Las Vegas West for your <a href="https://floorcoveringsinternational.com/locations/us/nv/west-las-vegas/schedule/">free, no-obligation in-home consultation</a> and let our Design Associate bring the showroom to your living room! If you’ve already found your perfect flooring with us, compare competitive offers from our curated financing partners today – and find your best option for Las Vegas flooring financing.</p>
      </div>
   </div>
</div>
```

## Financing Ad Block
```twig
 {% if site.custom_fields['financing_options'] %}
<div class="financingPage__content">
<section class="financingOptions">
    {% for item in site.custom_fields['financing_options'] %}
    <div class="financingOptions__option">
        {% if item.logo %}
        <div class="financingOptions__imageWrapper">
            
            <img decoding="async" class="financingOptions__image lazyload" data-src="${asset_url_prefix}{{ item.logo }}"{% if item.label %} alt="{{ item.label }}"{% endif %}>
            
        </div>
        {% endif %}

        <div class="financingOptions__text">
            {% if item.label %}
            <h2 class="financingOptions__title">{{ item.label }}</h2>
            {% endif %}
            {% if item.link %}
            <a href="{{ item.link }}" class="link link--cta link--medium" target="_blank">
                
                <span>Learn More</span>
                <span class="link__icon">
                    <svg>
                        <use href="#icon-chevron-right"></use>
                    </svg>
                </span>
            </a>
            {% endif %}
        </div>
    </div>
    {% endfor %}
</section>
</div> 
  {% endif %}
```

## Finance Footer Block
```twig
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
