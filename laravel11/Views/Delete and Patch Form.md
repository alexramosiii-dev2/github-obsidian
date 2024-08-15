##### Sending a DELETE request
```html
<form method="POST" action="#">
	@csrf
	@method("DELETE")
</form>
```
##### Sending a PATCH request
```html
<form method="POST" action="#">
	@csrf
	@method("PATCH")
</form>
```
##### Sending a form using a external button
```html
<button form="delete-form">Delete</button>
<form id="delete-form" method="POST" action="#" class="hidden">
	@csrf
	@method("PATCH")
</form>
```