# laravel-informix
This package provides an informix query and queue driver for the laravel framework.

# Installation

## Dependencies
- Laravel 5.1 or higher
- a working informix PDO driver ;) (pdo_informix support)

## Installation

**1.** Require the package in your `composer.json`

```json
{
    "require": {
        "fhenne/laravel-informix": "^0.1.0"
    }
}
```

**2.** Then install it with `composer install` or `composer update`

**3.** Add the service provider to the `providers` array in `config/app.php`

```php
fhenne\Informix\InformixServiceProvider,
```

**4.** After that you can configure a connection in `config/database.php` and `.env`

```php
...
'informix' => [
    'driver'   => 'informix',
    'host'     => env('DB_HOST', 'localhost'),
    'port'     => env('DB_PORT'),
    'database' => env('DB_DATABASE', 'forge'),
    'username' => env('DB_USERNAME', 'forge'),
    'password' => env('DB_PASSWORD', ''),
    'server'   => env('DB_SERVER'),
    'protocol' => env('DB_PROTOCOL'), # optional
],
...
```

# Usage

## Use `informix` as default driver

edit your `.env` file like this

```
DB_CONNECTION = informix
```

or change the `default` parameter in `config/database.php` manually

```php
'default' => 'informix', 
```

## Use `informix` only for specific queries or models

### `DB`-Query

`DB::connection('informix')->table('xyz')->...`

### Eloquent model

```php
namespace App;

use Illuminate\Database\Eloquent\Model;

class Xyz extends Model{
	
	protected $connection = 'informix';
	protected $table = 'xyz';
	...

}
```
Now you can use this model as usual `App\Xyz::all()`

