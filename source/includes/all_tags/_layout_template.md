# 4. CheatSheet

## 4.1. Layout Template tags.

### 4.1.1. Title and Meta liquid tags

> Title and Meta liquid tags :

```html
<html> 
  <head>
  {% if store.which_template == 'Home' %}
    <title>{{ store.name }}</title>
  {% elsif store.which_template == 'Products' %}
    <title>{{ store.name }}</title>
  {% elsif store.which_template == 'Product_Detail' %}
    {% if product.browser_title == blank %}
      <title>{{ product.name }}</title>
    {% else %} 
      <title>{{ product.browser_title }}</title>
    {% endif %}
    <meta name="description" content="{{ product.meta_description }}"/>
    <meta name="keywords" content="{{ product.meta_keywords }}"/>
  {% elsif store.which_template == 'Category' %}
    {% if store.active_category.browser_title == blank %}
      <title>{{ store.active_category.name }}</title>
    {% else %}
      <title>{{ store.active_category.browser_title }}</title>
    {% endif%}
    <meta name="description" content="{{ store.active_category.meta_description }}"/>
    <meta name="keywords" content="{{ store.active_category.meta_keywords }}"/>
  {% elsif store.which_template == 'Page' %}
    {% if page.browser_title == blank %}
      <title>{{ page.title }}</title>
    {% else %} 
      <title>{{ page.browser_title }}</title>
    {% endif %}
    <meta name="description" content="{{page.meta_description}}"/>
    <meta name="keywords" content="{{page.meta_keywords}}"/>
  {% elsif store.which_template == 'Cart' %}
    <title>{{ store.name }}</title>
  {% else %}  
    {% if post.browser_title != blank %}
      <title>{{ post.browser_title }}</title>
      <meta property="og:title" content="{{ post.browser_title }}" />
    {% else %}
      {% if post.title == blank %} 
        <title>{{ store.name }}</title>
      {% else %}
        <title>{{ post.title }}</title>
        <meta property="og:title" content="{{ post.title }}" />
      {% endif %}
    {% endif %}
    {% if post.meta_description != blank %}
      <meta name="description" content="{{ post.meta_description }}">
      <meta property="og:description" content="{{ post.meta_description }}" />
    {% else %}
      <meta name="description" content="{{ post.meta_description }}">
      <meta property="og:description" content="{{ post.meta_description }}" />
    {% endif %}
    {% if post.meta_keywords != blank %}
      <meta name="keywords" content="{{ post.meta_keywords }}">
    {% else %}
      <meta name="keywords" content="{{ post.meta_keywords }}">
    {% endif %}
  {% endif %}
  </head>
</html> 
```


<table>
	<thead>
		<td>Description </td>
		<td>Tags</td>
	</thead>
	<tbody>
		<tr>
			<td>Reture Name of the store</td>
			<td>{{ store.name }}</td>
		</tr>
		<tr>
			<td>To render the other template</td>
			<td>{{ content_for_layout }}</td>
		</tr>
		<tr>
			<td>Browser title Product</td>
			<td>{{ product.browser_title }}</td>
		</tr>
		<tr>
			<td>Product Mate tag description</td>
			<td>{{ product.meta_description }}</td>
		</tr>
		<tr>
			<td>Product Mate tag keyword</td>
			<td>{{ product.meta_keywords }}</td>
		</tr>
		<tr>
			<td>Return the Current category (in catelogue page)</td>
			<td>{{ store.active_category.name }}</td>
		</tr>
		<tr>
			<td>Browser title for Current category</td>
			<td>{{ store.active_category.browser_title }}</td>
		</tr>
		<tr>
			<td>Mate tag description for Current Category</td>
			<td>{{ store.active_category.meta_description }}</td>
		</tr>
		<tr>
			<td>Mate tag keyword for Current Category</td>
			<td>{{ store.active_category.meta_keywords }}</td>
		</tr>
		<tr>
			<td>Browser title for pages</td>
			<td>{{ page.browser_title }}</td>
		</tr>
		<tr>
			<td>Mate tag description for page</td>
			<td>{{ page.meta_description }}</td>
		</tr>
		<tr>
			<td>Mate tag keyword for page</td>
			<td>{{ page.meta_keywords }}</td>
		</tr>
		<tr>
			<td>Returns Blog post title</td>
			<td>{{ post.title }}</td>
		</tr>
		<tr>
			<td>Browser title for Blog post</td>
			<td>{{ post.browser_title }}</td>
		</tr>
		<tr>
			<td>Mate tag description for Blog post</td>
			<td>{{ post.meta_description }}</td>
		</tr>
		<tr>
			<td>Mate tag keyword for Blog post</td>
			<td>{{ post.meta_keywords }}</td>
		</tr>
	</tbody>
