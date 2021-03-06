Overview
========

TropoPHP is a set of PHP classes for working with [Tropo's cloud communication service](http://tropo.com/). Tropo allows a developer to create applications that run over the phone, IM, SMS, and Twitter using web technologies. This library communicates with Tropo over JSON.

[![Latest Stable Version](https://poser.pugx.org/albertobravi/tropo-webapi-php-oop/v/stable)](https://packagist.org/packages/albertobravi/tropo-webapi-php-oop)
[![Total Downloads](https://poser.pugx.org/albertobravi/tropo-webapi-php-oop/downloads)](https://packagist.org/packages/albertobravi/tropo-webapi-php-oop)
[![Latest Unstable Version](https://poser.pugx.org/albertobravi/tropo-webapi-php-oop/v/unstable)](https://packagist.org/packages/albertobravi/tropo-webapi-php-oop)
[![License](https://poser.pugx.org/albertobravi/tropo-webapi-php-oop/license)](https://packagist.org/packages/albertobravi/tropo-webapi-php-oop)
[![composer.lock](https://poser.pugx.org/albertobravi/tropo-webapi-php-oop/composerlock)](https://packagist.org/packages/albertobravi/tropo-webapi-php-oop)

Requirements
============

 * PHP 5.3.0 or greater
 * PHP Notices disabled (All error reporting disabled is recommended for production use)
 
Installation
============

  * Via [Composer](https://getcomposer.org/): `composer require albertobravi/tropo-webapi-php-oop`
    
  * Or, download/clone github project from: [https://github.com/albertobravi/tropo-webapi-php-oop.git](https://github.com/albertobravi/tropo-webapi-php-oop.git) and `require /path/to/tropo-webapi-php-oop/autoload.php`

Usage
=====
Create an application on Tropo's website.
 
Set an endpoint for SMS and/or VOICE channels.

Put your code in your endpoint, making sure that Tropo's services can call your endpoint.

Answer the phone, say something, and hang up.

```php
<?php
    $tropo = new \Tropo\Tropo();
    
    // Use Tropo's text to speech to say a phrase.
    $tropo->say('Yes, Tropo is this easy.');
    
    // Render the JSON back to Tropo.
    $tropo->renderJSON();
```

Asking for input.

```php
<?php
    $tropo = new \Tropo\Tropo();
    
    // Ask the user a question
    $tropo->ask('What is your favorite programming language?', [
      'choices'=>'PHP, Ruby(Ruby, Rails, Ruby on Rails), Python, Java(Groovy, Java), Perl',
      'event'=> [
        'nomatch' => 'Never heard of it.',
        'timeout' => 'Speak up!'
      ]
    ]);
    
    // Tell Tropo how to continue if a successful choice was made
    $tropo->on([
      'event' => 'continue', 
      'say' => 'Fantastic! I love that, too!'
    ]);
    
    // Render the JSON back to Tropo
    $tropo->renderJSON();
```