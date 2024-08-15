
### Routes
- `/routes/web.php` - file, contains all the routing

```php
Route::get('/', function (Illuminate\Http\Request $request) {
	// you can pass in the request as argument
}); 

Route::get('/', function () {
	// or get it using the global helper "request()" function
});
```

```php
Route::get('/', function () {
	$view_data = array("foo" => "bar");

	return view('about'); //render a view only
    return view('about', $view_data); //render a view with data
    return ["foo" => "bar"]; //json for api
    return "Hello, World"; //plain text
});
//dynamic routes
Route::get('/jobs/{id}', function ($id) {
	dd($id)//dump and die
});


```




