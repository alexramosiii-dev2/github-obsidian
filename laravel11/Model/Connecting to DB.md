#### To configure connection, edit the `config/database.php`


#### 1. SQL - To set the details edit the `.env` file

```php

// sqlite - default, mariadb, postgresql, microsoft sql service
	DB_CONNECTION=sqlite | mysql | mariadb | pgsql | sqlsrv
	# DB_HOST=127.0.0.1
	# DB_PORT=3306
	# DB_DATABASE=laravel
	# DB_USERNAME=root
	# DB_PASSWORD=
```

#### 2. NO-SQL - To setup MongoDB
- PHP natively doesn't support MongoDB, so does Laravel. You need the PHP MongoDB Extension to use MongoDB as a database for Laravel. This acts as a driver to communicate with MongoDB

##### - PHP MongoDB Extension Installation
- download the driver here https://pecl.php.net/package/mongodb
- copy the extracted `php_mongodb.dll` to the `C:php8.x/ext` directory.
- update your `php.ini` in your PHP directory to include `extension=php_mongodb.dll`
- restart web-server and verify installation `php -m | findstr mongodb` or use `phpinfo()`.
-
##### - Install `jenssegers/mongodb` package
- `composer require jenssegers/mongodb` 
- NOTE:
	- You can still use Laravel migrations to manage your MongoDB collections, though the schema options are more limited compared to SQL databases:
		- `php artisan migrate`
	- However, MongoDB’s dynamic schema might make migrations less necessary depending on your use case.
##### - Configure your connections
```php
// config/database.php
'connections' => [
    'mongodb' => [
        'driver' => 'mongodb',
        'host' => env('DB_HOST', '127.0.0.1'),
        'port' => env('DB_PORT', 27017),
        'database' => env('DB_DATABASE'),
        'username' => env('DB_USERNAME'),
        'password' => env('DB_PASSWORD'),
        'options' => [
            'database' => env('DB_AUTHENTICATION_DATABASE', 'admin'), // Required if you are using MongoDB with authentication
        ],
    ],
],
```

```php
// .env file
DB_CONNECTION=mongodb
DB_HOST=127.0.0.1
//DB_HOST=cluster0-shard-00-00.abcde.mongodb.net # for atlas
DB_PORT=27017
DB_DATABASE=your_database_name
DB_USERNAME=your_username
DB_PASSWORD=your_password
```
##### - Eloquent with MongoDB
```php
use Jenssegers\Mongodb\Eloquent\Model as Eloquent;

class User extends Eloquent
{
    // The name of the MongoDB collection that this model represents.
    protected $collection = 'users';
	$users = User::all();
	// More complex queries
	$users = DB::connection('mongodb')->collection('users')->get();
}
```