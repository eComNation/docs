## 4.14. Customer order detail template
###Basic order Details

>  Basic order Detail tags :

```html
<p>ORDER # <strong>{{ order.number }}</strong></p>
<p><strong>Placed on:</strong> {{ order.created_at | date: "%B %d, %Y" }}</p>
<p><strong>Payment Status:</strong>{{ order.status }}</p>
<p><strong>Payment Mode:</strong> {{ order.payment_mode }}</p>
<p><strong>Shipping Type:</strong> {{ order.shipping_type }}</p>
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
			<td>Returns order number</td>
			<td>{{ order.number }}</td>
		</tr>
		<tr>
			<td>Returns date of order placed</td>
			<td>{{ order.created_at | date: "%B %d, %Y" }}</td>
		</tr>
		<tr>
			<td>Returns order status<br> eg: pending, packing, ready to dispatch, shipping etc.</td>
			<td>{{ order.status }}</td>
		</tr>
		<tr>
			<td>Returns the mode of payment</td>
			<td>{{ order.payment_mode }}</td>
		</tr>
		<tr>
			<td>Returns shipping type</td>
			<td>{{ order.shipping_type }}</td>
		</tr>
	</tbody>
</table>


###Billing Address

>  Billing Address tags :

```html
<p>
  {{ order.billing_address.name |capitalize }}
  {{ order.billing_address.address1 }}, 
  {{ order.billing_address.address2 }}, 
  {{ order.billing_address.city }}, 
  {{ order.billing_address.state }},
  {{ order.billing_address.country_name }} 
  {{ order.billing_address.zipcode }}
  <span>Phone: {{ order.billing_address.phone }}</span>
</p>
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
			<td>Returns Name on the billing address</td>
			<td>{{ order.billing_address.name |capitalize }}</td>
		</tr>
		<tr>
			<td>Returns address1 on the billing address</td>
			<td>{{ order.billing_address.address1 }}</td>
		</tr>
		<tr>
			<td>Returns address2 on the billing address</td>
			<td>{{ order.billing_address.address2 }}</td>
		</tr>
		<tr>
			<td>Returns city on the billing address</td>
			<td>{{ order.billing_address.city }},</td>
		</tr>
		<tr>
			<td>Returns state on the billing address</td>
			<td>{{ order.billing_address.state }}</td>
		</tr>
		<tr>
			<td>Returns country on the billing address</td>
			<td>{{ order.billing_address.country_name }}</td>
		</tr>
		<tr>
			<td>Returns zipcode on the billing address</td>
			<td>{{ order.billing_address.zipcode }}</td>
		</tr>
		<tr>
			<td>Returns phone number of the customer on the billing address</td>
			<td>{{ order.billing_address.phone }}</td>
		</tr>
	</tbody>
</table>



###Shipping Address

>  Shipping Address tags :

```html
<p>
  {{ order.shipping_address.address1 }},
  {{ order.shipping_address.address2 }},
  {{ order.shipping_address.city }}, 
  {{ order.shipping_address.state }},
  {{ order.shipping_address.country_name }}
  {{ order.shipping_address.zipcode }}
  <span>Phone: {{ order.shipping_address.phone }}</span>
</p>
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
			<td>Returns Name on the billing Shipping</td>
			<td>{{ order.shipping_address.name |capitalize }}</td>
		</tr>
		<tr>
			<td>Returns address1 on the billing Shipping</td>
			<td>{{ order.shipping_address.address1 }}</td>
		</tr>
		<tr>
			<td>Returns address2 on the billing Shipping</td>
			<td>{{ order.shipping_address.address2 }}</td>
		</tr>
		<tr>
			<td>Returns city on the billing Shipping</td>
			<td>{{ order.shipping_address.city }},</td>
		</tr>
		<tr>
			<td>Returns state on the billing Shipping</td>
			<td>{{ order.shipping_address.state }}</td>
		</tr>
		<tr>
			<td>Returns country on the billing Shipping</td>
			<td>{{ order.shipping_address.country_name }}</td>
		</tr>
		<tr>
			<td>Returns zipcode on the billing Shipping</td>
			<td>{{ order.shipping_address.zipcode }}</td>
		</tr>
		<tr>
			<td>Returns phone number of the customer on the Shipping address</td>
			<td>{{ order.shipping_address.phone }}</td>
		</tr>
	</tbody>
</table>

### Iterate Order Item list

>  Iterate Order Item list :

```html
<table>
  <thead>
    <tr>
      <th></th>
      <th>product</th>
      <th>quantity</th>
      <th>cost</th>
      <th>total</th>
    </tr>
  </thead>
  <tbody>
	  {% for item in order.items %}
		  <tr>
		    <td></td>
		    <td>{{ item.name }}</td>
		    <td>{{ item.quantity }}</td>
		    <td>{{ item.unit_actual_price | money: store }}</td>
		    <td>{{ item.actual_price | money: store }}</td>
		  </tr>
	  {% endfor %}
  </tbody>
