# Finance Page

### New & Optimization Finance Page Implementation Guide

1. Add a new page **"Blank Normal Page"**. This *must* be named **Financing** with the URL as `/financing/`.
2. Copy HTML code from the top and bottom using code below for header, content, finance, footer. example used: [Las Vegas West, NV Finance](https://floorcoveringsinternational.cloudfrontend.net/app/builder/1986092/25732934).
3. The top block is an HTML Code module – Edit the H1 and `financingHero__ctaDescription` to match the Word Doc. (The CTA buttons are already part of the HTML code.)
4. The next block is a Component Template – HTML dropdown.
5. This content is the remainder of the Word document.
6. Paste it into the [Word2HTML tool](https://wordhtml.com/). Click **Clean**. Adjust H2, etc.
7. Paste the HTML template component after clicking the **[Source] <>** button and clearing the contents.
8. The final section is another HTML code module for the CTA section, with nothing to edit.
9. Under **Page > Page Options**, the Page Title is the SEO Title Tag.
10. Then further under **Advanced**, Description is Meta Description.
11. Publish the page using **"Save and Publish"** under the Save Draft dropdown.
12. View the live page under the Preview dropdown.
13. Put the live link in the [implementation tracker OneNote doc](https://oneupweb.sharepoint.com/sites/localmarketing/_layouts/15/Doc.aspx?sourcedoc=%7b5b70e07d-8986-4311-b652-89f81c07c4fc%7d&action=edit&wd=target%28Implementation.one%7C63218e3a-35e4-44ee-9d32-0d2eebc94973%2FImplementation%20Tracker%20for%20Speed%7Ce61d5783-3283-4ddb-9c36-af6c8ecb65ef%2F%29&wdorigin=NavigationUrl) and in the task comment when you tag Tyler.
14. Mark the task Implemented by adding to the Implemented board.
15. Person who QAs the page will update the board from Implemented to QA Complete once QA is finished. Board will close the task out. Continue to document with a comment on the task and update status of deliverable in the [Local Strategy Tracker](https://oneupweb.sharepoint.com/:x:/s/client-floorcoveringsinternational/EfKwXOnspC5KvtM0KhJasMEBnPwhZBG3vZKykoTFTr2E-w?e=KhmanZ).

### Page Block Components

## Header Block
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

## Content Block
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

## Financing Content Block
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

## Footer Block
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
## Utility Snippets

<include from="utility-codes.md" element-id="css-utility-classes"></include>
<include from="utility-codes.md" element-id="button-options"></include>
<include from="utility-codes.md" element-id="one-column-list-style"></include>
<include from="utility-codes.md" element-id="two-column-split-layout"></include>
