---
title: Welcome to CreditTools.org!
layout: home
---

CreditTools.org is a not-for-profit website that aims to educate individuals on good credit card and other financial habits. It aims to be the definitive free resource on credit cards.

{: .friendly}
CreditTools.org does NOT provide financial or legal advice. All this content is for education purposes only.

CreditTools.org is [open source]() on GitHub, so anyone can [propose changes](). Your help is much appreciated!

Get started by clicking on one of the items to the left of the screen (or in the navbar on mobile).

---

## Proposed initial format

This initial format will allow us to create useful summary tables. Additional context about the card can be displayed underneath on individual pages.

```
---
layout: home
card_name: String
card_brand: String
annual_fee: $
card_type: Visa/Mastercard/American Express/Discover
intro_apr: %
intro_offer: String  <!-- MAX 140 characters! Additional context can be provided on the card page. -->
ongoing_apr: %-%
apr_variable: Bool
cash_advance_ongoing_apr: %-%
approx_current_sub_value: $
issuing_bank: String
url: Link

foreign_transaction_fee: %  <!-- Put 0% if no FTF -->
car_rental_cdw_type: Primary/Secondary/None
travel_accident_insurance: Bool
trip_insurance: Bool
extended_warranty: Bool
purchase_protection: Bool
cell_phone_protection: Bool
flight_price_protection: Bool
hotel_price_protection: Bool
bag_delay_compensation: Bool
bag_loss_protection: Bool
free_bag: Bool  <!-- Checked, carry-on, or both -->
airport_lounge_cardholder_access: Bool
airport_lounge_guest_access: Bool
concierge_service: String  <!-- Delete this row if not applicable -->
open_membership: Bool
membership: String  <!-- Delete this row if not applicable -->

point_or_cb_reward: point/cb/none
approx_cpp: Double
approx_cpp_reasoning: String <!-- MAX 140 characters! Additional context can be provided on the card page. -->
reward_base: Double %/x
reward_mobilepay: Double %/x
reward_rent: Double %/x
reward_gas: Double %/x
reward_ev: Double %/x
reward_grocery: Double %/x
reward_clubstore: Double %/x
reward_dining: Double %/x
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

