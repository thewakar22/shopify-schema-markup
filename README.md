# Shopify: Manual Schema Markup Implementation
This repo is an example for how to implement schema code manual to your Shopify website without any 3rd party add-ons.
![Rich Snippets Results](https://github.com/thewakar22/shopify-schema-markup/blob/main/schema%20makup%20example.jpg)

# Schema Markup Implementation Guide

## Overview
This repository provides a step-by-step guide for implementing manual schema markup on your website. Schema markup helps search engines understand the content and context of your web pages, leading to better visibility in search results.

## Why I created this repo?
I’m an SEO expert, and one day, I decided to explore Shopify. My mission? To manually adding schema markup. Now, I’m not a coding pro or a Shopify expert, but I wanted to learn. So, let me explain more in detail.

🔍 The Problem: I needed to find information about implementing schema markup manually on Shopify. Most tutorials were outdated and  complicated—they assumed everyone was a coding genius or talked about old stuff like “product.liquid.”

🛠️ My Solution: Started experimenting with something called “liquid variables.” It sounds fancy, but it’s just a way to get info from Shopify. I figured out which variables to utilise for product details.

📂 Navigating Files: The usual “product.liquid” file wasn’t around anymore. But after editing a bunch of liquid and json files, I stumbled upon “main-product.liquid” This was the secret sauce for adding schema markup manually.

## Getting Started
Follow these steps to get started with schema markup:

1. **Understanding Schema Markup:**
   - This repo is specificaly dedicated for Product schema markup implementation with rating and review.
   - using Judge Reveiw plugin for creating sample reviews.

2. **Adding Schema Markup:**
   - Go to shopify admin and EDit Code.
   - Locate "main-product.liquid" file to add the schema markup code.
   - Add schema markup using JSON-LD or Microdata. For example:
     ```json
     {
     "@context": "https://schema.org/",
      "@type": "Product",
      "name": "{{product.title}}",
      "image": "{{ shop. url }}/cdn/shop/{{ product.featured_image }}",
      "description": "{{page_description}}",
      "brand": {
        "@type": "Brand",
        "name": "{{product.vendor}}"
      },
      "sku": {{ product.selected_or_first_available_variant.sku | json }},
      "gtin13": {{ product.variants.first.barcode | json }},
      "offers": {
        "@type": "Offer",
        "url": "{{ canonical_url }}",
        "priceValidUntil": "{{ 'now' | date: '%s' | plus: 31536000 | date: '%Y-%m-%d' | replace:'+','%20' }}",
        "priceCurrency": "{{shop.currency}}",
        "price": "{{product.price | money_without_currency}}",
        "availability": "https://schema.org/{% if product.selected_or_first_available_variant %}InStock{% else %}OutOfStock{% endif %}",
        "itemCondition": "https://schema.org/NewCondition"
      },
      "aggregateRating": {
        "@type": "AggregateRating",
        "ratingValue": "{{product.metafields.reviews.rating.value}}",
        "ratingCount": "{{product.metafields.reviews.rating_count}}"
      }
     }
     ```

3. **Testing Your Markup:**
   - Use Google's Structured Data Testing Tool to validate your schema markup.
   - Fix any errors or warnings.

4. **Publishing Your Changes:**
   - Commit your changes to this repository.
   - Push them to GitHub.

## Disclaimer
This is an work in progress repo, so I will keep updating it with more information after finishing more tests.

## Resources
- Schema.org Validator: <https://validator.schema.org/>
- Rich Snippets Testing: <https://search.google.com/test/rich-results>
- Google's Structured Data Documentation: <https://developers.google.com/search/docs/appearance/structured-data/search-gallery>
