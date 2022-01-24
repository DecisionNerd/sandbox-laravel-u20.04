# sandbox-laravel-u20.04
PHP Laravel Jetstream Setup on Ubuntu 20.04

## Getting Started

This is a step-by-step guide to getting started with developing a PHP web application on Laravel Jetstream.

## Environment

**Ubuntu 20.04**

We use Ubuntu Multipass.  Laravel Homestead is a great container development environment, but it does so much of the work for you that it is hard to learn what is going on under the hood.

We recommend connecting to your multipass instance via SSH from VS Code

## Repo Managmenet on Ubuntu 20.04

A developer called [Ondřej Surý](https://deb.sury.org/) maintains packages for PHP which include the latest minor versions - he is awesome.

### Prepare apt for Installation

```sh
sudo apt update
sudo apt upgrade
sudo apt install software-properties-common
```

### You can install his repositories for PHP & NGINX:

```
sudo add-apt-repository ppa:ondrej/php
sudo add-apt-repository ppa:ondrej/nginx
```

### Then update your repos & upgrade your packages:

```
sudo apt update
sudo apt upgrade
```
## SQL RDBMS Setup

Laravel works out of the box with MySQL, PostgreSQL, and SQLite.  You need to have a database configured before configuring your new application.

You will need to have values for the following settings in the `.env` file that configures your `config/database.php` file

```
DB_CONNECTION=mysql
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=db
DB_USERNAME=root
DB_PASSWORD=password
```

## NGINX

[NGINX Homepage](https://www.nginx.com/)

```sh
sudo apt install nginx
```

Note for Laravel deployment (also covered in sequence below): [Laravel Deployment on NGINX](https://laravel.com/docs/8.x/deployment#nginx)

## PHP 7.4

[PHP Homepage](https://www.php.net/)

```sh
sudo apt install php7.4 php7.4-xml php7.4-mbstring php7.4-pgsql php7.4-mysql

curl -LO https://phar.phpunit.de/phpunit-9.5.phar
chmod +x phpunit-9.5.phar
./phpunit-9.5.phar --version
```

## Node via NVM for `npm` Command used in Laravel Build

[Github NVM Install Instructions](https://github.com/nvm-sh/nvm#installing-and-updating)

### Install NVM

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

```sh
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

To download, compile, and install the latest release of node, do this:

```sh
nvm install node # "node" is an alias for the latest version
```

To install a specific version of node:

```sh
nvm install 14.7.0 # or 16.3.0, 12.22.1, etc
```

### npm Usage

[Github Usage Instructions](https://github.com/nvm-sh/nvm#usage)

```sh
npm [commands]...
```

## Composer

[Composer Installation Docs](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-macos)

### Download Instructions

[Download Page](https://getcomposer.org/download/)

```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '906a84df04cea2aa72f40b5f787e49f22d4c2f19492ac310e8cba5b96ac8b64115ac402c8cd292b8a03482574915d1a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

### Make Available Global

```
mv composer.phar /usr/local/bin/composer
```

## Laravel 8 

[Laravel Homepage](https://laravel.com/)

Laravel is a web application framework with expressive, elegant syntax. We’ve already laid the foundation — freeing you to create without sweating the small things.

### Installation Via Composer

[Composer Installation Instructions](https://laravel.com/docs/8.x/installation#installation-via-composer)

Install Globally:

```sh
composer global require laravel/installer
```

Or Install with Composer into your project:

```sh
composer create-project laravel/laravel example-app
```
## Laravel Jetstream 2

[L. Jetstream Homepage](https://jetstream.laravel.com/2.x/introduction.html)

### Installing L. Jetstream 2

[L. Jetstream 2 Installation Instructions](https://jetstream.laravel.com/2.x/installation.html)

You may use Composer to install Jetstream into your new Laravel project:

```sh
cd example-app
composer require laravel/jetstream
```

Install Jetstream With Livewire:

```sh
php artisan jetstream:install livewire --teams
npm install && npm run dev && php artisan migrate
```


## Laravel Artisan

[L. Artisan Homepage](https://laravel.com/docs/8.x/artisan)

Artisan is the command line interface included with Laravel. Artisan exists at the root of your application as the artisan script and provides a number of helpful commands that can assist you while you build your application. To view a list of all available Artisan commands, you may use the list command:

### Start local instance with Artisan

```
php artisan serve
```
