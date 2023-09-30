---
card_name: Chase Sapphire Preferred
card_brand: Chase
card_summary: The CSP is great for restaurants and okay for travel.
annual_fee: $95
apr: 20.24%-27.24%
apr_variable: True
approx_current_sub_value: $750
issuing_bank: Chase
url: https://creditcards.chase.com/rewards-credit-cards/sapphire/preferred
---

<h1>{{ page.card_name }}</h1>

Here is a brief description.

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
