---
title: "Chase"
---

<h1>{{ page.title }}</h1>

Chase is known for its "trifecta", or the pairing of at least one Chase Sapphire card (the Sapphire Reserve or Sapphire Preferred) with two other Chase cards. With one of the Sapphire cards, you can maximize the points earned with other cards by transferring them to other partners or using other reward-enhancing techniques.

You do not necessarily need exactly three Chase cards to maximize your rewards potential. Depending on your needs (and your tolerance for additional cards), it may be better to only have one Chase card, or to have more than three. Your mileage will vary!

## All {{ page.title }} Cards

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
      {% if card.brand == page.title %}
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

---

<!-- Parameters Selection -->
<div>
    <label><input type="checkbox" class="column-toggler" data-column="0" checked> Name</label>
    <label><input type="checkbox" class="column-toggler" data-column="1" checked> Annual Fee</label>
    <label><input type="checkbox" class="column-toggler" data-column="2" checked> Approx. Sub</label>
    <label><input type="checkbox" class="column-toggler" data-column="3" checked> Card Summary</label>
    <!-- Add more checkboxes for other parameters -->
</div>

<table id="{{ page.title }}_cards_table_2">
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
        {% if card.brand == page.title %}
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

<script>
$(document).ready(function() {
    let dataTable = $('#{{ page.title }}_cards_table_2').DataTable();

    $('.column-toggler').change(function() {
        let columnIdx = $(this).data('column');
        let column = dataTable.column(columnIdx);
        column.visible(!column.visible());
    });
});
</script>

---

<!-- Parameters Selection -->
<div>
  {% for field in site.data.credit_card_template.fields %}
  {% assign field_key = field[0] %}
  {% assign field_details = field[1] %}
  <label>
    <input type="checkbox" class="column-toggler" data-column="{{ field_key }}" checked>
    {{ field_details.title }}
  </label>
  {% endfor %}
</div>

<!-- Dynamically Generated Table -->
<table id="{{ page.title }}_cards_table_3">
  <thead>
    <tr>
      {% for field in site.data.credit_card_template.fields %}
      {% assign field_details = field[1] %}
      <th>{{ field_details.title }}</th>
      {% endfor %}
    </tr>
  </thead>
  <tbody>
    {% for card in site.cards %}
      {% if card.brand == page.title %}
      <tr>
        {% for field in site.data.credit_card_template.fields %}
        {% assign field_key = field[0] %}
        <td>{{ card[field_key] }}</td>
        {% endfor %}
      </tr>
      {% endif %}
    {% endfor %}
  </tbody>
</table>

<script>
$(document).ready(function() {
    let dataTable = $('#{{ page.title }}_cards_table_3').DataTable();

    $('.column-toggler').change(function() {
        let columnKey = $(this).data('column');
        // Use the field's key to determine the column's index
        let columnIdx = $(`#{{ page.title }}_cards_table_3 th:contains('{{ site.data.credit_card_template.fields[columnKey].title }}')`).index();
        let column = dataTable.column(columnIdx);
        column.visible(!column.visible());
    });
});
</script>
