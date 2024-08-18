#### Static Views
```php
Route::get("/", function() {
	return view("index");
})

// same thing as above
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

#### Route Resources
```php
Route::resource('jobs', JobsController::class); #using resources
```