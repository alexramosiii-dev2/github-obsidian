```php

/***** WITHOUT ROUTE MODEL BINDING *****/
Route::get('/jobs/{id}', function ($id) {
	$job = Job::find($id);
	return ('jobs.show', ['job' => $job])
});

/***** USING ROUTE MODEL BINDING *****/

// 1. wildcard '{job}' and param '$job' should be same name.
Route::get('/jobs/{job}', functtabion (App\Model\Job $job) {
	return ('jobs.show', ['job' => $job])
});

// 2. get 'post' record with matching 'slug'
Route::get('/posts/{post:slug}', function (App\Model\Post $post) {
	return ('post.show', ['post' => $post])
});
```