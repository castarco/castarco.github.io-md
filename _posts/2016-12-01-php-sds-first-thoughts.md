---
layout: post
date:   2016-12-01 19:00:00 +0200
title: PHP-SDS First Thoughts
categories:
    - "Data Engineering"
tags:
    - PHP
    - "PHP-SDS"
    - Rust
    - "Data Engineering"
---

Some days have passed since my last contribution to [PHP-SDS](https://github.com/SciPHPy/php-sds-polyfill), but today
I've returned, and my first step will be telling something about this project.

The name of this PHP library isn't very imaginative: "Scientific Data Structures". The data structures aren't scientific
or unscientific :s , but there is an extension called "[PHP-DS](https://github.com/php-ds)" (PHP Data Structures), which
provides basic data structures, and PHP-SDS aims to provide "data-science related data structures"... so, that's it.

My idea was to port some features from three interesting Python projects to PHP: [Pandas](http://pandas.pydata.org/),
[Numpy](http://www.numpy.org/) and [TensorFlow](https://www.tensorflow.org/). The basic data structures that will be
implemented are Matrix, DataFrame and Tensor (the "same" as Numpy's ndarray).

As today, almost all the meaningful features of the Tensor data structure have been developed in pure PHP, plus some
basic features of the Matrix class.

So? Well, the actual code is pure PHP, but it is a sort of prototype/polyfill. I want to implemenet a PHP extension to
boost performance for certain data related operations, and I want to implement that extension using Rust.

There are a lot of things to do, finishing the Matrix and DataFrame classes in the polyfill library, add some data
importing/exporting features, and then start coding the extension using Rust. You're welcome if you want to become
involved :) .

These are the main sources I'm using to obtain inspiration:

  * [Creating a PHP Extension to Rust](http://hermanradtke.com/2015/08/03/creating-a-php-extension-to-rust.html)
  * [Creating a PHP extension in Rust](https://jaredonline.svbtle.com/creating-a-php-extension-in-rust)
  * [Extension Writing Part I: Introduction to PHP and Zend](http://devzone.zend.com/303/extension-writing-part-i-introduction-to-php-and-zend)
  * [Extension Writing Part II: Parameters, Arrays, and ZVALS](http://devzone.zend.com/317/extension-writing-part-ii-parameters-arrays-and-zvals)
