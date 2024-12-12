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
