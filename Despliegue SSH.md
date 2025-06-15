# Despliegue SSH en un servidor cPanel

## Script de despliegue

```bash
#!/bin/bash
set -e

# Establesco mis variables que ocupare a lo largo del script
TOKEN_FILE=~/.token.signlydocs.kiubix.biz.txt
REPO_URL=gitlab.kiubix.com/singly-group/signly-landing-astro.git
RUTA_APP=/var/www/signlydocs.kiubix.biz

# Cambio la ruta de donde se encuntra la aplicacion de signly
cd ~/signlydocs.kiubix.biz

# Verifica si el archivo de token existe
if [ ! -f "$TOKEN_FILE" ]; then
  echo "El archivo $TOKEN_FILE no existe. Asegúrate de que el archivo contenga el token."
  exit 1
fi

# Lee el token desde el archivo
TOKEN=$(cat "$TOKEN_FILE")

# Se optiene los ultimos cambios en el repo
git fetch https://$TOKEN@$REPO_URL main
git pull https://$TOKEN@$REPO_URL main

# Instalo de nuevo las dependenicias para evitar que no existan alguna dependencia
npm i

# Se realiza la la contruccion de la aplicación eliminando el ultimo build
rm -rf ./dist
npm run build
rm -rf $RUTA_APP/*
cp -rf ./dist/* $RUTA_APP

# Mensaje final
echo "Despliegue con exito completo :)!!"
```
## Se guarda en `~/.personal_scripts/deploy_landding`, si se es root estaria en `/root/.personal_scripts/deploy_landding`

## Se crea un archivo de token en `~/.token.signlydocs.kiubix.biz.txt` con el token de acceso personal de gitlab, si se es root estaria en `/root/.token.signlydocs.kiubix.biz.txt` y este contiene el token de acceso personal de gitlab. ejemplo:

```
# Token de acceso personal de gitlab
glpat-xxxxxxxxxxxxxxxxxxxxxxxx
```

## Se le da permisos de ejecucion al script

```bash
chmod +x ~/.personal_scripts/deploy_landding
```
## Se ejecuta el script

```bash
~/.personal_scripts/deploy_landding
```
## Se puede agregar un alias para facilitar la ejecucion del script, por ejemplo:

```bash
alias deploy_landding='~/.personal_scripts/deploy_landding'
```
## Se agrega el alias al archivo `~/.bashrc` o `~/.zshrc` para que se cargue al iniciar la terminal

```bash
echo "alias deploy_landding='~/.personal_scripts/deploy_landding'" >> ~/.bashrc
```
```bash
echo "alias deploy_landding='~/.personal_scripts/deploy_landding'" >> ~/.zshrc
```
## Se recarga el archivo de configuracion de la terminal

```bash
source ~/.bashrc
```
```bash
source ~/.zshrc
```
## Ahora se puede ejecutar el script con el alias

```bash
deploy_landding
```
## Notas
- Asegúrate de que el token tenga permisos de lectura y escritura en el repositorio.
- El script asume que tienes `git` y `npm` instalados en tu servidor.
- El script elimina el contenido del directorio de destino antes de copiar los nuevos archivos, asegúrate de que esto sea lo que deseas.
- El script está diseñado para ser ejecutado en un entorno cPanel, asegúrate de que las rutas y permisos sean correctos para tu configuración específica.