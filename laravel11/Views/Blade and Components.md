### Views
- `/resources/views/` - directory, contains all views
#### Request Function
- `request()->is("/")` - checks what is the current uri
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
	<!--$attributes is used inside a tag-->
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

<x-componentName /> <!-- self-closing --> 

```

#### Attributes vs Props

##### - Attributes are any additional parameters inside a html tag
```php
//index.blade.php
<x-component id="" class="" href=" " style=" " title=" ">
	This is the slot value
</x-component>

//component.blade.php
<a {{ $attributes }} > {{ $slot }} </a>
<a {{ $attributes->merge(['class'=> " "])}} > </a>
```

##### - Props are used to pass data to the components
```php
//index.blade.php
<x-component id="" class="" href=" " style=" " title=" " active=" " random=" ">
	This is the slot value
</x-component>

//component.blade.php
@props(['active', 'random']) // extract props from the $attributes array
@props(['active' => false, 'random' => 'true']) // with default

<a {{ $active }} > {{ $slot }} </a>
<a {{ $random }} > </a>
```
##### - Passing an expression with props
```php
//index.blade.php

// using ":" semicolon would treat the value as expression
<x-component :active=" " :sum="1+1">
	This is the slot value
</x-component>

//component.blade.php
@props(['active', 'sum']) // this is now optional
@props(['active' => false]) // needed if defaults are set

<a {{ $active }} > {{ $slot }} </a>
<a {{ $random }} > </a>
<a> {{ $sum }} </a> // would output 2
```