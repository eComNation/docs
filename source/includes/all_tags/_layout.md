# 4. Tags

## 4.1. Tag Basics eComNation has two types of special operators used to render dynamic content in the HTML templates. They are **Variables** and **Blocks**.

### 4.1.1. Variables
Variables are used to insert dynamic data like product title, product price etc.

> Here is an example of variable:

```liquid
<html> 
	<body> 
	  <p>{{ product.name }}</p> 
	</body> 
</html> 
```