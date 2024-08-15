\
### Factory
- Used to scaffold data for development. Useful for QA tests.
- `php artisan make:factory FactoryName`
	- create a factory file
- `php artisan make:model ModelName -mf`
	- create a model with associated migration ( -m ) and factory ( -f )
```php
namespace Database\Factories;

use Illuminate\Database\Eloquent\Factories\Factory;

class FactoryName extends Factory
{
    public function definition(): array
    {
        return [
        // fake is a function that generate fake data.
        // Illuminate\Foundation\helpers // autoloaded
            'model_field' => fake()->name(),
            'model_field' => fake()->unique()->safeEmail(),
      
        ];
    }

    public function unverified(): static
    {
        return $this->state(fn (array $attributes) => [
            'email_verified_at' => null,
        ]);
    }

}
```

### Seeders
- used to trigger factories and database calls.

- `database/seeder/DatabaseSeeder.php`
	- file that contains the seeder file

- `php artisan db:seed`
- `php artisan migrate:fresh --seed`
	- reset database and run seeder file

- `php artisan make:seeder SeederName`
	- create a separate seeder file
	- `php artisan db:seed --class=SeederName`