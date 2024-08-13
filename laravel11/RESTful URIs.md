```php
// Route::resource('jobs', JobsController::class); #using resources

//jobs@index
Route::get('/jobs', function () {
	return ('jobs/index', $data) 
});

//jobs@new
Route::post('/jobs', function () {
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
Route::put('/jobs/{id}', function ($id) {
	return redirect("/jobs")
});

//jobs@destroy
Route::delete('/jobs/{id}', function ($id) {
	return redirect("/jobs")
});
```