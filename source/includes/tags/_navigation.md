## 3.6. Navigation Menus

39shops allows user to create any number of navigation menus and insert them into one or more template pages as needed.

### 3.6.1. Creating navigation menu

To create a navigation menu, log-in to your store administration area and under the 'Design and Navigation' tab, click on 'Navigation menus' option.

You will see that two navigation menu's 'Main' and 'Footer' are already created and a couple of links are also added to these. These are default navigation menus provided by 39shops and cannot be removed. For each of these navigation menus, you can add/remove links.

You can also add new navigation menus apart from main and footer by clicking on the link 'Add navigation menu' located on the top of the right side bar.

### 3.6.2 Navigation menu Tag

The navigation menu that you create can be easily added to any template pages using the navigation menu title.

> Here is the code:

```liquid
{% for link in store.main_navigation_links %}
<a href="{{ link.url }}" target="{{ link.url_target }}">{{ link.title }}</a>
{% endfor %}
```

In the first line, we have used the 'for' loop **{% for link in .....%}** to render each link added to a navigation menu. But there is more to this tag, lets take a look at the tag closely:

**{% for link in store.main_navigation_links %}**

Apart from the standard 'for' loop convention, we have the store.main_navigation_link argument in which really does the trick. In that
argument 'main_navigation' is the name of the navigation menu available in the 'Navigation menus' section of your store administration.

Likewise, suppose user has added a navigation menu called 'Top Categories', then the navigation menu tag will be something like this :

**{% for link in store.top_categories_link %}**

Notice how we used 'top_categories' as the argument instead of

'main_navigation'.

The second line of navigation menu tag looks familiar to us. The link tag {{ link.url }} links to the navigation menu item configured while adding the link, target tag {{ link.url_target }} takes the target (open in same browser window or open in a new browser window) selected while adding the link and finally {{ link.title }} tag displays the name of the link saved while adding the link to navigation menu.


Finally the navigation menu tags for loop ends with {% endfor %}, which is a standard convention to end a for loop.

Here is the standard code for footer main navigation and footer navigation menus which comes default with each 39shops store-front.

> Main navigation menu

```liquid
{% for link in store.main_navigation_links %}
<a href="{{ link.url }}" target="{{ link.url_target }}">{{ link.title }}</a>
{% endfor %}
```

> Footer navigation menu

```liquid
{% for link in store.footer_navigation_links %}
<a href="{{ link.url }}" target="{{ link.url_target }}">{{ link.title }}</a>
{% endfor %}
```
