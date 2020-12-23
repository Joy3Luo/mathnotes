---
layout: post
title: Programming Foundations with JavaScript, HTML and CS
date: 2020-12-22 23:18 +0800
tags: [Java, HTML]
toc:  true
math: true
---

<!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-TG0XJZG53F"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'G-TG0XJZG53F');
  </script>

#### <font color= 6FBCE1>Week 1</font>

## <font color= 977FD7> Building a Web Page with HTML - What Is HTML?</font>

HTML is a language used to make web pages
- NOT a programming language, markup language
- Specifies contents of web page, used by browsers
- Specifies meaning or semantics

Collaborative standard
- First standard in 1993
- Current (2020) standard in 2014

<font color= E675A7> For example</font>

```html
<html>
  <head>
    <title>Hello World Page</title>
  <head>
    <p>Hellp World!</p>
  <body>
<html>
```
>Hellp World!


Different Types of Elements
- Metadata elements
  - Information about the page
    - \<html>, \<head>, \<title>
- Sectioning elements
  - Define regions

    - \<body>, \<h1>, \<div>

---

\<html>
- Contains all other elements
- Specifies using HTML standard

\<head>
- Information about the page: title, scripts, CSS

\<title>
- Specifies page title
- Nested inside <head> </head> tags

\<body>
- Contains all items seen on page

\<h1>
- Section header
- Also \<h2>, \<h3> ... \<h6>

\<div>
- Defines section of web page
- Useful for CSS

<font color= E675A7> For example</font>

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="author" content="Owen Astrachan, Drew
Hilton, Susan Rodger, Robert Duvall">
 <link rel=stylesheet href="./common/css/style.css"
type="text/css">
 <title>Build Software Applications</title>
</head>
<body>
<div class="titlebar">
 <img src="./common/images/dukelogovert.png"
id="dukeLogo"/>
 <img src="./common/images/coursera.png"
id="courseraLogo"/>
 <h1>Build Software Applications</h1>
</div>
```
