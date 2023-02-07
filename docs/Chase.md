---
title: "Chase"
---

# Chase

<script type="text/javascript" src="jquery.dataTables.js"></script>
<script type="text/javascript" src="dataTables.filter.html.js"></script>
<script type="text/javascript">
    $(document).ready(function() {
        $('#example').dataTable( {
            "columnDefs": [
                { type: "type", targets: 0 }
            ]
        } );
    } );
</script>

<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.2/css/jquery.dataTables.css">
<script type="text/javascript" charset="utf8" src="https://code.jquery.com/jquery-3.6.3.min.js"></script>
<script type="text/javascript" charset="utf8" src="https://cdn.datatables.net/1.13.2/js/jquery.dataTables.js"></script>
<script>
$(document).ready( function () {
    $('#businesses_table').DataTable();
} );
</script>

<table id="cards_table">
  <thead>
    <tr>
      <th>Name</th>
      <th>Brand</th>
      <th>Annual Fee</th>
      <th>APR</th>
      <th>Variable?</th>
      <th>Approx. Sub</th>
      <th>Issuing Bank</th>
      <th>Link</th>
    </tr>
  </thead>
  <tbody>
    {% for card in site.cards %}
      {% if card.brand == 'Chase' %}
        <tr>
          <td>{{ card.name }}</td>
          <td>{{ card.brand }}</td>
          <td>{{ card.annual_fee }}</td>
          <td>{{ card.apr }}</td>
          <td>{{ card.apr_variable }}</td>
          <td>{{ card.approx_current_sub_value }}</td>
          <td>{{ card.issuing_bank }}</td>
          <td><a href="{{ card.url }}">More info</a></td>
        </tr>
      {% endif %}
    {% endfor %}
  </tbody>
</table>
