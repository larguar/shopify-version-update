## Files to Create/Copy
1. assets/style.css.liquid
2. assets/script.js.liquid
3. snippets/footer-paper.liquid


## Files to Update
1. layout/theme.liquid
2. snippets/social-icons.liquid
3. snippets/icon-pack.liquid
4. snippets/theme-symbols.liquid
5. sections/header.liquid
6. sections/footer.liquid


## Code

:file_folder: **layout/theme.liquid**

Search for `{{ 'theme.css' | asset_url | stylesheet_tag }}` and add below:
```
{% comment %} [LG] Custom CSS File {% endcomment %}
{{ 'style.css' | asset_url | stylesheet_tag }}
{% comment %} [LG] End Custom CSS File {% endcomment %}
```

Search for `</body>` and add above:
```
{% comment %} [LG] Custom JS File {% endcomment %}
{{ 'script.js' | asset_url | script_tag }}
{% comment %} [LG] End Custom JS File {% endcomment %}

{% comment %} [LG] Klaviyo Back in Stock Flow {% endcomment %}
<script src="https://a.klaviyo.com/media/js/onsite/onsite.js"></script>
<script>
    var klaviyo = klaviyo || [];
    klaviyo.init({
      account: "Sd5RY7",
      platform: "shopify",
      exclude_on_tags: 'clearance'
    });
    klaviyo.enable("backinstock",{ 
    trigger: {
      product_page_text: "Notify Me When Available",
      product_page_class: "add-to-cart button button--solid button--product button--loader button--move",
      product_page_text_align: "center",
      product_page_margin: "0px",
      replace_anchor: false
    },
    modal: {
     headline: "{product_name}",
     body_content: "Have no fear! We'll send you an email as soon as this item is back in stock. Just let us know the best email to reach you.",
     email_field_label: "Email",
     button_label: "Notify me when available",
     subscription_success_label: "You're in! We'll let you know when it's back.",
     footer_content: '',
     additional_styles: "",
     drop_background_color: "#000",
     background_color: "#fff",
     text_color: "#222",
     button_text_color: "#fff",
     button_background_color: "#439fdb",
     close_button_color: "#ccc",
     error_background_color: "#fcd6d7",
     error_text_color: "#C72E2F",
     success_background_color: "#d3efcd",
     success_text_color: "#1B9500"
        }
    });
</script>
{% comment %} [LG] End Klaviyo Back in Stock Flow {% endcomment %}
```

Search for `[LG]` in case this list is missing anything. Paste wherever applicable.

:file_folder: **snippets/social-icons.liquid**

Search for `{%- if settings.social_custom != '' -%}` and add to the `<a>`:
```
class="threads"
```

Do the same for Facebook, Instagram, Pinterest, and TikTok:
```
class="facebook"
```
```
class="instagram"
```
```
class="pinterest"
```
```
class="tiktok"
```

In the `{%- if settings.social_custom != '' -%}` section, add above `<span class="icon" aria-hidden="true">`:
```
<span class="visually-hidden">Threads</span>
```

In the same section, replace `<img>` between `<span class="icon" aria-hidden="true"></span>`:
```
<svg fill="none" viewBox="0 0 448 512" xmlns="http://www.w3.org/2000/svg"><path d="M331.5 235.7c2.2 .9 4.2 1.9 6.3 2.8c29.2 14.1 50.6 35.2 61.8 61.4c15.7 36.5 17.2 95.8-30.3 143.2c-36.2 36.2-80.3 52.5-142.6 53h-.3c-70.2-.5-124.1-24.1-160.4-70.2c-32.3-41-48.9-98.1-49.5-169.6V256v-.2C17 184.3 33.6 127.2 65.9 86.2C102.2 40.1 156.2 16.5 226.4 16h.3c70.3 .5 124.9 24 162.3 69.9c18.4 22.7 32 50 40.6 81.7l-40.4 10.8c-7.1-25.8-17.8-47.8-32.2-65.4c-29.2-35.8-73-54.2-130.5-54.6c-57 .5-100.1 18.8-128.2 54.4C72.1 146.1 58.5 194.3 58 256c.5 61.7 14.1 109.9 40.3 143.3c28 35.6 71.2 53.9 128.2 54.4c51.4-.4 85.4-12.6 113.7-40.9c32.3-32.2 31.7-71.8 21.4-95.9c-6.1-14.2-17.1-26-31.9-34.9c-3.7 26.9-11.8 48.3-24.7 64.8c-17.1 21.8-41.4 33.6-72.7 35.3c-23.6 1.3-46.3-4.4-63.9-16c-20.8-13.8-33-34.8-34.3-59.3c-2.5-48.3 35.7-83 95.2-86.4c21.1-1.2 40.9-.3 59.2 2.8c-2.4-14.8-7.3-26.6-14.6-35.2c-10-11.7-25.6-17.7-46.2-17.8H227c-16.6 0-39 4.6-53.3 26.3l-34.4-23.6c19.2-29.1 50.3-45.1 87.8-45.1h.8c62.6 .4 99.9 39.5 103.7 107.7l-.2 .2zm-156 68.8c1.3 25.1 28.4 36.8 54.6 35.3c25.6-1.4 54.6-11.4 59.5-73.2c-13.2-2.9-27.8-4.4-43.4-4.4c-4.8 0-9.6 .1-14.4 .4c-42.9 2.4-57.2 23.2-56.2 41.8l-.1 .1z"/></svg>
```

