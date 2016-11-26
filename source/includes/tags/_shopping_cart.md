## 3.10. Shopping Cart

With every eComNation theme, there is a default template called 'cart.liquid'. The 'cart.liquid' template is used to render the items added to shopping cart. Morover in this page user can modify quantity and proceed to checkout. Lets look at what goes into the cart.liquid template one by one.

All dynamic tags of shopping cart page are within the *'form'* tag which is a standard HTML tag.

>Here is form action:

```liquid
<form action="/cart/update" method="post" id="cart">
---- shopping cart dynamic tags in this area ----
</form>
```

As you can see, the *'form'* tag does nothing special except accepting the 'post' method based on the 'cart id'. This is a standard code and it is a pre-requisite for the shopping cart page to function properly.

Now, let's take a look at how we can render the items added to the shopping cart.


Since there can be multiple items added to a cart, we will use the 'for loop' to render to loop items added to the cart and render in our view:

```liquid
<table>
{% for item in cart.items %}
<tr>
<!-- loop each item in a row -->
</tr>
{% endfor %}
</table>
```

<aside class="notice">
Note:- For the sake of this example, we have used table structure, but you can also used 'div' based structure for your design.
</aside>

Within this for loop, for each item that is rendered, we need to display following elements:

1. Item name and link to product description
2. Unit price of each item
3. Quantity input so that user can modify quantity
4. Amount for that items i.e. quantity multiplied by unit price
5. Check box to remove one or more items

>Let's see how each of these elements is rendered using our tags:

```liquid
{% for item in cart.items %}
<tr>
<td><a href="{{ item.product.url }}">{{ item.name }}</a></td>
<td><input type="text" size="2" value="{{ item.quantity }}" name="item_quantity_{{ item.id }}" id="item_quantity_{{ item.id }}" /></td>
<td>{{ item.unit_price | money: store }}</td>
<td>{{ item.price | money: store }}</td>
<td><input type="checkbox" value="true" name="item_check_{{ item.id }}"
id="item_check_{{ item.id }}"></td>
</tr>
{% endfor %}
```

In the above mentioned code, we have rendered all of the elements related to a product (which is added to shopping cart) in table column *'td'*. This five columns will be loop for every row *'tr'*.

> Here is an explanation of these tags:

```liquid
Product name with link to product detail page
<a href="{{ item.product.url }}"> {{ item.name }}</a>

Input field that accepts quantity for each item	
<input type="text" value="{{item.quantity }}"	name="item_quantity_{{ item.id }}" id="item_quantity_{{ item.id }}" />

Unit rate of each item
{{ item.unit_price | money: store }}
	
Unit rate multiplied by quantity entered i.e. today amount for each item
{{ item.price | money: store }}
	
Check box associated with each item to remove item from cart
<input type="checkbox" value="true" name="item_check_{{ item.id }}" id="item_check_{{ item.id }}">
```
	
>Finally, we need the action buttons which will allow users to either update cart, checkout or continue shopping.

```liquid
<a href="/products">Continue Shopping</a>
<button name="commit" value="Update cart" >Update cart</button> {% if store.payment_enabled? %}
<button name="commit" value="Checkout">Checkout</button> {% endif %}
```

In the above code, we simply have an *'a'* tag which takes user to the product catalog page. In the next line we have a *'button'* tag with value='update cart' . This action allows user to update quantity if changed for any item added to the cart. And lastly, we have another *'button'* tag to allow user to checkout. Notice the use of {if store.payment_enabled? %} ....
{endif} tag which makes the 'Checkout' button displayed to the user only if at least one payment method is enabled by the store owner.
Shopping cart header

In an online store it is usually preferred to display shopping info across all pages of the site. Usually the shopping info is how many products are added to shopping cart, the total amount of goods added to cart and a link to view the shopping cart page.

>Here is the code:

```liquid
Your cart contains {{ cart.total_items }} items
You have items worth {{ cart.total_amount | money: store }} in your cart
<a href="/cart">View Cart</a>
```

The above code is self-explainatory. Tag in the first line displayed the total number of items added to the shopping cart. In the second line, the {{cart.total_amount | money : store }} tag displays the total worth of goods added to the shopping cart. In third line, we simply provide a link to the 'cart' template to view the cart content.

<aside class="notice">
Note: Usually the shopping cart header is included in the 'Layout' template so that it remains consistent across the store front.
</aside>
