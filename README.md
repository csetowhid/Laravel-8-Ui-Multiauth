# Laravel 8 Multi Authentication With Laravel Ui Package

## Step: 1 Create a New Laravel 8 Application
`composer create-project laravel/laravel laravel-ui-multiauth`

After successfully create a project run some commands to generate default auth.
```
composer require laravel/ui
php artisan ui bootstrap --auth
npm install && npm run dev 
npm run watch
```

## Step: 2 Create a Model and Migration File for Admin
```
php artisan make:model Admin -m
```
Add some code in the admin model

<b>Models / Admin.php</b>
```
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Foundation\Auth\User as Authenticatable;
class Admin extends Authenticatable
{
    use HasFactory;
    protected $guard = 'admin';

    /**
     * The attributes that are mass assignable.
     *
     * @var array
     */
    protected $fillable = [
        'name', 'email', 'password',
    ];

    /**
     * The attributes that should be hidden for arrays.
     *
     * @var array
     */
    protected $hidden = [
        'password', 'remember_token',
    ];
}
```