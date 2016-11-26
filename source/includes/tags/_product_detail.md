## 3.9. Product Detail

eComNation provides template called 'product_detail.liquid'. This template is used to render detailed product information.

**Displaying product photos**

In the product detail page, one of the major elements is displaying multiple product images and also allowing user to see a bigger product image.

Let's begin with the code that displays multiple product thumbnails and a larger image when click on the thumb image. 

>Here is the code:

```liquid
{% for product_image in product.product_images %}
<li>
<a href="{{ product_image | img_url: 'medium'}}">
{{ product_image | images_tag: 'thumb'}}</a>
</li>
{% endfor %}
```


Next, we always need to display a default big image of the product. Here is the code which does the job:

**{{product | product_img_tag: 'medium' }}**


If we further need to show even a larger version of the image, here is the code:

**{{product | product_img_tag: 'large' }}**


Now, if you want that clickng on the big image should open the large image, you can link the big image to the large image in the following way:

> Here is the code

```liquid
<a href="{{product | product_img_url: 'large' }}">{{product | product_img_tag:'medium' }}</a>
```

<aside class="notice">
Note: You can use a variety of Javascript and Jquery functions to display product images innovatively in the product detail page. Refer to our public themes to see example usage.
</aside>

Displaying product information

Here are the simple tags you can use to show detailed product information:

{{ product.name }}	Show product title
{{ product.description }}	Show detailed description
{{ product.price | money: store }}	Show product price
	

**Adding product to cart**

>Here is the code which allows user to specify quantity and add the product to cart:

```liquid
<form method="post" action="/cart/add" >
<input type="hidden" id="product_id" name="product_id" value="{{ product.id
}}" />
<input type="text" value="1" size="2" name="quantity" id="quantity" class="textinput">
<input type="submit" name="button" id="button" value="Add to cart" /> </form>
```

In the above code, since we are collecting user data, we certainly need to have a *'form'* tag with a 'post' method.
