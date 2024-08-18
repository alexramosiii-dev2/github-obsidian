
```html
<body>
	@csrf
	@method("PATCH" || "DESTROY") //optional
	<!-- FIRST NAME -->
	<div>
		<label for="first_name"> First Name </label>
		<input id="first_name" name="first_name" type="text"/>
		@error('first_name')
			<p>{{ $message }}</p>
		@enderror
	</div>
	<!-- LAST NAME -->
	<div>
		<label for="last_name"> Last Name </label>
		<input id="last_name" name="last_name" type="text"/>
		@error('last_name')
			<p>{{ $message }}</p>
		@enderror
	</div>
	<!-- EMAIL -->
	<div>
		<label for="email"> Email </label>
		<input id="email" name="email" type="email"/>
		@error('email')
			<p>{{ $message }}</p>
		@enderror
	</div>
	<!-- PASSWORD -->
	<div>
		<label for="password"> Password </label>
		<input id="password" name="password" type="password"/>
		@error('password')
			<p>{{ $message }}</p>
		@enderror
	</div>
	<!-- PASSWORD CONFIRM -->
	<div>
		<label for="password_confirmation"> Confirm Password </label>
		<input id="password_confirmation" type="password_confirmation"/>
		@error('password_confirmation')
			<p>{{ $message }}</p>
		@enderror
	</div>
	<!-- SUBMIT BUTTON -->
	<input type="submit" value="Submit"/>
	<button type="submit"> Submit </button>
</body>
```