:file_folder: **snippets/icon-pack.liquid**

Search for `{%- elsif icon == "paper-bag" -%}` and replace `<svg>`:
```
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M256 141.3l-22.6-22.6L209.1 94.4C189.7 74.9 163.3 64 135.8 64C78.5 64 32 110.5 32 167.8c0 27.5 10.9 53.9 30.4 73.4l24.2 24.2L256 434.8 425.4 265.4l24.2-24.2c19.5-19.5 30.4-45.9 30.4-73.4C480 110.5 433.5 64 376.2 64c-27.5 0-53.9 10.9-73.4 30.4l-24.2 24.2L256 141.3zm22.6 316.1L256 480l-22.6-22.6L64 288 39.8 263.8C14.3 238.3 0 203.8 0 167.8C0 92.8 60.8 32 135.8 32c36 0 70.5 14.3 96 39.8l1.6 1.6L256 96l22.6-22.6 1.6-1.6c25.5-25.5 60-39.8 96-39.8C451.2 32 512 92.8 512 167.8c0 36-14.3 70.5-39.8 96L448 288 278.6 457.4z"/></svg>
```

:file_folder: **snippets/theme-symbols.liquid**

Search for `{%- elsif icon == "cart" -%}` and replace section for cart, account, search, burger, and close:
```
{%- elsif icon == "cart" -%}

  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><path d="M16 0C7.2 0 0 7.2 0 16s7.2 16 16 16H53.9c7.6 0 14.2 5.3 15.7 12.8l58.9 288c6.1 29.8 32.3 51.2 62.7 51.2H496c8.8 0 16-7.2 16-16s-7.2-16-16-16H191.2c-15.2 0-28.3-10.7-31.4-25.6L152 288H466.5c29.4 0 55-20 62.1-48.5L570.6 71.8c5-20.2-10.2-39.8-31-39.8H99.1C92.5 13 74.4 0 53.9 0H16zm90.1 64H539.5L497.6 231.8C494 246 481.2 256 466.5 256H145.4L106.1 64zM168 456a24 24 0 1 1 48 0 24 24 0 1 1 -48 0zm80 0a56 56 0 1 0 -112 0 56 56 0 1 0 112 0zm200-24a24 24 0 1 1 0 48 24 24 0 1 1 0-48zm0 80a56 56 0 1 0 0-112 56 56 0 1 0 0 112z"/></svg>

{%- elsif icon == "account" -%}

  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M412.1 416.6C398.1 361.1 347.9 320 288 320H224c-59.9 0-110.1 41.1-124.1 96.6C58 375.9 32 319 32 256C32 132.3 132.3 32 256 32s224 100.3 224 224c0 63-26 119.9-67.9 160.6zm-28.5 23.4C347.5 465.2 303.5 480 256 480s-91.5-14.8-127.7-39.9c4-49.3 45.3-88.1 95.7-88.1h64c50.4 0 91.6 38.8 95.7 88.1zM256 512A256 256 0 1 0 256 0a256 256 0 1 0 0 512zm0-256a48 48 0 1 1 0-96 48 48 0 1 1 0 96zm-80-48a80 80 0 1 0 160 0 80 80 0 1 0 -160 0z"/></svg>  

{%- elsif icon == "search" -%}

  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M368 208A160 160 0 1 0 48 208a160 160 0 1 0 320 0zM337.1 371.1C301.7 399.2 256.8 416 208 416C93.1 416 0 322.9 0 208S93.1 0 208 0S416 93.1 416 208c0 48.8-16.8 93.7-44.9 129.1l124 124 17 17L478.1 512l-17-17-124-124z"/></svg>

{%- elsif icon == "burger" -%}

  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><path d="M0 64H448V96H0V64zM0 224H448v32H0V224zM448 384v32H0V384H448z"/></svg>

{%- elsif icon == "close" -%}

  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512"><path d="M192 233.4L59.5 100.9 36.9 123.5 169.4 256 36.9 388.5l22.6 22.6L192 278.6 324.5 411.1l22.6-22.6L214.6 256 347.1 123.5l-22.6-22.6L192 233.4z"/></svg>
```

