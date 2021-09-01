Service
=====

[![Latest Stable Version](http://img.shields.io/packagist/v/nxtcode/agent.svg)](https://packagist.org/packages/nxtcode/agent) [![Total Downloads](http://img.shields.io/packagist/dm/nxtcode/agent.svg)](https://packagist.org/packages/nxtcode/agent) [![Build Status](http://img.shields.io/travis/nxtcode/agent.svg)](https://travis-ci.org/nxtcode/agent) [![Coverage Status](http://img.shields.io/coveralls/nxtcode/agent.svg)](https://coveralls.io/r/nxtcode/agent) [![Donate](https://img.shields.io/badge/donate-paypal-blue.svg)](https://www.paypal.me/nxtcode)

A PHP desktop/mobile user agent parser with support for Laravel, based on [Mobile Detect](https://github.com/serbanghita/Mobile-Detect) with desktop support and additional functionality.

<p align="center">
<img src="https://www.nxtcode.com/webassets/img/behance.png" height="275">
</p>

Installation
------------

Install using composer:

```bash
composer require nxtcode/agent
```

Laravel (optional)
------------------

Add the service provider in `config/app.php`:

```php
NxtCode\Service\ServiceServiceProvider::class,
```

And add the Service alias to `config/app.php`:

```php
'Service' => NxtCode\Service\Facades\Service::class,
```

Basic Usage
-----------

Start by creating an `Service` instance (or use the `Service` Facade if you are using Laravel):

```php
use NxtCode\Service\Service;

$tool = new Service();
```

If you want to parse user agents other than the current request in CLI scripts for example, you can use the `setUserService` and `setHttpHeaders` methods:

```php
$tool->setUserService('Mozilla/5.0 (Macintosh; Intel Mac OS X 10_6_8) AppleWebKit/537.13+ (KHTML, like Gecko) Version/5.1.7 Safari/534.57.2');
$tool->setHttpHeaders($headers);
```

All of the original [Mobile Detect](https://github.com/serbanghita/Mobile-Detect) methods are still available, check out some original examples at https://github.com/serbanghita/Mobile-Detect/wiki/Code-examples

### Is?

Check for a certain property in the user agent.

```php
$tool->is('Windows');
$tool->is('Firefox');
$tool->is('iPhone');
$tool->is('OS X');
```

### Magic is-method

Magic method that does the same as the previous `is()` method:

```php
$tool->isAndroidOS();
$tool->isNexus();
$tool->isSafari();
```

### Mobile detection

Check for mobile device:

```php
$tool->isMobile();
$tool->isTablet();
```

### Match user agent

Search the user agent with a regular expression:

```php
$tool->match('regexp');
```

Additional Functionality
------------------------

### Accept languages

Get the browser's accept languages. Example:

```php
$languages = $tool->languages();
// ['nl-nl', 'nl', 'en-us', 'en']
```

### Device name

Get the device name, if mobile. (iPhone, Nexus, AsusTablet, ...)

```php
$device = $tool->device();
```

### Operating system name

Get the operating system. (Ubuntu, Windows, OS X, ...)

```php
$platform = $tool->platform();
```

### Browser name

Get the browser name. (Chrome, IE, Safari, Firefox, ...)

```php
$browser = $tool->browser();
```

### Desktop detection

Check if the user is using a desktop device.

```php
$tool->isDesktop();
```

*This checks if a user is not a mobile device, tablet or robot.*

### Phone detection

Check if the user is using a phone device.

```php
$tool->isPhone();
```

### Robot detection

Check if the user is a robot. This uses [jaybizzle/crawler-detect](https://github.com/JayBizzle/Crawler-Detect) to do the actual robot detection.

```php
$tool->isRobot();
```

### Robot name

Get the robot name.

```php
$robot = $tool->robot();
```

### Browser/platform version

MobileDetect recently added a `version` method that can get the version number for components. To get the browser or platform version you can use:

```php
$browser = $tool->browser();
$version = $tool->version($browser);

$platform = $tool->platform();
$version = $tool->version($platform);
```

*Note, the version method is still in beta, so it might not return the correct result.*

## License

Laravel User Service is licensed under [The MIT License (MIT)](LICENSE).

## Security contact information

To report a security vulnerability, follow [these steps](https://tidelift.com/security).
