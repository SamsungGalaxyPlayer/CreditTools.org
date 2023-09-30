---
card_name: Citi Custom Cash
card_brand: Citi
card_summary: 5% back in your top of pre-selected categories, for up to $500 in purchases per month. Quite versatile.
annual_fee: $0
card_type: Mastercard
intro_apr: 0%
intro_offer: $200 cash back after $1500 spend in first 6 months. 0% APR for 15 months on purchases and balance transfers.
ongoing_apr: 19.24%-29.24%
apr_variable: true
cash_advance_ongoing_apr: 29.99%
approx_current_sub_value: $200
issuing_bank: Citi
url: https://www.citi.com/credit-cards/citi-custom-cash-credit-card
foreign_transaction_fee: 3%
car_rental_cdw_type: None
travel_accident_insurance: false
trip_insurance: false
extended_warranty: false
purchase_protection: false
cell_phone_protection: false
flight_price_protection: false
hotel_price_protection: false
bag_delay_compensation: false
bag_loss_protection: false
free_bag: false
airport_lounge_cardholder_access: false
airport_lounge_guest_access: false
concierge_service: None
open_membership: true
point_or_cb_reward: cb
approx_cpp: 1
approx_cpp_reasoning: Most people redeem at $0.01 for cash back. It is possible to get higher values with transfer partner combinations, or less.
reward_base: 1%
reward_mobilepay: 1%
reward_rent: 1%
reward_gas: 5%
reward_ev: 1%
reward_grocery: 5%
reward_clubstore: 1%
reward_dining: 5%
reward_drugstore: 5%
reward_bills: 1%
reward_travel: 5%
travel_types: Includes airline, hotel, cruise line and travel agency purchases
reward_air: 5%
reward_hotel: 5%
reward_cruise: 5%
reward_travel_portal: 1%
reward_entertainment: 5%
reward_streaming: 5%
reward_rotating: 1%
other_credits_max_value: $0
---

<h1>{{ page.card_name }}</h1>

The Citi Custom Cash is considered a very versatile card, that can be a positive contribution to anyone's collection.

Make sure not to exceed $500 in category purchases per month, and only use one category per month to maximize your cash back.

Earn 5% cash back on purchases in your top eligible spend category each billing cycle, up to the first $500 spent, 1% cash back thereafter.

5% eligible categories: Restaurants, gas stations, grocery stores, select travel, select transit, select streaming services, drugstores, home improvement stores, fitness clubs, live entertainment.

No enrollment is required; you will automatically earn 5% back in your top category.

Earn 1% cash back on all other purchases.

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
