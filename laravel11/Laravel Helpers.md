##### Routes, Models, and Controllers
``` php
// Return a view instance with optional data.
view('welcome', ['name' => 'John'])
// Generate a URL for a named route with optional parameters. For redirects
route('user.profile', ['id' => 1])
// Retrieve input data from the current request.
request()->input('name')
// Access a value from the session.
session()->get('key')
// Hash a password using the bcrypt algorithm.
bcrypt('password')
// Retrieve the currently authenticated user.
auth()->user()
// Abort the current request with a given HTTP status code. Redirects
abort(404)

// Dump the given variable(s) and terminate the script execution (for debugging).
dd($variable)
// Dump the given variable(s) without terminating script execution (for debugging).
dump($variable)


// Generate a fully qualified URL to the specified path.
url('/path/to/page')
// Create a redirect response to a named route.
redirect()->route('home') or redirect('home')
// Generate a URL for an asset located in the `public` directory.
asset('images/logo.png')



// Retrieve a value from the configuration files.
config('app.timezone')
// Create a new JSON response.
response()->json(['key' => 'value'])
// Resolve and return an instance of a class from the service container.
app('SomeClass')


// Access an environment variable from the `.env` file.
env('APP_DEBUG')
// Create a new `Collection` instance from the provided array.
collect([1, 2, 3])
```

##### Useful for views
```php
// Translate a given language line.
trans('messages.welcome')

// Alias for `trans()`, used for easier string translation.
__('messages.welcome')
```
