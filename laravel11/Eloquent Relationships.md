- **One-to-One**
- **One-to-Many**
- **Many-to-Many** - using pivot tables
- **Has One Through**
- **Has Many Through**
- **Polymorphic Relations**
- **Many-to-Many Polymorphic Relations**

# SQL Basic
### 1. One to One
- 1 author = 1 book
```php
	//class Author extends Model
	public function book()
	{
		// App\Models\Author::first()->book;
		return $this->hasOne(Book::class);
	}

	//class Book extends Model
    public function author()
    {
		// App\Models\Book::first()->author;
        return $this->belongsTo(Author::class);
    }
```

### 2. One-to-Many
- 1 author = 2-10 books
```php
    //class Author extends Model
	public function books()
	{
		// App\Models\Author::first()->books[0];
		// App\Models\Author::first()->books->first();
		return $this->hasMany(Book::class);
	}

	//class Book extends Model
    public function author()
    {
		// App\Models\Book::first()->author;
        return $this->belongsTo(Author::class);
    }
```

### 3. Many-to-Many
- bridge/junction/pivot table is needed to be created.
- Naming: singularModel1_singularModel2 ex. author_book. NOTE: THIS IS MANDATED
- If you can't follow the naming convention
	- `belongsToMany(Book::class, 'pivot_name', 'foreign_name', 'related_name');`
- 2-10 author = 2-10 book
- `App\Models\Author::first()->attach($bookID)`
- `App\Models\Book::first()->attach(App\Models\Author::find($bookID))`
- `App\Models\Book::first()->sync([$author_id1, $author_id2])`
	- Attach multiple authors (this will replace existing authors)
- `App\Models\Book::saveMany()->sync([$author_id1, $author_id2])`
	- Attach multiple authors without replacing existing ones

```php
	//class Author extends Model
	public function books()
	{
		// App\Models\Author::first()->books[0];
		// App\Models\Author::first()->books->first();
		return $this->belongsToMany(Book::class);
//belongsToMany(Book::class, foreignPivotKey: author_id, relatedPivotKey: book_id);
	}

	//class Book extends Model
    public function authors()
    {
		// App\Models\Author::first()->authors[0];
		// App\Models\Author::first()->authors->first();
        return $this->belongsToMany(Author::class);
        return $this->belongsToMany(Author::class);
//belongsToMany(Book::class, foreignPivotKey: book_id, relatedPivotKey: author_id);
// foreignPivotKey - column name of this model in the pivot table 
// relatedPivotKey - column name of the model you try to access.
    }
    
	//Migration for the junction table
	Schema::create('authors_books', function (Blueprint $table) {
	    $table->unsignedBigInteger('author_id');
	    $table->foreign('author_id')
	    ->references('id')
	    ->on('author')
	    ->onDelete('cascade');
	    
	    $table->unsignedBigInteger('book_id');
	    $table->foreign('book_id')
	    ->references('id')
	    ->on('book')
	    ->onDelete('cascade');
	});
```


# ORM Specific
### 1. Has one Through
- 1 job = 1 recruiter = 1 applicant
- Job <- Recruiter <- Applicant
```php
	//class Job extends Model
	public function applicant()
	{
		// App\Models\Job::first()->applicant;
		return $this->hasOneThrough(Applicant::class, Recruiter::class);
	}
	//class Recruiter extends Model
	public function job()
	{
		// App\Models\Recruiter::first()->job;
		return $this->belongsTo(Job::class);
	}
	public function applicant()
	{
		// App\Models\Recruiter::first()->applicant;
		return $this->hasOne(Applicant::class);
	}


	//class Applicant extends Model
    public function author()
    {
		// App\Models\Applicant::first()->recruiter;
        return $this->belongsTo(Recruiter::class);
    }
```

### 2. Has Many Through
- 1 job = 1 recruiter = 2-10 applicant
- Job <- Recruiter <- Applicant
```php
	//class Job extends Model
	public function applicant()
	{
		// App\Models\Job::first()->applicant;
		return $this->hasManyThrough(Applicant::class, Recruiter::class);
	}
	//class Recruiter extends Model
	public function job()
	{
		// App\Models\Recruiter::first()->job;
		return $this->belongsTo(Job::class);
	}
	public function applicant()
	{
		// App\Models\Recruiter::first()->applicant;
		return $this->hasOne(Applicant::class);
	}


	//class Applicant extends Model
    public function author()
    {
		// App\Models\Applicant::first()->recruiter;
        return $this->belongsTo(Recruiter::class);
    }
```

### 3. Polymorphic Relations
- Bahala kana sa buhay mo.
### 4. Many to Many Polymorphic Relations
- Bahala kana sa buhay mo.
