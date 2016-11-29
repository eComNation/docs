## 4.9. Forgot password form.

> Forgot password form syntax :

```html
{% form 'recover_customer_password' %}
  {{ form.errors | default_errors }}
  <input type="email" name="email" required="required" placeholder="Email Address"/>
 	<input type="submit" value="Submit" class="fr-btn button">
{% endform %}
```

<table>
	<thead>
		<td>Description</td>
		<td>Tags / Parameter</td>
	</thead>
	<tbody>
		<tr>
			<td>Starting tag for forgot password form</td>
			<td>{% form 'recover_customer_password' %}</td>
		</tr>
		<tr>
			<td>End tag for forgot password form</td>
			<td>{% endform %}</td>
		</tr>
		<tr>
			<td>Form validation</td>
			<td>{{ form.errors | default_errors }}</td>
		</tr>
		<tr>
			<td>Email Address</td>
			<td>name="email"</td>
		</tr>
		
	</tbody>
</table>