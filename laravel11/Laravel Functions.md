- `abort( 404 | [error_code])` - redirects to 404 page.
- `request()` - returns request object.

## Migration
`php artisan make:migration` - generate a migration file
`php artisan migrate` - run 'down' migrations
`php artisan rollback` - revert migrations.
`php artisan migrate:fresh` - drop tables and re-run migrations
`php artisan migrate:status` - see which migration are 'up' or 'down'

```php
//migration file example
use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    public function up()
    {
        Schema::create('table_name', function (Blueprint $table) {
            $table->string('field_name');
            $table->string('field_name')->unique();
	        $table->text('field_name');
            
            $table->integer('field_name');
            $table->tinyInteger('field_name');
            $table->bigInteger('field_name');
            $table->float('field_name');
            
            $table->boolean('field_name');
            
	        $table->id();
            $table->foreignId('field_name')->nullable()->index();
            
	        $table->json('field_name');
            $table->uuid('field_name');
        });
    }

    public function down()
    {
        Schema::dropIfExists('table_name');
    }
}
```