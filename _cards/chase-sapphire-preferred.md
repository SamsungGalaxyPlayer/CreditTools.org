---
name: Chase Sapphire Preferred
brand: Chase
card_summary: The CSP is great for restaurants and okay for travel.
annual_fee: $95
apr: 20.24%-27.24%
apr_variable: True
approx_current_sub_value: $750
issuing_bank: Chase
url: https://creditcards.chase.com/rewards-credit-cards/sapphire/preferred
---

<h1>{{ page.name }}</h1>

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

<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.2/css/jquery.dataTables.css">
<script type="text/javascript" charset="utf8" src="https://cdn.datatables.net/1.13.2/js/jquery.dataTables.js"></script>

<!-- DataTable Initialization -->
<script>
$(document).ready(function() {
    $('#{{ page.name }}_table').DataTable();
});
</script>

<table id="{{ page.name }}_table">
  <thead>
    <tr>
      {% for field in site.data.credit_card_template.fields %}
      {% assign field_key = field[0] %}
      {% assign field_details = field[1] %}
      <th>{{ field_details.title }}</th>
      {% endfor %}
    </tr>
  </thead>
  <tbody>
    <tr>
      {% for field in site.data.credit_card_template.fields %}
      {% assign field_key = field[0] %}
      <td>{{ page[field_key] }}</td>
      {% endfor %}
    </tr>
  </tbody>
</table>
