---
layout: post
date:   2015-10-18 19:00:00 +0200
title: Added Isso commenting system
categories:
    - "Meta"
tags:
    - Blog
    - Isso
    - Privacy
---

Since today is possible to post comments in this blog :) . I've integrated the [Isso](http://posativ.org/isso/)
commenting system in order to allow readers to send comments.

### My reasons

I've chosen this software because I don't want to help big companies to destroy our privacy. If people want to tell to
the world everything about themselves then I'm not opposed to that, but I don't want to force the people who are worried
about protecting its privacy.

Disqus is a great option to add comments in static blogs, but it requires registration and allows user tracking around
the web.

### About the underlying technology

Isso is programmed in Python and runs in the server as a daemon, and it can be integrated with the following "http
handlers": **Gevent** (this isn't an http handling library, but a generic non-blocking IO handling library), **uWSGI**,
**Gunicorn**, **mod_wsgi** (for Apache), and **mod_fastcgi** (also for Apache).

For simplicity, I've chosen to use **Gevent**, it's the easiest option (no settings :D), but maybe I'll change the
settings in the future in favour of uWSGI because its flexibility.

**Gunicorn** is not an option because I need to optimize every service in my server (my server is VERY tiny), and the
prefork model isn't enough efficient.

**mod_wsgi**, and **mod_fastcgi** require some configuration and are too coupled with the Apache server, so I won't
consider them neither.

### Some points that I dislike

I'm very grateful for the existence of Isso, but I it needs some rework: The management system is too complicated and
rigid, there is lack of documentation, and there aren't new releases since 7 months ago (I think this is because there
is a work in progress on a big refactor).

Because this, I'm considering to study the Isso's code in order to be able to contribute, or to fork the project if my
needs don't match with the project's aims.
