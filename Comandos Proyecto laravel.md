### Comandos.md

# Cambiar la ruta de la carpeta public en app/Providers/AppServiceProvider.php dentro de la funcion register
- [x] `app()->usePublicPath(realpath(base_path().'/public_html'));`

# Cambiar la ruta de la build en el archivo vite.config.js
- [x] ` plugins: [
    laravel({
      input: [
        'resources/css/app.css',
      ],
      publicDirectory: 'public_html',
      refresh: true
    })
  ]
  },`

#install tailwind css vite
- [x] `npm install -D tailwindcss postcss autoprefixer` //instala tailwind css
- [x] `npx tailwindcss init -p` //crea el archivo tailwind.config.js

#install vite
- [x] `npm create vite@latest` //instala vite

#npm
- [x] `npm install just-debounce-it -E` //instala just-debounce-it para evitar que se ejecute muchas veces una funcion
- [x] `npm uninstall eslint eslint-config-react-app` //desinstala eslint
- [x] `npm i standard -D` //instala standard


#Laravel 10
- [x] `composer create-project laravel/laravel prueba` //instala laravel
- [x] `php artisan make:controller DiscordNotifications` //crea el controlador DiscordNotifications
- [x] `php artisan make:mail MessageWelcome` //crea el mail MessageWelcome
- [x] `php artisan migrate` //migrar la base de datos
- [x] `php artisan make:service WHMCS` //crea el servicio WHMCS
- [x] `php artisan make:model ShoppingCart` //crea el modelo ShoppingCart
- [x] `php artisan ser` //iniciar el servidor

#Laravel 10 servicios
- [x] `composer require guzzlehttp/guzzle` //instalar guzzle para hacer peticiones http
- [x] `composer require srmklive/paypal:~3.0` //instalar paypal
- [x] `php artisan vendor:publish --provider "Srmklive\PayPal\Providers\PayPalServiceProvider"` //publicar paypal
- [x] `composer require anhskohbo/no-captcha` //instalar captcha
- [x] `composer require laravel-lang/common --dev` //instalar idiomas
- [x] `php artisan lang:add es` //agregar idioma español
- [x] `php artisan lang:update` //actualizar idioma
- [x] `composer require torann/geoip` //instalar geoip
- [x] `php artisan vendor:publish --provider="Torann\GeoIP\GeoIPServiceProvider" --tag=config` //publicar geoip
- [x] `CACHE_DRIVER=array` //configurar cache en el archivo .env

#Servidor local/cPanel cron jobs
- [x] `php artisan make:command ExpirationTask` //crea el comando ExpirationTask
- [x] `$schedule->command('app:expiration-task')->everyMinute();` //programar tarea cada minuto, en el archivo app/Console/Kernel.php
- [x] `php artisan schedule:list` //lista las tareas programadas
- [x] `php artisan schedule:run` //ejecuta las tareas programadas
- [x] `php artisan schedule:work` //ejecuta las tareas programadas
- [x] `find / -name "php" -type f 2>/dev/null` //buscar lista de rutas de version php en el servidor
- [x] `/opt/cpanel/ea-php81/root/usr/bin/php /home/snipe/artisan schedule:run >> /dev/null 2>&1` //ejemplo de comando cron job en cPanel

#laravel 11 + vue 3 + vite + tailwind css + inertia js

- [x] `composer create-project laravel/laravel project-name` //instala laravel
- [x] `composer require laravel/breeze --dev` //instala laravel breeze
- [x] `php artisan breeze:install` //instala laravel breeze



