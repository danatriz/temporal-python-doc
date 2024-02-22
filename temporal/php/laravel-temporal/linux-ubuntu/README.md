# Linux (Ubuntu)

## Konfigurasi Temporal pada Ubuntu menggunakan Terminal

ketikan atau copy perintah dibawah ini menggunakan terminal pada linux `sudo apt install php8.1-cli`

## Instalasi Composer pada Ubuntu menggunakan Terminal

Berikut merupakan langkah langkah command line yang dijalankan pada terminal Ubuntu untuk menginstall composer:

* `curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php`
* `HASH=curl -sS` `https://composer.github.io/installer.sig`
* `cecho $HASH`
* `php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"`
* `sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer`

### Konfigurasi PHP

**Instalasi ekstensi php-dom**

Jalankan command di bawah ini untuk mengaktifkan eksistensi php-dom

* `sudo apt update`
* `sudo apt install php-dom`

**Instalasi ekstensi php-curl**

* `sudo apt update`
* `sudo apt install php-curl`

### Instalasi GRPC

Berikut di bawah ini merupakan langkah langkah menginstall GRPC pada Linux

* `sudo apt-get install autoconf zlib1g-dev php-dev php-pear`
* `sudo pecl install grpc`
* `extension=grpc.so`
* `composer require "grpc/grpc"`

### Instalasi Temporal

Berikut di bawah ini merupakan langkah langkah menginstall Temporal pada Linux

* `sudo snap install temporal`

Jalankan Temporal Web UI pada Terminal Linux

* `temporal server start-dev --ui-port 8080`

### Instalasi Laravel Menggunakan Composer

* `composer create-project laravel/laravel example-app`
