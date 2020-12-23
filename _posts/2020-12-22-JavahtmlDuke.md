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

# Building a Web Page with HTML

## <font color= 977FD7>What Is HTML?</font>

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
\> Hellp World!

---

Different Types of Elements
- Metadata elements
  - Information about the page
    - \<html>, \<head>, \<title>
- Sectioning elements
  - Define regions

    - \<body>, \<h1>, \<div>

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

---

## <font color= 977FD7>Formatting Text and Nesting Tags</font>

Tags surround text or page elements
```html
<b> Make text stylistically different </b>
<b> Traditionally bold face, but can change </b>
<em> Emphasize text! </em>
<b>this</b> <em>is an <b>example of nested</b> tags</em>
```
\> <b> Make text stylistically different </b>

\> <b> Traditionally bold face, but can change </b>

\> <em> Emphasize text! </em>

\> <b>this</b> <em>is an <b>example of nested</b> tags</em>

---

## <font color= 977FD7>Adding Images and Links</font>

Image tag:
```html
<img src=“{{ '/IMG_0621.jpg' | relative_url }}” width=“75%”/>
<img src="{{ '/IMG_0621.jpg' | relative_url }}" width="300px">
<img src=“{{ '/IMG_0621.jpg' | relative_url }}” />
```
\>
<img src="{{ '/IMG_0621.jpg' | relative_url }}" width="300px">


No end tag, src required, width optional
- height=
- CSS later

Linking Pages Together

```html
<h1>Where to learn HTML?</h1>
<p>
There are many sites that will serve as …
<p>
Mozilla provides
<a href="https://developer.mozilla.org/en-US/Learn/HTML">
a resource for learning
</a> HTML.
```

\> Mozilla provides <a href="https://developer.mozilla.org/en-US/Learn/HTML"> a resource for learning</a> HTML.

---

## <font color= 977FD7>Lists and Tables</font>


Some lists use circles or bullets
- These are unordered lists, tag: \<ul> \</ul>
  - Inside \<ul> \</ul> must have sequence of \<li>\</li> elements
- Content viewed in order, list labels all the same

 ```html
 <ul>
 <li>How computing and programming are changing the world.</li>
 <li>Internet and the Web</li>
 <li>HTML and CSS to create web pages</li>
<li>Javascript to create images and to</li>
 </ul>
 ```
\>
 <ul><li>How computing and programming are changing the world.</li>
<li>Internet and the Web</li>
<li>HTML and CSS to create web pages</li>
<li>Javascript to create images and to</li> </ul>


\<ol> is ordered list
- \<li>\</li> required
- Automatic numbering
- Add, remove \<li>
- Numbers change

```html
<ol>
  <li>Apple1</li>
  <li>Apple2</li>
  <li>Apple3</li>
  <li>Apple4</li>
</ol>
```
\>
<ol>
  <li>Apple1</li>
  <li>Apple2</li>
  <li>Apple3</li>
  <li>Apple4</li>
</ol>


HTML table elements
- \<table>\</table>
- contains rows \<tr>\</tr>

```html
<table>
 <tr>
 <th>Sweet</th>
 <th>Sour</th>
 <th>Salty</th>
 </tr>
 <tr>
 <td> Milk </td>
 <td> Yogurt </td>
 <td> Sardines </td>
 </tr>
 <tr>
 <td> Pineapple </td>
 <td> Kimchi </td>
 <td> Salami </td>
 </tr>
 <tr>
 <td> Grape </td>
 <td> Vinegar </td>
 <td> Pickles </td>
 </tr>
</table>
```

\>
<table>
 <tr>
 <th>Sweet</th>
 <th>Sour</th>
 <th>Salty</th>
 </tr>
 <tr>
 <td> Milk </td>
 <td> Yogurt </td>
 <td> Sardines </td>
 </tr>
 <tr>
 <td> Pineapple </td>
 <td> Kimchi </td>
 <td> Salami </td>
 </tr>
 <tr>
 <td> Grape </td>
 <td> Vinegar </td>
 <td> Pickles </td>
 </tr>
</table>
