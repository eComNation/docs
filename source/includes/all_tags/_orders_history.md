## 4.13. Customer order History tags

>  Customer order History tags:

```html
<table>
  <thead>
    <th>
    <td><a href="#">Order Status  </a></td>
    <td><a href="#">Order </a></td>
    <td><a href="#">Date of Order </a></td>
    <td><a href="#">Amount </a></td>
    <td><a href="#">Detail </a></td>
    </th>
  </thead>
  <tbody>
    {% for order in orders %}
      <tr>
        <td>{{ order.status }}</td>
        <td>{{ order.number }}</td>
        <td>{{ order.created_at | date: "%B %d, %Y" }}</td>
        <td>{{ order.discounted_amount | money: store }}</td>
        <td><a href="{{ order.details_path }}">View</a></td>
      </tr>
    {% endfor %}   
  </tbody>
</table>
```
{% for order in orders %} ... {% endfor %}
<table>
	<thead>
    <tr>
  		<th>Description</th>
  		<th>Tags</th>
    </tr>
	</thead>
	<tbody>
		<tr>
			<td>Returns order status</td>
			<td>{{ order.status }}</td>
		</tr>
		<tr>
			<td>Returns order number</td>
			<td>{{ order.number }}</td>
		</tr>
		<tr>
			<td>Returns Date when order place</td>
			<td>{{ order.created_at | date: "%B %d, %Y" }}</td>
		</tr>
		<tr>
			<td>Returns Total order value with currency</td>
			<td>{{ order.discounted_amount | money: store }}</td>
		</tr>
		<tr>
			<td>Returns url of order detail </td>
			<td>{{ order.details_path }}</td>
		</tr>
	</tbody>
</table>