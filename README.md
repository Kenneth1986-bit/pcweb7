## Steps to run
1. Check ```.env``` that the values are correct for the following <br>
	DB_PORT<br>
	DB_DATABASE<br>
	DB_USERNAME<br>
	DB_PASSWORD<br>

2. Make sure the database on phpmyadmin that the application is connected to is empty
3. Migrate the migrations to the database: <br>```php artisan migrate```
4. Reset the symbolic link from the public folder: in your terminal or powershell:<br>
```php artisan storage:link```
5. Start the server<br>
```php artisan serve```

## Knowned errors
1. ```php artisan migrate``` throws
> Illuminate\Database\QueryException] SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long; max key length is 767 bytes

Solution (this solution has been implemented): 
- In ```app/Providers/AppServiceProvider.php```, add ```use Illuminate\Support\Facades\Schema;``` to the line 1. And add ```Schema::defaultStringLength(191);``` into the boot function definition. 
