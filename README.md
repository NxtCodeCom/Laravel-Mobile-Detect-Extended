# MobileDetect

MobileDetect is a wrapper of Mobile_Detect which integrates it into Laravel.

## Installation

Add `nxtcode/mobile-detect` to `composer.json`.

    "nxtcode/mobile-detect": "dev-master"
    
Run `composer update` to pull down the latest version of MobileDetect. Now open up `app/config/app.php` and add the service provider to your `providers` array.

    'providers' => array(
        'NxtCode\Minimalist\MobileDetectServiceProvider',
    )

## Usage

Facade would be \Mobile  
for the API see: [Mobile_Detect](https://github.com/serbanghita/Mobile-Detect)
