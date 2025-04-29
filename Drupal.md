# Modulos de Drupal

- [Drupal](https://www.drupal.org/)
- [Devel 7](https://www.drupal.org/project/devel/releases/7.x-1.7)
- [Localization update](https://www.drupal.org/project/l10n_update/releases/7.x-2.7)
- [ckeditor](https://www.drupal.org/project/ckeditor/releases/7.x-1.23)
- [IMCE](https://www.drupal.org/project/imce/releases/7.x-1.11)
- [Video Embed Field](https://www.drupal.org/project/video_embed_field/releases/7.x-2.0-beta11)
- [ctools](https://www.drupal.org/project/ctools/releases/7.x-1.21)
- [Views](https://www.drupal.org/project/views/releases/7.x-3.30)


## Configuración de Drupal

## Agregar en app/sites/default/settings.php para permisos de archivos
```php
$conf['file_temporary_path'] = '/tmp';
$conf['file_chmod_directory'] = 0777;
$conf['file_chmod_file'] = 0666;
```