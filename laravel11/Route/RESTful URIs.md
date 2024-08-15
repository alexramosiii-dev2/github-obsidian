##### Extra notes
- patch redirects to the show view
- delete redirects to the index view
- delete form is better inside the edit view
- check for route model binding


#### **`php artisan route:list --except-vendor'**

```php
Route::view("/", "index"); // for static pages

//using resources, seconda param is for route model binding
Route::resource('jobs', JobsController::class); #using resources

//jobs@index page
Route::get('/jobs', function () {
	return ('jobs/index', $data) 
});

//jobs@create page
Route::get('/jobs/create', function () {
	return ('jobs.create', $data)
});

//jobs@edit page
Route::get('/jobs/{id}/edit', function ($id) {
	return ('jobs.edit', $data)
});

//jobs@show page
Route::get('/jobs/{id}', function ($id) {
	return ('jobs.show', $data)
});


//jobs@new :also known as 'store'
Route::post('/jobs', function () {
	// validate and authorization check
	return redirect()->route('jobs') 
	->with('status', 'Job created successfully!');
});

//jobs@update
Route::patch('/jobs/{id}', function ($id) {
	// validate and authorization check
	return redirect("/jobs")
});

//jobs@destroy
Route::delete('/jobs/{id}', function ($id) {
	// validate and authorization check
	return redirect("/jobs")
});
```


#### **`php artisan route:list --except-vendor'**

#### Using Resources
```php
use App\Http\Controllers\ControllerName;

Route::resource('jobs', JobsController::class);
Route::resource('jobs', JobsController::class, [
	'only' => ['index, edit, store'];
]);
```

#### Using Controller
```php
use App\Http\Controllers\ControllerName;

Route::get('/users', [ControllerName::class, 'index']);
Route::get('/users/create', [ControllerName::class, 'create']);
Route::get('/users/{user}/edit', [ControllerName::class, 'edit']);
Route::get('/users/{user}', [ControllerName::class, 'show']);
Route::get('/users', [ControllerName::class, 'store']);
Route::get('/users/{user}', [ControllerName::class, 'update']);
Route::get('/users/{user}', [ControllerName::class, 'destroy']);
```

#### Grouping Controller Routes
```php
use App\Http\Controllers\ControllerName;

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

