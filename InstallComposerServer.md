# Install Composer in cPanel server

## Download Composer in root project directory

```bash
cd /home/username/
curl -sS https://getcomposer.org/installer -o composer-setup.php
```

## Install Composer locally

```bash
php composer-setup.php --install-dir=bin --filename=composer
```

## Add Composer to PATH

```bash
export PATH="$HOME/bin:$PATH"
```

## Add Composer to .bashrc

```bash
source ~/.bashrc
```

## Check Composer version

```bash
composer --version
```

## Create alias for php version and composer + php version

```bash
alias php82='/opt/cpanel/ea-php82/root/usr/bin/php'
alias composer='/opt/cpanel/ea-php82/root/usr/bin/php /home/{userdir}/bin/composer'
```

## Use Composer

```bash
composer install
```

## Use php artisan commands

```bash
php82 artisan key:generate
php82 artisan migrate
php82 artisan db:seed
php82 artisan serve
```