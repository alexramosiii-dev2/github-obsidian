## Artisan commands
`php artisan make:migration` - generate a migration file
`php artisan migrate` - run 'down' migrations
`php artisan rollback` - revert migrations.
`php artisan migrate:fresh` - drop tables and re-run migrations
`php artisan migrate:status` - see which migration are 'up' or 'down'

```php
use App\Models\House;
use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
	public function up(): void
    {
        Schema::create('table_name', function (Blueprint $table) {
            $table->id(); // auto incrementing primary key
            $table->string('field_name')->nullable();
            $table->string('field_name')->unique;
            $table->string('field_name')->default("default_value");
            $table->timestamps(); // created_at and updated_at

			// extra
            $table->foreignIdFor(House::class)->constrained()->cascadeOnDelete();
	        $table->unsignedBigInteger('foreign_key');
			$table->foreign('foreign_key')->references('id')->on('table_name')->onDelete('cascade');// foreign_key is a reference to the table_name
		
            $table->increments('id'); // auto-incrementing integer
            $table->softDeletes(); // soft_delete
            $table->unsignedBigInteger('field_name'); // non negative number
            $table->enum('status', ['active', 'inactive', 'suspended']);
            $table->uuid('id'); // generate a uuid
			$table->json('options');
			$table->integer('total')->storedAs('field_1 + field_2'); // initial
			$table->integer('total')->virtualAs('field_1 + field_2'); // not-stored
        
	        $table->morphs('imageable'); // polymorphic
	        $table->unique(['field_1', 'field_2']); // unique combination of field_1 and field_2
        });
    }

    public function down(): void
    {
        Schema::dropIfExists('table_name');
    }

};
```