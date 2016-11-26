## 3.11. Content Page

The content pages added by user from store administration through the 'Pages' section is rendered in the template called 'page.liquid'.
>Here is the code which displayed the page title and content of a page.

```liquid
<h1>{{ page.title }}</h1>
<p>{{ page.body }} </p>
```
The tags are self-explanatory.
