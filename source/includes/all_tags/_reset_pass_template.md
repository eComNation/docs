## 4.10. Password Reset form.

>  Password Reset form syntax :

```html
{% form 'reset_customer_password' %}
  {{ form.errors | default_errors }}
  <input type="password" name="customer[password]" required="required" placeholder="Password"/>
  <input type="password" name="customer[password_confirmation]" required="required"  placeholder="Confirm Password"/>
  <input type="submit" value="Reset" >
{% endform %}
```

<table>
	<thead>
		<td>Description</td>
		<td>Tags / Parameter</td>
	</thead>
	<tbody>
		<tr>
			<td>Starting tag for resetting Customer's password form</td>
			<td>{% form 'reset_customer_password' %}</td>
		</tr>
		<tr>
			<td>End tag for resetting Customer's password form</td>
			<td>{% endform %}</td>
		</tr>
		<tr>
			<td>Form Validation</td>
			<td>{{ form.errors | default_errors }}</td>
		</tr>
		<tr>
			<td>Password</td>
			<td>name="customer[password]"</td>
		</tr>
		<tr>
			<td>Confirm Password</td>
			<td>name="customer[password_confirmation]"</td>
		</tr>
	</tbody>
</table>