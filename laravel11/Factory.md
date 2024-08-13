Used to create test data and seed your database with fake data during development.

`php artisan make:factory FactoryName`

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