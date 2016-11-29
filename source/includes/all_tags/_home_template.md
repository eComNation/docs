## 4.2. Home Template tags.

### 4.2.1. Feature product

> Feature product  liquid tags :

```html
{% for product in store.featured_products %}
  <a href="{{ product.url }}">
    <img src=" {{ product | product_img_url : 'list' }}" alt=""/>
    {{ product.name }}
    {{ product.price | money:store }}
  </a>
{% endfor %}
```
{% for product in store.featured_products %} ... {% endfor %}

<table>
	<thead>
		<td>Description </td>
		<td>Tags</td>
	</thead>
	<tbody>
		<tr>
			<td>Return the product url</td>
			<td>{{ product.url }}</td>
		</tr>
		<tr>
			<td>Generates the image tag with its product image url</td>
			<td>{{ product | product_img_tag }} </td>
		</tr>
		<tr>
			<td>Return product image url</td>
			<td>{{ product | product_img_url : 'list' }} eg: medium, list, thumb</td>
		</tr>
		<tr>
			<td>Return the product name</td>
			<td> {{ product.name }}</td>
		</tr>
		<tr>
			<td>Return the price of a product</td>
			<td>{{ product.price | money:store }}</td>
		</tr>
		<tr>
			<td>Return the previous price of a product</td>
			<td>{{ product.previous_price | money:store }}</td>
		</tr>
	</tbody>
</table>

### 4.2.2. Blog post

> Blog post liquid tags for home template :

```html
{% for post in store.blog_posts limit:2 %}  
  <a href="{{ post.url }} ">{{post.title}} </a>
  <img src="{{ post.hero_image.big_url }}" alt="{{ post.hero_image.alt_text }}"> 
  {{post.published_on | date: "%B %d, %Y" }} 
{% endfor %}
```
{% for post in store.blog_posts %} ... {% endfor %}

<table>
	<thead>
		<td>Description </td>
		<td>Tags</td>
	</thead>
	<tbody>
		<tr>
			<td>Return the blog post url</td>
			<td>{{ post.url }}</td>
		</tr>
		<tr>
			<td>Return big image for blog post</td>
			<td>{{ post.hero_image.big_url }}</td>
		</tr>
		<tr>
			<td>Return small image for blog post</td>
			<td>{{ post.hero_image.small_url }}</td>
		</tr>
		<tr>
			<td>Return thumb image for blog post</td>
			<td>{{ post.hero_image.thumb_url }}</td>
		</tr>
		<tr>
			<td>Return alt text for hero image</td>
			<td> {{ post.hero_image.alt_text }}</td>
		</tr>
		<tr>
			<td>Return the published date of the post</td>
			<td>{{ post.published_on | date: "%B %d, %Y" }} </td>
		</tr>
	</tbody>
</table>