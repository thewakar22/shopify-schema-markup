# Shopify: Manual Schema Markup Implementation
This repo is an example for how to implement schema code manual to your Shopify website without any 3rd party add-ons.

# Schema Markup Implementation Guide

## Overview
This repository provides a step-by-step guide for implementing manual schema markup on your website. Schema markup helps search engines understand the content and context of your web pages, leading to better visibility in search results.

## Why I created this repo?
This repository provides a step-by-step guide for implementing manual schema markup on your website. Schema markup helps search engines understand the content and context of your web pages, leading to better visibility in search results.

## Getting Started
Follow these steps to get started with schema markup:

1. **Understanding Schema Markup:**
   - Learn about schema.org and the different types of schema available (e.g., Article, Product, Organization).
   - Identify which schema type is relevant for your content.

2. **Adding Schema Markup:**
   - Open your HTML file (or any other markup format you're using).
   - Locate the relevant content (e.g., an article, product details, or event information).
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
