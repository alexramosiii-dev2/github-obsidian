```php
// Route::resource('jobs', JobsController::class); #using resources

//jobs@index
Route::get('/jobs', function () {
	return ('jobs/index', $data) 
});

//jobs@new :also known as 'store'
Route::post('/jobs', function () {
	// validate and authorization check
	return redirect()->route('jobs') 
	->with('status', 'Job created successfully!');
});

//jobs@create
Route::get('/jobs/create', function () {
	return ('jobs/create', $data)
});

//jobs@edit
Route::get('/jobs/{id}/edit', function ($id) {
	return ('jobs/show', $data)
});


//jobs@show
Route::get('/jobs/{id}', function ($id) {
	return ('jobs/show', $data)
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

##### Extra notes
- patch redirects to the show view
- delete redirects to the index view
- delete form is better inside the edit view