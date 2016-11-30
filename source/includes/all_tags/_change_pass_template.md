## 4.15. Change Password template tags

>  Change Password form :

```html
{% form 'change_customer_password' %}
  {{ form.errors | default_errors }}
  <input type="password" name="current_password" required="required" placeholder="Old Password"/>
  <input type="password" name="new_password" required="required" placeholder="New Password"/>
  <input type="password" name="confirm_password" required="required" placeholder="Confirm Password" />
  <input type="submit" value="Update" >
{% endform %}
```

<table>
	<thead>
		<tr>
			<th>Description</th>
			<th>Tags / Parameter</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Starting tag for Changing Customer's password form</td>
			<td>{% form 'change_customer_password' %}</td>
		</tr>
		<tr>
			<td>End tag for Changing Customer's password form</td>
			<td>{% endform %}</td>
		</tr>
		<tr>
			<td>Form Validation</td>
			<td>{{ form.errors | default_errors }}</td>
		</tr>
		<tr>
			<td>Old Password</td>
			<td>name="current_password"</td>
		</tr>
		<tr>
			<td>New Password</td>
			<td>name="new_password"</td>
		</tr>
		<tr>
			<td>Confirm Password</td>
			<td>name="confirm_password"</td>
		</tr>
	</tbody>
</table>