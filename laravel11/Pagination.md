
```php
//Route or Controller 

# slow on large dataset. Known total pages.
$data = ModelName::with("table_name")->paginate(3); //3 per page

# slow on large dataset. faster than paginate(). Unknown total pages.
$data = ModelName::with("table_name")->simplePaginate(3);

# fast on large dataset. Infinite scrolling. Real-time apps.
$data = ModelName::with("table_name")->cursorPaginate(3);

return view('view_name', ['data' => $data]);
```

```php
//view_name.blade.php
<body>
	<div>
		{{$data->links()}}
	</div>
</body>
```