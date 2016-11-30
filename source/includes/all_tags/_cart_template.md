## 4.5. Cart Template tags

### 4.5.1. Iterate Cart items

> Iterate Cart items :

```html
{% for item in cart.items %}
  <tr>
    <td>
      <a href="{{ item.product.url }}"><img src="{{ item.product | product_img_url: 'thumb' }}" alt=""></a>
      {{ item.name }}{{ item.option.name }}
    </td>
    <td>
      QUANTITY  <input type="text" size="2" value="{{ item.quantity }}" />
    </td>
    <td>
      PRICE  {{ item.unit_price |  money: store |remove: ".00"}}
    </td>
    <td>SUB TOTAL {{ item.actual_price | money: store |remove: ".00"}}</td>
  </tr>
{% endfor %}
```

{% for item in cart.items %} ... {% endfor %}

<table>
	<thead>
		<tr>
			<th>Description</th>
			<th>Tags</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Return cart discounted total</td>
			<td>{{ cart.total_discount }}</td>
		</tr>
		<tr>
			<td>Return cart actual amount wiht  currency</td>
			<td>{{ cart.actual_cart_amount | money : store }}</td>
		</tr>
		<tr>
			<td>Return item with selected varient</td>
			<td>{{ item.option.name }}</td>
		</tr>
		<tr>
			<td>Return item quantity</td>
			<td>{{ item.quantity }}</td>
		</tr>
		<tr>
			<td>Return product thumb size image</td>
			<td>{{ item.product | product_img_url: 'thumb' }}</td>
		</tr>
		<tr>
			<td>Return Products price with currency</td>
			<td>{{ item.unit_price |  money: store }}</td>
		</tr>
		<tr>
			<td>Return Products previous price with currency</td>
			<td>{{ item.actual_price | money: store }}</td>
		</tr>
	</tbody>
</table>

### 4.5.2. Cart Calculator

> Cart Calculator :

```html
{% if cart.total_discount %}
	Total  : <strong>{{ cart.actual_cart_amount | money : store }}</strong>
	Discount: <strong>{{ cart.total_discount | money : store }}</strong>
  {% if cart.gift_card_applied? %}
		Gift Card Amount : <strong>{{ cart.gift_card_amount | money : store }}</strong>
  {% endif %}
  Grand Total : <strong>{{ cart.discounted_cart_amount | minus: cart.gift_card_amount | money : store }}</strong>
{% else %}
  {% if cart.gift_card_applied? %}
  	Gift Card Amount : <strong>{{ cart.gift_card_amount | money : store }}</strong>
  {% endif %}
  Total : <strong>{{ cart.actual_cart_amount | minus: cart.gift_card_amount | money : store "}}</strong>
{% endif %}
```

<table>
	<thead>
		<tr>
			<th>Description</th>
			<th>Tags</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Return cart actual amount with currency</td>
			<td>{{ cart.actual_cart_amount | money : store }}</td>
		</tr>
		<tr>
			<td>Return cart discounted amount with currency</td>
			<td>{{ cart.total_discount | money : store }}</td>
		</tr>
		<tr>
			<td>Return applied gift card amount</td>
			<td>{{ cart.gift_card_amount | money : store }}</td>
		</tr>
		<tr>
			<td>Return total cart amount if giftcard and discount coupone is applied</td>
			<td>{{ cart.discounted_cart_amount | minus: cart.gift_card_amount | money : store }}</td>
		</tr>
		<tr>
			<td>Return total cart amount if giftcard is applied</td>
			<td>{{ cart.actual_cart_amount | minus: cart.gift_card_amount | money : store }}</td>
		</tr>
	</tbody>
</table>