</table>

### 4.1.2. Stylesheet and Javascript liquid tags

> Stylesheet and Javascript liquid tags :

```html
<html>
  <head>
    <link type="text/css" rel="stylesheet"  href="{{current_theme.stylesheet_path }}/style.css?{{ store.css_cache_token }}">
    <script src="{{ current_theme.javascript_path }}/main.js?{{ store.js_cache_token }}"></script>
  </head>
</html>
```

<table>
	<thead>
		<td>Description</td>
		<td>Tags</td>
	</thead>
	<tbody>
		<tr>
			<td>Return the path of the Stylesheet director</td>
			<td>{{ current_theme.stylesheet_path }}</td>
		</tr>
		<tr>
			<td>Clear the css cache on the server</td>
			<td>{{ store.css_cache_token }}</td>
		</tr>
		<tr>
			<td>Return the path of the javascript directory </td>
			<td>{{ current_theme.javascript_path }}</td>
		</tr>
		<tr>
			<td>Clear the js cache on the server</td>
			<td>{{ store.js_cache_token }}</td>
		</tr>
	</tbody>
</table>

### 4.1.3. Category iteration liquid tags

> Category and subcategory iteration  :

```html
{% for category in store.categories %}
  {% if category.child_categories.size == 0 %}
    <a class="" href="{{ category.url }}">{{ category.name }}</a>
  {% else %}
    <a  href="{{ category.url }}">{{ category.name }}</a>
    {% for sub_category in category.child_categories %}
       <a href="{{ sub_category.url }}">{{ sub_category.name }}</a>
    {% endfor %}
  {% endif %}
{% endfor %}
```
{% for category in store.categories %} {% endfor %}
<table>
	<thead>
		<td>Description </td>
		<td>Tags</td>
	</thead>
	<tbody>
		<tr>
			<td>Return category url</td>
			<td>{{ category.url }}</td>
		</tr>
		<tr>
			<td>Return category name</td>
			<td>{{ category.name }}</td>
		</tr>
	</tbody>
</table>

### 4.1.4. Total cast items liquid tags

> Total cast items  :

```html
<a href="/cart">{{ cart.total_items }} </a>
```
<table>
	<thead>
		<td>Description </td>
		<td>Tags</td>
	</thead>
	<tbody>
		<tr>
			<td>Return total cart items</td>
			<td>{{ cart.total_items }}</td>
		</tr>
	</tbody>
</table>

### 4.1.4. Current logged in User & Logout liquid tags

> Current logged in User & logout tag:

```html
{% if current_user_name %}
  <a href="/customer/dashboard">Welcome, {{ current_user_name }}</a>
  {% customer_logout_tag Logout %}
{% else %}
  <a class="" href="/customer/login">Login</a>
  <a class="" href="/customer/customers">Register</a>
{% endif %}
```
<table>
	<thead>
		<td>Description</td>
		<td> Tags</td>
	</thead>
	<tbody>
		<tr>
			<td>Return current loggedin users Full name</td>
			<td>{{ current_user_name }}</td>
		</tr>
		<tr>
			<td>Generate logout link</td>
			<td>{% customer_logout_tag Logout %}</td>
		</tr>
	</tbody>
</table>