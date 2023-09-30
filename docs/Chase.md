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
    <label><input type="checkbox" class="column-toggler" data-column="name"> Name</label>
    <label><input type="checkbox" class="column-toggler" data-column="annual_fee"> Annual Fee</label>
    <label><input type="checkbox" class="column-toggler" data-column="approx_current_sub_value"> Approx. Sub</label>
    <label><input type="checkbox" class="column-toggler" data-column="card_summary"> Card Summary</label>
    <!-- Add more checkboxes for other parameters -->
</div>

<table id="{{ page.title }}_cards_table_2">
    <thead>
        <tr>
            <!-- Columns will be added dynamically here based on user selection -->
        </tr>
    </thead>
    <tbody>
        <!-- Rows data will be added dynamically here based on user selection -->
    </tbody>
</table>

<script>
$(document).ready(function() {
    let dataTable;

    // Handle column toggling
    $('.column-toggler').change(function() {
        let columnData = [];
        $('.column-toggler:checked').each(function() {
            let columnName = $(this).data('column');
            columnData.push(columnName);
        });
        rebuildTable(columnData);
    });

    function rebuildTable(columns) {
        // Destroy the existing datatable if any
        if (dataTable) {
            dataTable.destroy();
            $('#{{ page.title }}_cards_table').empty();
        }

        let headerRow = '<tr>';
        columns.forEach(col => {
            headerRow += `<th>${capitalizeFirstLetter(col)}</th>`;
        });
        headerRow += '</tr>';

        $('#{{ page.title }}_cards_table thead').html(headerRow);

        let bodyContent = '';
        {% for card in site.cards %}
        if ("{{ card.brand }}" == "{{ page.title }}") {
            bodyContent += '<tr>';
            columns.forEach(col => {
                bodyContent += `<td>${{ card[col] }}</td>`;
            });
            bodyContent += '</tr>';
        }
        {% endfor %}

        $('#{{ page.title }}_cards_table tbody').html(bodyContent);

        // Initialize datatable on the newly created table structure
        dataTable = $('#{{ page.title }}_cards_table').DataTable();
    }

    function capitalizeFirstLetter(string) {
        return string.charAt(0).toUpperCase() + string.slice(1);
    }
});
</script>