</table>
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
			<td>Staring tag for order item iteration</td>
			<td>{% for item in order.items %}</td>
		</tr>
		<tr>
			<td>Ending tag</td>
			<td>{% endfor %}</td>
		</tr>
		<tr>
			<td>Returns product name</td>
			<td>{{ item.name }}</td>
		</tr>
		<tr>
			<td>Returns product quantity</td>
			<td>{{ item.quantity }}</td>
		</tr>
		<tr>
			<td>Returns product unit price</td>
			<td>{{ item.unit_actual_price | money: store }}</td>
		</tr>
		<tr>
			<td>Returns product actual price</td>
			<td>{{ item.actual_price | money: store }}</td>
		</tr>
	</tbody>
</table>

### Order Calculation

>  Order Calculation :

```html
{% if order.discount %}
  <tr>
    <td colspan="4">Sub Total</td>
    <td>{{ order.actual_amount | money: store }}</td>
  </tr>
  <tr>
    <td colspan="4">Discount</td>
    <td>{{ order.discount | money: store }}</td>
  </tr>
{% endif %}
<tr>
  <td colspan="4">Sub Total</td>
  <td>{{ order.sub_total | money: store}}</td>
</tr>
{% if order.is_tax_calculated %}
  <tr>
    <td colspan="4">Tax</td>
    <td>{{ order.tax_amount | money: store}}</td>
  </tr>
{% else %}
  <tr>
    <td colspan="4">*All applicable taxes included in total amount*</td>
    <td>0</td>
  </tr>
{% endif %}
<tr>
  <td colspan="4">Shipping & Handling</td>
  <td>{{ order.shipping_charge | money: store }}</td>
</tr>
{% if order.payment_processing_charge %}
  <tr>
    <td colspan="4">Payment processing charges</td>
    <td>{{ order.payment_processing_charge | money: store}}</td>
  </tr>
{% endif %}
<tr>
  <td colspan="4">Grand Total</td>
  <td>{{ order.grand_total | money: store }}</td>
</tr>
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
			<td>Discounted amount with currency</td>
			<td>{{ order.discount | money: store }}</td>
		</tr>
		<tr>
			<td>Actual amount with currency</td>
			<td>{{ order.actual_amount | money: store }}</td>
		</tr>
		<tr>
			<td>Returns difference of actual amount and discounted amount with currency</td>
			<td>{{ order.sub_total | money: store}}</td>
		</tr>
		<tr>
			<td>Returns tax amount with currency </td>
			<td>{{ order.tax_amount | money: store}}</td>
		</tr>
		<tr>
			<td>Returns shipping charge with currency</td>
			<td>{{ order.shipping_charge | money: store }}</td>
		</tr>
		<tr>
			<td>Returns payment processing charge with currency</td>
			<td>{{ order.payment_processing_charge | money: store}}</td>
		</tr>
	</tbody>
</table>