## Generar usuarios y lotes en Laravel

## Crear comando

```php
<?php

namespace App\Console\Commands;

use App\Models\Client;
use App\Models\Lot;
use Illuminate\Console\Command;
use Illuminate\Support\Facades\Hash;
use Illuminate\Support\Str;

class GenerateTestData extends Command
{
  /**
   * The name and signature of the console command.
   *
   * @var string
   */
  protected $signature = 'generate:test-data';

  /**
   * The console command description.
   *
   * @var string
   */
  protected $description = 'Generates 100 test clients and 100 test lots.';

  /**
   * Execute the console command.
   */
  public function handle()
  {
    $this->info('Starting test data generation...');

    $clientIds = [];
    for ($i = 1; $i <= 100; $i++) {
      $rfcSuffix = str_pad($i, 3, '0', STR_PAD_LEFT);
      $rfc = 'XAXX020202' . $rfcSuffix;
      $client = Client::create([
        'type' => 'legal_person',
        'rfc' => $rfc,
        'name' => 'User Test ' . $i,
        'email' => 'clientes@admonvistas.com',
        'phone' => '4495806701',
        'password' => Hash::make('password' . $i),
        'email_verified_at' => now(),
        'created_at' => now(),
        'updated_at' => now(),
      ]);
      $clientIds[] = $client->id;
      $this->info("Client 'User Test {$i}' created with ID: {$client->id}");
    }

    $this->info('100 test clients generated. Now generating 100 test lots...');

    foreach ($clientIds as $index => $clientId) {
      Lot::create([
        'uuid' => Str::uuid(),
        'name' => 'Lote Test ' . ($index + 1),
        'block' => 'Bloque Test',
        'area' => 100.50,
        'status' => 'active',
        'project_id' => 6,
        'client_id' => $clientId,
        'created_at' => now(),
        'updated_at' => now(),
      ]);
      $this->info("Lot 'Lote Test " . ($index + 1) . "' created for client ID: {$clientId}");
    }

    $this->info('All 100 test lots generated and linked to clients.');
    $this->info('Test data generation complete!');
  }
}
```

### Registrar el proveedor de servicios

```php
<?php

namespace App\Providers;

use App\Models\LotRequirement;
use Illuminate\Pagination\Paginator;
use Illuminate\Support\Facades\Gate;
use Illuminate\Support\ServiceProvider;
use App\Policies\Admin\LotRequirementPolicy as AdminLotRequirementPolicy;
use App\Policies\Client\LotRequirementPolicy as ClientLotRequirementPolicy;
use App\Console\Commands\GenerateTestData;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Register any application services.
     */
    public function register(): void
    {
        app()->usePublicPath(env('APP_PUBLIC_PATH', public_path()));
    }

    /**
     * Bootstrap any application services.
     */
    public function boot(): void
    {
        Paginator::useBootstrapFive();

        Gate::before(function ($user, $ability) {
            return $user->hasRole('super') ? true : null;
        });
        
        // Registrar comandos de consola
        if ($this->app->runningInConsole()) {
            $this->commands([
                GenerateTestData::class,
            ]);
        }
    }
}
```