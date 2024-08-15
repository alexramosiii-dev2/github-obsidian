#### Route
- NOTE: using route model binding
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

#### Controller
- NOTE: using route model binding

#### **`php artisan make:controller ControllerName`**

```php
use App\Models\User

class ControllerName extends Controller
{
	public function index() {}
	public function create() {}
	public function edit(User $user) {}
	public function show(User $user) {}
	
	public function store() {}
	public function update(User $user) {}
	public function destroy(User $user) {}
}
```