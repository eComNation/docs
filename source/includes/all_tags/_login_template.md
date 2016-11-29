## 4.7. Login form.

> Login form syntax :

```html
{% form 'customer_login' %}
  {{ form.errors | default_errors }}
  {% store_alert_message_tag %}
  <input type="email" name="customer_session[login]" required="required"  placeholder="Email Address" />
  <input type="password" name="customer_session[password]" required="required"  placeholder="Password" />
  <a href="/customer/forgot_password">Forgot Password?</a>
  <input type="submit" value="Sign in" >
{% endform %}
```

<table>
	<thead>
		<td>Description</td>
		<td>Tags / Parameter</td>
	</thead>
	<tbody>
		<tr>
			<td>Starting tag for Customer login form</td>
			<td>{% form 'customer_login' %}</td>
		</tr>
		<tr>
			<td>Form validation</td>
			<td>{{ form.errors | default_errors }}</td>
		</tr>
		<tr>
			<td>End tag for Customer login form</td>
			<td>{% endform %}</td>
		</tr>
		<tr>
			<td>Email Address</td>
			<td>name="customer_session[login]"</td>
		</tr>
		<tr>
			<td>Password</td>
			<td>name="customer_session[password]"</td>
		</tr>
	</tbody>
</table>