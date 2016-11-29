## 4.8. Registration form.

> Registration form syntax :

```html
{% form 'create_customer' %}
  {{ form.errors | default_errors }}
  <input type="text" name="customer[first_name]" required="required" placeholder="First Name"/>
  <input type="text" name="customer[last_name]" required="required" placeholder="Last Name"/>
  <input type="email" name="customer[login]" required="required" placeholder="Email Address" />
  <input type="text" name="customer[phone]" required="required" placeholder="Phone No."/>
  <input type="password" name="customer[password]" required="required" placeholder="Password"/>
  <input type="password" name="customer[password_confirmation]" required="required" placeholder="Password again"/>
  <input  type="submit" value="Register">
{% endform %}

```

<table>
	<thead>
		<td>Description</td>
		<td>Tags / Parameter</td>
	</thead>
	<tbody>
		<tr>
			<td>Starting tag for Create New Customer form</td>
			<td>{% form 'create_customer' %}</td>
		</tr>
		<tr>
			<td>End tag for Create New Customer form</td>
			<td>{% endform %}</td>
		</tr>
		<tr>
			<td>Form validation</td>
			<td>{{ form.errors | default_errors }}</td>
		</tr>
		<tr>
			<td>First Name</td>
			<td>name="customer[first_name]"</td>
		</tr>
		<tr>
			<td>Last Name</td>
			<td>name="customer[last_name]"</td>
		</tr>
		<tr>
			<td>Email Address</td>
			<td>name="customer[login]"</td>
		</tr>
		<tr>
			<td>Phone No.</td>
			<td>name="customer[phone]"</td>
		</tr>
		<tr>
			<td>Password</td>
			<td>name="customer[password]"</td>
		</tr>
		<tr>
			<td>Password again</td>
			<td>name="customer[password_confirmation]"</td>
		</tr>
	</tbody>
</table>