# Secure Headers

[![Financial Contributors on Open Collective](https://opencollective.com/secure-headers/all/badge.svg?label=financial+contributors)](https://opencollective.com/secure-headers)
[![Actions Status](https://github.com/bepsvpt/secure-headers/workflows/Laravel/badge.svg)](https://github.com/bepsvpt/secure-headers/actions)
[![Latest Stable Version](https://poser.pugx.org/bepsvpt/secure-headers/v/stable)](https://packagist.org/packages/bepsvpt/secure-headers)
[![Total Downloads](https://poser.pugx.org/bepsvpt/secure-headers/downloads)](https://packagist.org/packages/bepsvpt/secure-headers)
[![License](https://poser.pugx.org/bepsvpt/secure-headers/license)](https://packagist.org/packages/bepsvpt/secure-headers)

Add security related headers to HTTP response. The package includes Service Providers for easy [Laravel](https://laravel.com) integration.

- [Version](#version)
- [Installation](#installation)
- [Usage（non laravel project）](#usagenon-laravel-project)
- [Document and Notice](#document-and-notice)
- [Changelog](#changelog)
- [Upgrade](#upgrade)
- [License](#license)

## Version

7.3.0

### Supported Laravel Version

5.1 ~ 9.x

## Installation

### Non Laravel Project

Install using composer

```sh
composer require yohn/secure-headers
```

Copy config file to your project directory

```sh
cp vendor/yohn/secure-headers/config/secure-headers.php path/to/your/project/directory
```

Set up config file

Done!

### Laravel Project

Install using composer

```sh
composer require yohn/secure-headers
```

Add service provider in `config/app.php` ( laravel version < 5.5 )

```php
yohn\SecureHeaders\SecureHeadersServiceProvider::class,
```

Publish config file

```sh
php artisan vendor:publish --provider="yohn\SecureHeaders\SecureHeadersServiceProvider"
```

Add global middleware in `app/Http/Kernel.php`

```php
\yohn\SecureHeaders\SecureHeadersMiddleware::class,
```

Set up config file `config/secure-headers.php`

Done!

### Lumen Project

Install using composer

```sh
composer require yohn/secure-headers
```

Add service provider in `bootstrap/app.php`

```php
$app->register(yohn\SecureHeaders\SecureHeadersServiceProvider::class);
```

Copy config file to project directory

```sh
mkdir config
cp vendor/yohn/secure-headers/config/secure-headers.php config/secure-headers.php
```

Add global middleware in `bootstrap/app.php`

```php
$app->middleware([
   \yohn\SecureHeaders\SecureHeadersMiddleware::class,
]);
```

Set up config file `config/secure-headers.php`

Done!


## Usage(Non Laravel Project)

**Do not forget to import namespace.**

```php
<?php

use \yohn\SecureHeaders\SecureHeaders;
```

#### Instance

```php
<?php

// instantiate the class by fromFile static method
$secureHeaders = SecureHeaders::fromFile('/path/to/secure-headers.php');

// or instantiate the class directly
$config = require '/path/to/secure-headers.php';

$config['key'] = 'value'; // modify config value if needed

$secureHeaders = new SecureHeaders($config);
```

#### Send
```php
// Get headers
$secureHeaders->headers();

// Send headers to HTTP response
$secureHeaders->send();
```

## Document and Notice

Please see [DOCS](DOCS.md) for details.

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for details.

## Upgrade

Please see [UPGRADE](UPGRADE.md) for details.

## License

Secure Headers is licensed under [The MIT License (MIT)](LICENSE).
