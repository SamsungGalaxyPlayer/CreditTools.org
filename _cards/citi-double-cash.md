---
name: Citi Double Cash
brand: Citi
card_summary: Perhaps the best-known flat 2% back credit card. Easy with few perks.
annual_fee: $0
apr: 18.49%-28.49%
apr_variable: True
approx_current_sub_value: $0
issuing_bank: Citi
url: https://www.citi.com/credit-cards/citi-double-cash-credit-card
---

<h1>{{ page.name }}</h1>

## Subtitle

# Specs

{% assign fields = site.data.credit_card_template.fields %}
{% for field in fields %}
  {% assign key = field[0] %}
  {% assign context = field[1] %}
  {% if page[key] %}
    {% assign title = context.title | default: key | capitalize %}
    **{{ title }}:** {{ page[key] }}
  {% endif %}
{% endfor %}



