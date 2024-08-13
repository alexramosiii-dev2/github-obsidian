
### Routes
- `/routes/web.php` - file, contains all the routing
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


### Views
- `/resources/views/` - directory, contains all views

#### Components Using Blade
- `/resources/views/components/` - directory, contains all reusable blocks of codes
	- `~/components/nav-link.blade.php`
	- `~/components/header.blade.php`
	- `~/components/footer.blade.php`
	- `~/components/accordion.blade.php`
	- `~/components/layout.blade.php` - useful layouts
#### Defining a component
```html
<!-- /resources/views/components/layout.blade.php -->
<body>
	{{ $attributes }} <!-- class="layout" id="layout" -->
	{{ $slot }} <!-- blade's shorthand echo (<?=?>) -->
	{{ $namedSlot }} 
</body>
```

#### Using the component
```html
<!-- /resources/views/home.blade.php -->
<x-layout class="layout" id="layout">
	
	This is value for $slot

	<!-- Named slots, alternative for props/attributes -->
	<x-slot:namedSlot> this is value for $namedSlot</x-slot:namedSlot>
</x-layout>
```

#### Tailwind CSS
- `<script src="https://cdn.tailwindcss.com"></script>`

#### Request Function
- `request()->is("/")` // checks if the request endpoint match the "is(" ")"

#### Props vs Attributes
- attributes are normal html attributes and shows in inspect elements, while props are like attributes but are used as variables for components

- `<a :props_name="1+1"></a>` // using colon before props name would treat the value as expression
- `@props(["props_name"])`  // removes props from attributes showing in inspect element
- `@props(["props_name" => "optional default"])`



### Models
- `/app/Models/` - directory, stores all your model class.
- use

### Controllers
```php
use App\Models\[ModelName]; //importing a model


```