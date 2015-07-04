Endroid Google Cloud Messaging Bundle
=====================================

*By [endroid](http://endroid.nl/)*

[![Build Status](https://secure.travis-ci.org/endroid/EndroidGcmBundle.png)](http://travis-ci.org/endroid/EndroidGcmBundle)
[![Latest Stable Version](https://poser.pugx.org/endroid/gcm-bundle/v/stable.png)](https://packagist.org/packages/endroid/gcm-bundle)
[![Total Downloads](https://poser.pugx.org/endroid/gcm-bundle/downloads.png)](https://packagist.org/packages/endroid/gcm-bundle)

This bundle enables you to use the Endroid Google Cloud Messaging (endroid/Gcm) library as a decoupled service and
enables configuration through the Symfony framework. Google Cloud Messaging is a service that helps developers send
data from servers to their Android applications on Android devices. For more information on the services provided see
the [endroid/Gcm](https://github.com/endroid/Gcm) repository and [Google GCM](http://developer.android.com/guide/google/gcm/index.html).

[![knpbundles.com](http://knpbundles.com/endroid/EndroidGcmBundle/badge-short)](http://knpbundles.com/endroid/EndroidGcmBundle)

## Requirements

* Symfony
* Dependencies:
 * [`Buzz`](https://github.com/kriswallsmith/Buzz)
 * [`Gcm`](https://github.com/endroid/Gcm)

## Installation

### Add in your composer.json

```js
{
    "require": {
        "endroid/gcm-bundle": "dev-master"
    }
}
```

### Install the bundle

``` bash
$ curl -s http://getcomposer.org/installer | php
$ php composer.phar update endroid/gcm-bundle
```

Composer will install the bundle to your project's `vendor/endroid` directory.

### Enable the bundle via the kernel

``` php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Endroid\Bundle\GcmBundle\EndroidGcmBundle(),
    );
}
```

## Configuration

### config.yml

```yaml
endroid_gcm:
    api_key: "Your API Key (use the Browser key)"
```

## Usage

After installation and configuration, the service can be directly referenced from within your controllers.

```php
<?php
public function gcmSendAction()
{
    $client = $this->get('endroid.gcm.client');

    $registrationIds = array(
        // Registration ID's of devices to target
    );

    $data = array(
        'title' => 'Message title',
        'message' => 'Message body',
    );

    $response = $gcm->send($data, $registrationIds);

    ...
}
```

## Versioning

Semantic versioning ([semver](http://semver.org/)) is applied as much as possible.

## License

This bundle is under the MIT license. For the full copyright and license information, please view the LICENSE file that
was distributed with this source code.
