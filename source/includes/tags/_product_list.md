## 3.7. Product List

Product lists are displayed using 'blocks'. The product listing block is used in 'catalogue.liquid' template.

>Here is an example of the product list block:

```liquid
<html>
<head>
...
</head>
<body>
<h1>Products</h1> <div class="item"> <ul>
{% for product in store.paginated_products %}
<li>
<h2 class="title"><a href="{{ product.url }}">{{ product.name }}</a></h2> <div class="photo"> <a href="{{ product.url }}">{{ product |product_img_tag
}}</a> </div>
<p class="price">{{ product.price | money : store }}</p>
</li>
{% endfor %}
</ul>
</div>
<div style="clear"></div>
{{ store.paginated_products | will_paginate_liquid: "Prev", "Next" }} </body>
</html>
```

Some of the above code looks familiar to us while some tags are relatively new. Let's understand what each of these tags do:

**{% for product in**	Begins the product block

**store.paginated_products %}{{ product.url }}**	Provides hyperlink to the product detail page.

**{{ product.name }}**	Displays the product title

**{{ product | product_img_tag }}**	Displays the product image (small
	size).
	There are two parts of this tag
	separated by a vertical line. The first
	part 'product' tells the system to
	identify the product and the second
	tag after the vertical line
	"product_image_tag" finds out the
	corresponding image path of the
	product.

**{{ product.price | money : store }}**	Displays the product price.
	There are two parts of this tag
	separated by a vertical line. The first
	part 'product.price' shows the actual
	price of the product while the second
	part after the vertical line 'money' is a
	special operator to covert any number
	into currency format.

**{% endfor %}**	Ends the loop

**{{ store.paginated_products |**	Displays the pagination of the product 

**will_paginate_liquid: "Prev", "Next" }}**	list.
	In this tag, the text written inside the
	double quotes i.e. 'Prev' , 'Next' can
	be changed to any text that you want
	to show.

### 3.7.1 Featured Product List

In addition to the product list, 39shops has a special type of product list called 'Featured Products'. If user has flagged a product 'Featured' from his store administration area, those products are displayed using this Tag.

>Here is an example of featured product list block:

```liquid
<html>
<head>
...
</head>
<body>
<h1>Products</h1>
<div class="item">
<ul>
{% for product in store.featured_products %}
<li>
<h2 class="title"><a href="{{ product.url }}">{{ product.name
}}</a></h2>
<div class="photo"> <a href="{{ product.url }}">{{ product |
product_img_tag }}</a> </div>
<p class="price">{{ product.price | money : store }}</p>
</li>
{% endfor %}
</ul>
</div>
<div style="clear"></div>
{{ store.paginated_products | will_paginate_liquid: "Prev", "Next" }}
</body>
</html>
```

**Explanation**

The only difference between a normal product list and a featured product list is the first line in that tag where we have specified 'store.featured_products' instead of 'store.paginated_products'
