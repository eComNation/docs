## 4.12. Edit Customer Details

>  Edit Customer Details:

```html
{% form 'change_customer_details' %}
  {{ form.errors | default_errors }}
  <input type="text" name="address[first_name]" value="{{ form.first_name }}"  required="required" placeholder="First Name"/>
  <input type="text" name="address[last_name]" value="{{ form.last_name }}" required="required" placeholder="Last Name" />
  <input type="text" name="address[phone]" value="{{ form.phone }}"  required="required" placeholder="Phone No."/>
  <input type="text" name="address[address1]"  value="{{ form.address1 }}" required="required" placeholder="ADDRESS LINE 1" />
  <input type="text" name="address[address2]" value="{{ form.address2 }}" placeholder="ADDRESS LINE 2"/>
  <select name="address[country_id]" data-default="{{form.country_id}}" id="address_country_id" required="required">{% countries_for_select %}</select>
  <div  id="address_state">
  {% if form.country_id %}
    {% if form.country.has_states %}
      <select name="address[state_id]" data-default="{{form.state_id}}" id="address_state_id">
      <option>Select State/Province</option>
      </select>
    {% else %}
      <input type="text" id="address_state_name" name="address[state_name]" value="{{form.state_name }}"/>
    {% endif %}
  {% endif %}
  <input type="text" name="address[city]" value="{{ form.city }}" required="required" placeholder="CITY"/>
  <input type="text" name="address[zipcode]" value="{{ form.zipcode }}" required="required" placeholder="ZIP/POSTAL"/>
  <input type="submit" value="Update">
{% endform %}
```

```js
$(document).ready(function () {
  default_state_id = $("#address_state_id").data('default');
  if(typeof(default_state_id) == 'undefined')
    default_state_id = '';
  else
    default_state_id = default_state_id.toString();

  var country_dropdown = $('#address_country_id');
  country_dropdown.val(country_dropdown.data('default'));
  if($("#address_state_name").length == 0 )
		get_states_for_country(country_dropdown.val());

	$('#address_country_id').change(function () {
	  get_states_for_country($(this).val());
	});
});

var get_states_for_country = function(countryid) {
  if(countryid == '') {
    $('#address_state').html('');
    return;
  }
  var dropdown = $('<select name="address[state_id]" id="address_state_id">');
  var blank = $('<option>').attr({value: ""}).html("Select State/Province");
  dropdown.append(blank);
  $.ajax({
    data: 'country_id=' + countryid,
    type: 'get',
    dataType: 'json',
    url: '/checkouts/states_for_country',
    success: function (data, textStatus, jqXHR) {
      var state_ids = []
      if (data != "") {
        $.each(data, function (index, value) {
            var option = $('<option>').attr({value: value.id}).html(value.name);
            state_ids.push(value.id)
            dropdown.append(option);
        });
        $('#address_state').html("");
        $('#address_state').append(dropdown);
        if(default_state_id != '' && $.inArray(default_state_id, state_ids))
          dropdown.val(default_state_id);
      }
      else
      $('#address_state').html("<input type='text' name='address[state_name]' value='' placeholder='STATE/PROVINCE'>");
    }
  })
}
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
			<td>Starting tag for Change Customer address</td>
			<td>{% form 'change_customer_details' %}</td>
		</tr>
		<tr>
			<td>End tag for Multiple addresses</td>
			<td>{% endform %}</td>
		</tr>
		<tr>
			<td>Form Validation</td>
			<td>{{ form.errors | default_errors }}</td>
		</tr>
		<tr>
			<td>Customer First name</td>
			<td>name="address[first_name]"  <br>	value="{{ form.first_name }}" </td>
		</tr>
		<tr>
			<td>Customer Last name</td>
			<td>name="address[last_name]" <br>  value="{{ form.last_name }}"</td>
		</tr>
		<tr>
			<td>Customer Phone number</td>
			<td>name="address[phone]" <br> value="{{ form.phone }}" </td>
		</tr>
		<tr>
			<td>Customer Address1</td>
			<td>name="address[address1]" <br> value="{{ form.address1 }}"</td>
		</tr>
		<tr>
			<td>Customer Address2</td>
			<td>name="address[address2]" <br> value="{{ form.address2 }}"</td>
		</tr>
		<tr>
			<td>Customer city</td>
			<td>name="address[city]" <br> value="{{ form.city }}"</td>
		</tr>
		<tr>
			<td>Customer zipcode</td>
			<td>name="address[zipcode]" <br> value="{{ form.zipcode }}"</td>
		</tr>
	</tbody>
</table>