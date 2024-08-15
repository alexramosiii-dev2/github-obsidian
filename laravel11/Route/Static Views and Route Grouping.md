#### Static Views
```php
// THIS CAN BE SIMPLIFIED INTO 
Route::get("/", function() {
	return view("index");
})

// =====

Route::view("/", "index");
```

#### Grouping Routes
```php
Route::controller(ControllerName::class)->group(function() {
	Route::get('/jobs', 'index');
	Route::get('/jobs/create', 'create');
	Route::get('/jobs/{job}', 'show');
	Route::get('/jobs/{job}/edit', 'edit');
	
	Route::post('/jobs', 'store');
	Route::patch('/jobs/{job}', 'update');
	Route::delete('/jobs/{job}', 'destroy');
})
```