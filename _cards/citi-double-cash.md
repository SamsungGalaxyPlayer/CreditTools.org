---
card_name: Citi Double Cash
card_brand: Citi
card_summary: Perhaps the best-known flat 2% back credit card. Easy with few perks.
annual_fee: $0
apr: 18.49%-28.49%
apr_variable: True
approx_current_sub_value: $0
issuing_bank: Citi
url: https://www.citi.com/credit-cards/citi-double-cash-credit-card
---

<h1>{{ page.card_name }}</h1>

Here is a brief description.

## Specs

<table>
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Value</th>
    </tr>
  </thead>
  <tbody>
    {% for field in site.data.credit_card_template.fields %}
    {% assign field_key = field[0] %}
    {% assign field_details = field[1] %}
    {% if page[field_key] and field_key != 'layout' %}
    <tr>
      <td>{{ field_details.title }}</td>
      <td>{{ page[field_key] }}</td>
    </tr>
    {% endif %}
    {% endfor %}
  </tbody>
</table>
