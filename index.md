---
title: Welcome to my new project!
layout: home
---

I am starting with DataTables:

https://datatables.net/forums/discussion/73297/column-widths-for-datatables-on-just-the-docs-github-page

https://talk.jekyllrb.com/t/filter-page-functionality-ebay-amazon-style/1251/

https://jekyllrb.com/docs/collections/

https://datatables.net/plug-ins/filtering/

https://just-the-docs.github.io/just-the-docs/docs/ui-components/tables/

https://idratherbewriting.com/documentation-theme-jekyll/mydoc_tables.html#jquery-datatables

---

## Proposed initial format

The following items are meant to help identify

```
---
layout: home
name: String
brand: String
annual_fee: $
apr: %-%
apr_variable: Bool
approx_current_sub_value: $
issuing_bank: String
url: Link

foreign_transaction_fee: %
car_rental_cdw_type: Primary/Secondary/None
travel_accident_insurance: Bool
tip_insurance: Bool
extended_warranty: Bool
purchase_protection: Bool
cell_phone_protection: Bool
price_protection: Bool
bag_delay: Bool
open_membership: Bool
membership: String

point_or_cb_reward: point/cb
approx_cpp: Double
approx_cpp_reasoning: String
reward_base: Double %/x
reward_mobilepay: Double %/x
reward_rent: Double %/x
reward_gas: Double %/x
reward_ev: Double %/x
reward_grocery: Double %/x
reward_clubstore: Double %/x
reward:_dining: Double %/x
reward_drugstore: Double %/x
reward_bills: Double %/x
bill_types: String
reward_travel: Double %/x
travel_types: String
reward_air: Double %/x
reward_hotel: Double %/x
reward_cruise: Double %/x
reward_travel_portal: Double %/x
travel_portal_types: String
reward_entertainment: Double %/x
reward_streaming: Double %/x
reward_rotating: Double %/x

other_credits_max_value: $
other_credits_types: String
---
```



---

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
    $('#cards_table').DataTable();
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
    </tr>
  </thead>
  <tbody>
  {% for card in site.cards %}
    <tr>
      <td><a href="{{ card.url }}">{{ card.name }}</a></td>
      <td>{{ card.brand }}</td>
      <td>{{ card.annual_fee }}</td>
      <td>{{ card.apr }}</td>
      <td>{{ card.apr_variable }}</td>
      <td>{{ card.approx_current_sub_value }}</td>
      <td>{{ card.issuing_bank }}</td>
    </tr>
  {% endfor %}
  </tbody>
</table>

