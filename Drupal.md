# Modulos de Drupal

- [Drupal](https://www.drupal.org/)
- [Devel 7](https://www.drupal.org/project/devel/releases/7.x-1.7)
- [Localization update](https://www.drupal.org/project/l10n_update/releases/7.x-2.7)

## Configuración de Drupal

## Agregar en app/sites/default/settings.php para permisos de archivos
```php
$conf['file_temporary_path'] = '/tmp';
$conf['file_chmod_directory'] = 0777;
$conf['file_chmod_file'] = 0666;
```