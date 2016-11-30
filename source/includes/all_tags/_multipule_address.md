## 4.11. Iterate Customers Multiple Addresses

>  Iterate Customers Multiple Addresses:

```html
{% for cust in customer.addresses %}
	<p>
		{{ cust.name }}<br>
		{{ cust.phone }}<br>
		{{ customer.login }}<br>
		{{ cust.address1 }}<br>
		{{ cust.address2 }}<br>
		{{ cust.city }}, {{ cust.state }},<br>
		{{ cust.country_name }},<br>
		{{ cust.zipcode }}
	</p>
 	<a href="/customer/edit_details?address_id={{cust.id}}">Edit Address</a>
{% endfor %}
```

<table>
	<thead>
		<tr>
			<th>Description</th>
			<th>Tags / Parameter</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Starting tag for Multiple addresses</td>
			<td>{% for cust in customer.addresses %}</td>
		</tr>
		<tr>
			<td>End tag for Multiple addresses</td>
			<td>{% endform %}</td>
		</tr>
		<tr>
			<td>Returns Customer id</td>
			<td>{{ cust.id }}</td>
		</tr>
		<tr>
			<td>Returns Customer name</td>
			<td>{{ cust.name }}</td>
		</tr>
		<tr>
			<td>Returns Customer phone number</td>
			<td>{{ cust.phone }}</td>
		</tr>
		<tr>
			<td>Returns registered Customers email id</td>
			<td>{{ customer.login }}</td>
		</tr>
		<tr>
			<td>Returns Customer Address1</td>
			<td>{{ cust.address1 }}</td>
		</tr>
		<tr>
			<td>Returns Customer Address2</td>
			<td>{{ cust.address2 }}</td>
		</tr>
		<tr>
			<td>Returns Customer city</td>
			<td>{{ cust.city }}</td>
		</tr>
		<tr>
			<td>Returns Customer state</td>
			<td>{{ cust.state }}</td>
		</tr>
		<tr>
			<td>Returns customer country</td>
			<td>{{ cust.country_name }}</td>
		</tr>
		<tr>
			<td>Returns customer pincode</td>
			<td>{{ cust.zipcode }}</td>
		</tr>
	</tbody>
</table>