:file_folder: **sections/header.liquid**

Search for first `<div class="site-nav-container">` and paste above:
```
{% comment %} [LG] Logo Mark for Sticky Header {% endcomment %}
<div class="logo-sticky">
  <a href="/"><img src="https://cdn.shopify.com/s/files/1/0106/9426/2842/files/LogoMark-Black.png?v=1669569930" /></a>
</div>
{% comment %} [LG] End Logo Mark for Sticky Header {% endcomment %}
```

:file_folder: **sections/footer.liquid**

Search for `"id": "content",` in schema and update "type":
```
"type": "liquid",
```

Search for first `<div class="container--large` and paste above:
```
{% comment %} [LG] Footer Paper {% endcomment %}
{%- render 'footer-paper' -%}
{% comment %} [LG] End Footer Paper {% endcomment %}

{% comment %} [LG] Footer Email Sign Up {% endcomment %}
<div class="footer-signup-container">
  <div class="footer-signup">
    <h3><em>Get 10% <span>Off</span> Your First Order</em></h3>
    <p>Let's be pin pals! Be the first to hear about new arrivals, exclusive sales, freebies, & other fun things.</p>
    <div class="form-container"><div class="klaviyo-form-RGmBAq"></div></div>
    <p class="small">By signing up you agree with our <a href="{{ shop.privacy_policy.url | escape }}">Privacy Policy</a> and <a href="{{ shop.terms_of_service.url | escape }}">Terms of Service</a>.</p>
  </div>
</div>
{% comment %} [LG] End Footer Email Sign Up {% endcomment %}
```

Search for `<div class="footer-bottom"` and replace contents inside of `<div class="container--large"></div>`:
```
{% comment %} [LG] Footer Copyright Section {% endcomment %}
<div class="copy-col social">{%- render 'social-icons' -%}</div>

<div class="copy-col copy">
  &copy; 2018–{{ 'now' | date: "%Y" }} {{ shop.name | escape }}, LLC
</div>

<div class="copy-col legal">
  {%- if section.settings.show_locale_selector == false and section.settings.show_country_selector == false -%}
  {%- else -%}
    <div class="footer-localization">
    {%- render 'localization-form', show_country_selector: section.settings.show_country_selector, show_locale_selector: section.settings.show_locale_selector, location: 'footer' -%}
    </div>
  {%- endif -%}
  <ul class="legal-links">
    <li><a href="{{ shop.terms_of_service.url | escape }}">Terms of Service</a></li>
    <li><a href="{{ shop.privacy_policy.url | escape }}">Privacy Policy</a></li>
  </ul>
</div>
{% comment %} [LG] End Footer Copyright Section {% endcomment %}
```


## Customize

:page_facing_up: **Sections ▸ Home page ▸ Footer group**

Update the Content section of the ★★★★★ block to:
```
<div class="ssw-html-widget ssw-reviews-badge-widget" data-module="recommendation" data-name="ReviewsBadge"></div>
<div class="review-text">
<p>5.0 Star Rating based on <span id="review-count">400+</span> Reviews</p>
<p><a href="/pages/reviews">All Reviews</a></p>
</div>
```


## Additional Steps
1. [Shopify Image Hover](https://github.com/larguar/shopify-image-hover)
2. [Shopify Clickable Mega Menu Links](https://github.com/larguar/shopify-clickable-links)
3. [Shopify Short Titles](https://github.com/larguar/shopify-short-titles)
4. [Shopify Product Badges](https://github.com/larguar/shopify-badges)
5. [Shopify Custom Sold Out Button Text](https://github.com/larguar/shopify-sold-out-button)
