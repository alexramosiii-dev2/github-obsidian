### Client-Side

```php
<input type="text" name="first_name" required> //basic

// for advance validation, use javascript
```

### Server-Side
[All laravel validation rules](https://laravel.com/docs/11.x/validation#available-validation-rules)
```php
function index(request $request) {
	// at error, in exit the controller and go back with an $errors object
	$validated_data = $request->validate([
		'first_name' => ['required', 'min:3', 'max:15'],
		'email' => ['email', 'unique:table_name, field_name'],
		'password' => ['confirmed'] // name=password_confirmation
		'phone_number' => ['digits:10'],
		
		'age' => ['numeric']
		'description' => ['string']
		'is_active' => ['boolean']
		'birthday' => ['date']
		'profile_picture' => ['image'],
		'avatar' => ['file'],
		'status' => ['array']
		'website' => ['url','sometimes'] // validate if field is present
		'document' => ['mimes:pdf,doc,docx']
		'status' => ['in:active, inactive, pending'] // one of the options
		
		'category' => ['exists:table_name, field_name']
		'username' => ['regex:/^[a-zA-Z0-9_]+$/'],
	])
}
```

##### Displaying Errors
```php
// once each time
@error->('first_name')
	<p> {{ $message }} <p>
@enderror

// all at once
@if($errors)->any()
	<ul>
		@foreach($errors->all() as $error)
			<li> {{ $error }} </li>
		@endforeach
	</ul>
@endif
```
### Database-side
- check [Migration](Migration.md)
