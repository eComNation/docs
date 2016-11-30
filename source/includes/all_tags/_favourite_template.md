## 4.16. Favourite products template
###Iterate Favourite products:
> Iterate Favourite products:

```html
{% if favourite_products.size == 0 %}
  <h5>No Product in wishlist.</h5>
{% else %}
  <table>
    <thead>
      <tr>
        <th>Product Image </th>
        <th>Product Name </th>
        <th>Price </th>
      </tr>
    </thead>
    {% paginate favourite_products by 10 %} 
      {% for favourite_product in favourite_products %}
        <tr>
          <td>
            <a href="{{favourite_product.url}}">
              <img src="{{favourite_product | product_img_url: 'thumb'}}" alt="{{ favourite_product.name }}" class="" />
            </a>
          </td>
          <td><a href="{{favourite_product.url}}">{{favourite_product.name}}</a></td>
          <td>{{ favourite_product.price | money:store}}</td>
        </tr>
      {% endfor %} 
    {% endpaginate %}
  </table>
{% endif %}
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
			<td>Starting tag for favourite products list with number of products</td>
			<td>{% paginate favourite_products by 10 %} </td>
		</tr>
		<tr>
			<td>End tag</td>
			<td>{% endpaginate %}</td>
		</tr>
		<tr>
			<td>Staring tag for iterate favourite products</td>
			<td>{% for favourite_product in favourite_products %}</td>
		</tr>
		<tr>
			<td>End tag</td>
			<td>{% endfor %} </td>
		</tr>
		<tr>
			<td>Returns Product Name</td>
			<td>{{ favourite_product.name }}</td>
		</tr>
		<tr>
			<td>Returns Product url</td>
			<td>{{favourite_product.url}}</td>
		</tr>
		<tr>
			<td>Returns Product image</td>
			<td>{{favourite_product | product_img_url: 'thumb'}}</td>
		</tr>
		<tr>
			<td>Returns Product price with currency</td>
			<td>{{ favourite_product.price | money:store}}</td>
		</tr>
	</tbody>
</table>

###Pagination links for Favourite products
> Pagination links for Favourite products:

```html
{% paginate favourite_products by 10 %} 
  <ul>
    {% if paginate.previous %}
      <li><a href="{{ paginate.previous.url }}">Prev</a></li>
    {% endif %}
    {% if paginate.next %}
      <li><a href="{{ paginate.next.url }}">Next</a></li>
    {% endif %}
  </ul>
{% endpaginate %}
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
			<td>Return url for previous page</td>
			<td>{{ paginate.previous.url }}</td>
		</tr>
		<tr>
			<td>Return url for next page</td>
			<td>{{ paginate.next.url }}</td>
		</tr>
	</tbody>
</table>