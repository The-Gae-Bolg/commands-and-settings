# Auth API laravel 11

## 1. Install Sanctum

```bash
php artisan install:api
```

## 2. Model User

```php
<?php
use Laravel\Sanctum\HasApiTokens;
use Illuminate\Foundation\Auth\User as Authenticatable;

class User extends Authenticatable
{
  use HasApiTokens, HasFactory, Notifiable;
}
```

## 3. Config Auth

```php
'guards' => [
  'web' => [
    'driver' => 'session',
    'provider' => 'users',
  ],

  'api' => [
    'driver' => 'sanctum',
    'provider' => 'users',
  ],
],
```

## 4. Create Token

```php

use App\Models\User;
use Illuminate\Support\Facades\Hash;

/**
* Send the response after the user was authenticated. *
*
* @param \Illuminate\Http\Request $request
* @return \Illuminate\Http\Response
* */
protected function sendLoginResponse(Request $request)
{
  $request->session()->regenerate();
  $this->clearLoginAttempts($request);
  $user = $this->guard()->user();
  $token = $request->user()->createToken('authToken')->plainTextToken;

  return response()->json(['user' => $user, 'token' => $token,]);
}
```

## 5. Save Token

```javascript
.then(response => {
  const token = response.token;
  localStorage.setItem('authToken', token);
  window.location.href = '/';
})
```

## 6. Get Token and Send

```javascript
axios.post('/api/users', {}, { 
  headers: { 
    'Authorization': `Bearer ${localStorage.getItem('authToken')}`,
    'Accept': 'application/json'  
  } 
})
```

## 8. Use middleware

```php
Route::middleware('auth:sanctum')->get('/user', function (Request $request) {
  return $request->user();
});
```
