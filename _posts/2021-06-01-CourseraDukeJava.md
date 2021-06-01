---
layout: post
title: Programming - Programming Foundations with JavaScript
date: 2021-06-01 12:18 +0800
tags: [Programming]
---

<!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-TG0XJZG53F"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'G-TG0XJZG53F');
  </script>

### Variables
declare a new Variable,
> var x = 3;

more variables
> var y = 4;
var z = x + 2 * y;

update variables
> x = z - 1;
y = y * 2;

more complex
> var fgImage = new SimpleImage("drewRobert.png");
var bgImage = new SimpleImage("dinos.png");

calling methods:Syntax
> var fgImage = new SimpleImage("drewRobert.png");
var w = fgImage.getWidth();
var h = fgImage.getHeight();

Some Methods Have Parameters
> var pixel = fgImage.getPixel(0,0);
