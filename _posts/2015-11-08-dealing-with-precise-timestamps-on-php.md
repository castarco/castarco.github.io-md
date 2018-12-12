---
layout: post
date:   2015-11-08 19:00:00 +0200
title: Dealing with precise timestamps in PHP
categories:
    - "Backend Development"
tags:
    - PHP
    - Timestamps
    - Doctrine
    - MongoDB
---

PHP does not offer any native class to implement timestamps with milliseconds or microseconds precision, the only
"native" way to do it is working with the weird microtime function and/or the `\MongoDate` class (available through the
`mongo` extension).

Using the `\DateTime` class is not enough, because it only can offer seconds precision, and using the `\MongoDate` class
isn't a good idea if you aren't using MongoDB or if you care about coupling. In fact, the `mongo` extension will be
deprecated in a few months in favour of a new extension that is in active development right now.

Because this, I've developed two Composer packages to allow using type hinting without increasing coupling and with less
abstraction leaks:

* PHP-Jiffy, a library that provides a timestamp class with milliseconds (and   even microseconds) precision:
  [https://github.com/Litipk/php-jiffy/](https://github.com/Litipk/php-jiffy/).
* Doctrine MongoDB Jiffy, an addapter to use the PHP-Jiffy library with Doctrine's MongoDB ODM:
  [https://github.com/Litipk/doctrine-mongodb-jiffy](https://github.com/Litipk/doctrine-mongodb-jiffy).

Is my intention to modify the PHP-Jiffy library at the same time of the new MongoDB's extension release, so it will be
very useful for people who likes moving fast to new software versions.
