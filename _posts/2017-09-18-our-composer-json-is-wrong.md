---
layout: post
date:   2017-08-18 23:00:00 +0200
title: "Our composer.json file is wrong"
categories:
    - "Software Engineering"
tags:
    - PHP
    - Adsmurai
    - Alpine Linux
    - Docker
---

I'm working for the [Adsmurai](http://www.adsmurai.com/) engineering team since
January, that's around 8 months and a half right now. In this time, we've
advanced a lot in the direction of splitting a big code monolith into different
and isolated services.

One tool that helped us a lot to achieve this goal was [Docker](https://www.docker.com/).
We started with [Ubuntu-based images](https://hub.docker.com/_/ubuntu/) for our
development environment, that was the case during my first seven months.

But then we wanted to use Docker in our production servers too for reasons that
are not important here: this is not a devops post! And at that point, we
realized that using [Alpine Linux](https://alpinelinux.org/) for our base images
could help us to save disk space, among other minor benefits. So we jumped to
[Alpine-based images](https://hub.docker.com/_/alpine/).

And here is where our story really starts. Our applications started to crash...
because there were missing functions and interfaces.

[Composer](https://getcomposer.org/) didn't complain about missing extensions,
but it was evident that something that we needed was not there. Our problem was
that Alpine, in order to obtain very little systems, splits its packages
whenever it makes sense, but that's not the case with Ubuntu nor Debian, nor
other popular Linux distros.

So, because many PHP extensions are pre-packaged in a single bundle for systems
like Debian, Ubuntu, RedHat, Centos... many developers forget to declare some
extensions as dependencies of their packages. Extensions that typically fall
into this category are: [`ext-ctype`](http://php.net/manual/en/book.ctype.php),
[`ext-fileinfo`](http://php.net/manual/en/book.fileinfo.php),
[`ext-session`](http://php.net/manual/en/book.session.php),
[`ext-tokenizer`](http://php.net/manual/en/book.tokenizer.php)...

This problem can be found across the entire [Packagist](https://packagist.org/)
packages repository, even if we look into the subset of super-popular packages,
like [Symfony](http://symfony.com/) components.

To end this post: my advice is to read the PHP.net documentation when we're
using special purpose functions  in order to know if they belong to an extension,
and declare such extensions as dependencies on our composer.json files.

Best regards!
