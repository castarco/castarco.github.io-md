---
layout: post
date:   2016-04-03 19:00:00 +0200
title: Generating Colored Gosper Curves
categories:
    - Hobbies
tags:
    - Fractals
    - Geometry
    - Mathematics
    - Generative Art
    - Art
---

Yesterday I finished a script to generate colored [Gosper Curves](https://en.wikipedia.org/wiki/Gosper_curve). You can
find it in Github, as a Gist:
[gosper_curve.py](https://gist.github.com/castarco/58826fa6a880cff69e1d987ce2037a1f).

The main idea behind this code is to generate an ordered list of points using a
[L-system](https://en.wikipedia.org/wiki/L-system) (a set of production rules combined with a mechanism for translating
the generated strings into geometric structures).

One extra idea I've applied is to work with the HSL color space instead of the RGB color space, this way I can do a
random walk over the Hue dimension (with "smooth" steps) keeping lightness and saturation as constants.

And this is one of the generated images:

![Gosper Curve](/images/2016/gosper_curve.png)
