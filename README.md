# MobileDetect

MobileDetect is a wrapper of Mobile_Detect which integrates it into Laravel.

## Installation

Add `itrulia/mobile-detect` to `composer.json`.

    "itrulia/mobile-detect": "dev-master"
    
Run `composer update` to pull down the latest version of MobileDetect. Now open up `app/config/app.php` and add the service provider to your `providers` array.

    'providers' => array(
        'Itrulia\Minimalist\MobileDetectServiceProvider',
    )

## Usage

Facade would be \Mobile  
for the API see: [Mobile_Detect](https://github.com/serbanghita/Mobile-Detect)
