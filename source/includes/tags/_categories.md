## 3.8. Categories

From your eComNation store administration, you can assign products to one or more categories. This allows the shopper to click on categories and get desired products quickly while they are browsing through the store front.

>Here is the code example that displays list of categories:

```liquid
<ul>
{% for category in store.categories %}
<li><a href="{{ category.url }}">{{ category.name }}</a></li>
{% endfor %}
</ul>
```

> Showing Featured Categories

```liquid
<ul>
{% for category in store.featured_categories %}
<li><a href="{{ category.url }}">{{ category.name }}</a></li>
{% endfor %}
</ul>
```


**Categories link with active category**

In order to provide a better user experience, sometimes active category needs to be highlight using a difference CSS. In the following example, we are using a special 'for loop' to display an active category. In this example, we are assuming that a css class called 'active' is already available.

```liquid
<ul>
{% for category in store.categories %}
{% if store.active_category.name == category.name %}
{% assign active_class = "active" %} {% else %}
{% assign active_class = "" %} {% endif %}
<li><a href="{{ category.url }}" class={{ active_class }}>{{ category.name
}}</a></li>
{% endfor %}
</ul>
```

In this example, we are using the already known for loop for categories. However, the interesting part of the code begins from second line. Here we are using an {%if...%} {%else%} {%endif %} block to tell the system which class to apply when a particular category is active.
