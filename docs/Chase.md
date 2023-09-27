---
title: "Chase"
---

<h1>{{ page.title }}</h1>

## All {{ page.name }} Cards

<!-- Load the necessary styles and scripts for DataTables -->
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.2/css/jquery.dataTables.css">
<script type="text/javascript" charset="utf8" src="https://code.jquery.com/jquery-3.6.3.min.js"></script>
<script type="text/javascript" charset="utf8" src="https://cdn.datatables.net/1.13.2/js/jquery.dataTables.js"></script>

<!-- DataTables Initialization -->
<script>
$(document).ready( function () {
    $('#{{ page.title }}_cards_table').DataTable({
      ordering: true
    });
} );
</script>

<table id="{{ page.title }}_cards_table">
  <thead>
    <tr>
      <th>Name</th>
      <th>Annual Fee</th>
      <th>Approx. Sub</th>
      <th>Card Summary</th>
    </tr>
  </thead>
  <tbody>
    {% for card in site.cards %}
      {% if card.brand == {{ page.title }} %}
        <tr>
          <td><a href="{{ card.url }}">{{ card.name }}</a></td>
          <td>{{ card.annual_fee }}</td>
          <td>{{ card.approx_current_sub_value }}</td>
          <td>{{ card.card_summary }}</td>
        </tr>
      {% endif %}
    {% endfor %}
  </tbody>
</table>
