---
layout: post
date:   2015-10-12 19:00:00 +0200
title: Be aware of trailing slashes in Symfony 2 URIs
categories:
    - "Backend Development"
tags:
    - Symfony
    - Symfony2
    - PHP
    - FOSRestBundle
    - REST
---

This post will be very short, it's only a little advice. I'm currently working on the development of a REST API with
Symfony 2, and to save time we're using the FOS REST Bundle.

Following the recommended practices, we are using HTTPS to enhance security. For some strange reason, we discovered that
a single method in the entire API was sending a 301 status code, telling the client to request the resource to the same
path, but using HTTP.

As you can imagine, this was pretty annoying. We aren't using redirections anywhere, why Symfony was doing this? Well,
it was a trailing slash:

```php
<?php

namespace OurCompany\BundleName\Controller;

use FOS\RestBundle\Controller\Annotations\Get;
use FOS\RestBundle\Controller\Annotations\NamePrefix;
use FOS\RestBundle\Controller\FOSRestController;

use Sensio\Bundle\FrameworkExtraBundle\Configuration\Security;

use Symfony\Component\HttpFoundation\Request;
use Symfony\Component\HttpFoundation\Response;

/**
 * Class ExamplesController
 * @package OurCompany\BundleName\Controller
 *
 * @NamePrefix("example_")
 */
class ExampleController extends FOSRestController
{
    /**
     * @Get("/example/{exampleId}/subexamples/")
     * @Security("has_role('ROLE_USER')")
     *
     * @param Request $request
     * @return Response
     */
    public function getSubexamplesAction(Request $request, $exampleId)
    {
        // Whatever
    }
}

```

So, the bug was in the `@Get` annotation on the `ExampleController::getSubexamplesAction` method. The trailing slash was
breaking the normal behavior of the application. The corrected code looks like this:

```php
<?php

    /**
     * @Get("/example/{exampleId}/subexamples")
     * @Security("has_role('ROLE_USER')")
     *
     * @param Request $request
     * @return Response
     */
    public function getSubexamplesAction(Request $request, $exampleId)
    {
        // Whatever
    }
```
