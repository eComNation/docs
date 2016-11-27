# 3. Tags

## 3.1. Tag Basics eComNation has two types of special operators used to render dynamic content in the HTML templates. They are **Variables** and **Blocks**.

### 3.1.1. Variables
Variables are used to insert dynamic data like product title, product price etc.

> Here is an example of variable:

```liquid
<html> 
	<body> 
	  <p>{{ product.name }}</p> 
	</body> 
</html> 
```

### 3.1.2. Blocks

Blocks are either used to render a block of HTML for set of data (example: Category listing), or to conditionally render a block of HTML.

> Here is an example of a block:

```liquid
<html> 
	<body> 
		{% for category in store.categories %} 
		  <li> 
		    <a href="{{category.url}}">{{ category.name }}</a>
		  </li> 
		{% endfor %} 
	</body> 
</html>
```

In the example, the block starts with the tag **{% for category in store.categories %} ** and ends with **{% endfor %}**
In between the bLocks we have the variable to display category name. The **{{category.name}}** variable will be looped with *li* HTML tag to display a list of category name.

<aside class="notice">
Note: Block always begins and ends with a single curly bracket and a percentage sign ‘{% ... %}’ while a variable begins and end with double curly brackets ‘{{ ... }}‘
</aside>

### 3.1.3 Types of Blocks

Mainly, there are two types of blocks supported by 39shops:

The *'For'* block:

{% for ... in ... %}
...
{% endfor %}


This block is used when certain list of items are to be displayed. For example. product list, category list, list of navigation links etc. You can use this block only with dynamic tags.


The *'If'* block:

This block is used when certain data or tag should be displayed conditionally. You can use this tag block anywhere, either with static HTML elements or dynamic tags.

{% if ..... %}
......
{% endif %}

>Here is an example of the 'If' block

```liquid
<html>
	<head>
		<title></title>
	</head>
	<body>
		{% for category in store.categories %} 
			{% if store.categories.name == "Tshirt" %}
				<a href="{{category.url}}">{{ category.name }}</a>
			{% endif %}
		{% endfor %}
	</body>
</html>
```

In the example, the **{% if store.categories.name %}** condition checks if any category name is equal to the "Tshirt". If the condition is true, the link should be displayed otherwise it should not displayed.


## 3.2. Using Stylesheets and JavaScript

Stylesheets and JavaScripts are the fundamental building blocks of any design. You can insert Stylesheets and JavaScripts into your 39shops theme within the *head* tag of your 'Layout'. Here are the tags:

>**For Stylesheet:**
```liquid
<link href="{{ current_theme.stylesheet_path }}/stylesheet-file.css" rel="stylesheet" type="text/css"/>
```

>**For JavaScript:**
```liquid
<script src="{{ current_theme.javascript_path }}/javascript-file.js" type="text/Javascript"></script>
```

>Here is an example:

```liquid
<head>
	<title>My pet store</title>
	<link href="{{ current_theme.stylesheet_path }}/default.css" rel="stylesheet" type="text/css"/>
	<link href="{{ current_theme.stylesheet_path }}/orbit.css" rel="stylesheet" type="text/css"/>
	<script src="{{ current_theme.javascript_path }}/default.js" type="text/Javascript"></script>
	<script src="{{ current_theme.javascript_path }}/product_hover.js" type="text/Javascript"></script>
</head>
<body>
...
</body>
```

As shown in the example, the tags to insert Stylsheet and JavaScript are almost similar. The first part of the tag "current_theme" finds out the current theme and the second part **.stylesheet_path** and **.javascript_path** finds out the location of the particular stylesheet or Javascript file. This tag is followed by a forward slash "/" and then the actual stylesheet or javascript file name. Likewise, you can attach multiple JavaScript and Stylesheets with your theme.


## 3.3. Inserting Images

You can insert image to any template page including the 'Layout' template. In a normal website you use the *'img'* HTML tag to insert images. In case of 39shop, we also use the 'img' tag but the path to image is specified using this dynamic tag: **{{ current_theme.image_path }}**.

>Let me show you the usage with an example:

```liquid
<img src="{{ current_theme.image_path }}/american-express.png" alt=" logo"/>
```

In this example, 'american-express.png' is the image file stored in the 'images' folder associated with the theme. The tag **{{ current_theme.image_path }}** is used inside the 'img src=".."' Attribute followed by a forward slash '/' and then the name of the image file to be displayed.


## 3.4. Inserting Page Parts

As explained earlier, you can create and use 'Pages Parts' into any template of your 39shops theme. Suppose you created a page part called 'side_navigation' and now you want to display it in your 'Catalog' template. Open the 'Catalogue' template and move your cursor to the HTML tag where you want to insert the page part. Use this tag: **{% include 'side_navigation' %}**. That's it, the page part 'side_navigation' is now included into the catalogue page and category navigation menu will be displayed in this page.

>Here is an example:

```liquid
<html>
	<body>
		<div class="content-left">
		...
		</div>
		<!-- Start right side bar -->
		<div class="content-right">

			{% include "side_navigation" %}

		</div>

		<!-- End right side bar -->
	<body>
</html>
```

The convention to insert a Page Part into any template is :
**{% include "name_of_ page_part" %}**


## 3.5. Rendering 'Layout' in other templates

Earlier we discussed that the 'Layout' is the base template which contain common design elements to be displayed store-wide; for example, header and footer. To allow rest of the templates, use the 'Layout' template, we need to put the following tag into the 'Layout' template.
**{{ content_for_layout }}**

>Here is an example of a typical 'Layout' template:

```liquid
<html>
	<head>
	...
	</head>
	<body>
		<!-- Start header --> 
		<div class="header">
		...
		</div>
		<!-- End header -->
		{{ content_for_layout }}
		<!-- Start footer ---> <div class="footer">
		...
		</div>
		<!-- End footer-->
	<body>
</html>
```

In the example, the *'head'* section has the Stylesheet and JavaScript links. Then in the *'body'* tag, only header and footer sections are rendered. Between the header and footer, we have included **{{ content_for_layout }}**.

This tag does all the job for rest of the template pages. When a template page loads, it looks for the layout and in the layout if **{{ content_for_layout }}**. tag is present, then the template page automatically take up the header and footer from the 'Layout' and displays the rest of the content specific to that page.
