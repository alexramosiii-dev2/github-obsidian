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
- `request()->is("/")` //
