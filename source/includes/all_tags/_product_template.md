## 4.4. Product Template tags

### 4.4.1. Basic liquid tags for Product 

> Basic liquid tags for Product :

```html
<h1>{{ product.name }}</h1>
<strong>{{ product.price | money : store | remove: ".00" }}  
<del>{{ product.previous_price | money : store | remove: ".00" }}</del>
<p>{{ product.description }}</p>
{{ product.detailed_description }}
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
			<td>Return name of the product</td>
			<td>{{ product.name }}</td>
		</tr>
		<tr>
			<td>Return product SKU</td>
			<td>{{ product.sku }}</td>
		</tr>
		<tr>
			<td>Return the product url</td>
			<td>{{ product.url }}</td>
		</tr>
		<tr>
			<td>Return product category</td>
			<td>{{ product.category.name }}</td>
		</tr>
		<tr>
			<td>Return product parent category</td>
			<td>{{ product.category.parent.name }}</td>
		</tr>
		<tr>
			<td>Return Products price with currency</td>
			<td>{{ product.price | money : store }}</td>
		</tr>
		<tr>
			<td>Return Products previous price with currency</td>
			<td>{{ product.previous_price | money : store }}</td>
		</tr>
		<tr>
			<td>Return the product Description of the product page</td>
			<td>{{ product.description }}</td>
		</tr>
		<tr>
			<td>Returen Detail Description of the product</td>
			<td>{{ product.detailed_description | paragraphs }}</td>
		</tr>
	</tbody>
</table>

### 4.4.2. Iterate Product images 

> Iterate Product images :

```html
{% for product_image in product.product_images %}
  <img src="{{ product_image | img_url: 'medium'}}" alt="" /> 
{% endfor %}
```
{% for product_image in product.product_images %} ... {% endfor %}

<table>
	<thead>
		<td>Tags</td>
		<td>Description</td>
	</thead>
	<tbody>
		<tr>
			<td>Return url of Orignal image or generate image tag with url</td>
			<td>{{ product | product_img_url }} or {{ product | images_tag }}</td>
		</tr>
		<tr>
			<td>Return url of Medium image or generate image tag with url</td>
			<td>{{ product | product_img_url: 'medium' }} or {{ product | images_tag: 'medium' }}</td>
		</tr>
		<tr>
			<td>Return url of List image or generate image tag with url</td>
			<td>{{ product | product_img_url: 'list' }} or {{ product | images_tag: 'list' }}</td>
		</tr>
		<tr>
			<td>Return url of Thumb image or generate image tag with url</td>
			<td>{{ product | product_img_url: 'thumb' }} or {{ product | images_tag: 'thumb' }}</td>
		</tr>
	</tbody>
</table>

### 4.4.2. Iterate the related products

> Iterate the related products tag:

```html
{% if product.related_products.size > 0 %}
  {% for related_product in product.related_products %}
    <a href="{{related_product.url}}">
      <img src="{{related_product | product_img_url}}" alt="{{ related_product.name }}"  />
    </a>
    <p>
      {{ related_product.name }}
      {{ related_product.price | money:store }}
      {{ related_product.previous_price | money:store }}
    </p>
  {% endfor %}
{% endif %}
```
                               
<table>
	<thead>
		<td>Description</td>
		<td> Tags</td>
	</thead>
	<tbody>
		<tr>
			<td>Return related product name</td>
			<td>{{ related_product.name }}</td>
		</tr>
		<tr>
			<td>Return related product url </td>
			<td>{{ related_product.url }}</td>
		</tr>
		<tr>
			<td>Return related product image url</td>
			<td>{{ related_product.product_image_url }}</td>
		</tr>
		<tr>
			<td>Return related product price with currency</td>
			<td>{{ related_product.price | money : store }}</td>
		</tr>
		<tr>
			<td>Return related product previous price with currency</td>
			<td>{{ related_product.previous_price | money : store }}</td>
		</tr>
	</tbody>
</table>