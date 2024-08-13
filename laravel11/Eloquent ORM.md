`php artisan make:model ModeName -m` - create model and migration
`php atisan tinker` - CLI to interact with app database.

NOTE:
	- Models are singular
	- Tables plural
	- Controllers are plural
```php
namespace App\Models; //VERY IMPORTANT

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class User extends Model {
    use HasFactory; //use trait Hasfactory
    
	protected $table = 'table_reference' // if table and class have diff name.

	protected $fillable = ['name', 'age']; // would only accept this property
}
```

```php
use App\Models\User; //load model

class Users extends Controller {
	public function index($id) {
		$users = User::all();
		$users = User::create([
			'name' => '', 'age' => 0, 'height' => '5\'6"'
		]); // ignores passed 'height'

		$user = User::find($id);

// ** CRUD **
// User::create(['field1' => 'val', 'field2' => 'val2'])
// User::where('field', 'value')->update(['field' => 'new value']);
// User::where('field', 'value')->delete();

// User::first();
// User::count();

// User::where('field', 'value')->get();
// User::where('field', 'operator','value')->get();
// User::where('field', 'value')->orWhere('field', 'operator', 'value')->get();
// User::orderBy('field', 'desc/asc')->get();
// User::limit(10)->get();
// User::pluck('field'); // all values for single field

// User::where('field', 'value')->exists();
// User::where('field', 'value')->doesntExist();


// ** JOINING **	
// User::has('table_name')->get();
// User::with('table_name')->get(); //eager loading. performance
// User::join('table_name', 'users.id', '=', 'posts.user_id')->get();

	}
}
```

### Install Laravel Debugger Bar
- `composer require barryvdh/laravel-debugbar --dev`
