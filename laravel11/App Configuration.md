- `/app/Providers/AppServieProvider.php `
	- configure your vendor and app setting through this file.
- `php artisan vendor:publish`
	- make a copy of packages asset to the app for manual configuration
``` php
namespace App\Providers;
use Illuminate\Support\ServiceProvider;

class AppServiceProvider extends ServiceProvider
{
    // Register any application services.
    public function register(): void
    {
        //
    }
    //triggers after all project depencies are loaded
    public function boot(): void
    {
        Illuminate\Database\Eloquent\Model::preventLazyLoading(); //disable lazylading
        Illuminate\Pagination\Paginator::useBootstrapFive(); // diff pagination template
    }
}
```
