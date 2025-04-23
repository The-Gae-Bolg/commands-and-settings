# Crear imagen de docker para Drupal 7

```
drupal7-docker/
│
├── docker-compose.yml
├── php.ini
└── drupal/     <-- aquí se descargará el core de Drupal 7
```

```yaml
version: '3.8'

services:
  web:
    image: php:5.6-apache
    container_name: drupal7-web
    ports:
      - "8080:80"
    volumes:
      - ./drupal:/var/www/html
      - ./php.ini:/usr/local/etc/php/php.ini
    depends_on:
      - db

  db:
    image: mysql:5.7
    container_name: drupal7-db
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: drupal7
      MYSQL_USER: drupal
      MYSQL_PASSWORD: drupal
    ports:
      - "3307:3306"

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    container_name: drupal7-pma
    restart: always
    ports:
      - "8081:80"
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: root
```

```
# php.ini
upload_max_filesize=64M
post_max_size=64M
memory_limit=256M
max_execution_time=300
max_input_time=300
```

## Descargar Drupal 7 o hacerlo por git bash
```bash
cd drupal
curl -OL https://ftp.drupal.org/files/projects/drupal-7.98.tar.gz
tar -xzf drupal-7.98.tar.gz --strip-components=1
rm drupal-7.98.tar.gz
```

## Iniciar los contenedores
```bash
docker-compose up -d
```
## Acceder a la instalación
- Acceder a `http://localhost:8080` para la instalación de Drupal 7.
- Acceder a `http://localhost:8081` para phpMyAdmin.
## Acceder a la base de datos
- Host: `db`
- Usuario: `drupal`
- Contraseña: `drupal`
- Base de datos: `drupal7`
## Acceder a phpMyAdmin
- Host: `localhost`
- Usuario: `root`
- Contraseña
- Base de datos: `drupal7`

## Acceder a la consola de los contenedores
```bash
docker exec -it drupal7-web bash
```
## Levantar los contenedores
```bash
docker-compose up -d
```
## Ver el estado de los contenedores
```bash
docker-compose ps
```
## Ver los logs de los contenedores
```bash
docker-compose logs -f
```
## Reiniciar los contenedores
```bash
docker-compose restart
```

## Parar los contenedores
```bash
docker-compose down
```
## Eliminar los contenedores
```bash
docker-compose down -v
```
## Eliminar los contenedores y las imágenes
```bash
docker-compose down --rmi all -v
```
## Eliminar los contenedores y las imágenes sin eliminar los volúmenes
```bash
docker-compose down --rmi all
```