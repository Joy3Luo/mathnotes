---
layout: post
title: DataCamp Intermediate Python
date: 2023-11-01 11:18 +0800
tags: [Python]
toc:  true
---

<!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-TG0XJZG53F"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'G-TG0XJZG53F');
  </script>

  <style TYPE="text/css">code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}</style><script type="text/x-mathjax-config">
  MathJax.Hub.Config({
      tex2jax: {
          inlineMath: [['$','$'], ['\\(','\\)']],
          displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
          skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
      }});
  MathJax.Hub.Queue(function() {
      var all = MathJax.Hub.getAllJax(), i;
      for(i = 0; i < all.length; i += 1) {
          all[i].SourceElement().parentNode.className += ' has-jax';
      }});
  </script><script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-AMS_HTML-full"></script>  

## Intermediate Python

### Matplotlib

---
#### **Line plot (1)**

With matplotlib, you can create a bunch of different plots in Python. The most basic plot is the line plot. A general recipe is given here.

```
import matplotlib.pyplot as plt
plt.plot(x,y)
plt.show()
```
In the video, you already saw how much the world population has grown over the past years. Will it continue to do so? The world bank has estimates of the world population for the years 1950 up to 2100. The years are loaded in your workspace as a list called year, and the corresponding populations as a list called pop.

This course touches on a lot of concepts you may have forgotten, so if you ever need a quick refresher, download the Python For Data Science Cheat Sheet and keep it handy!


> **_Instructions:_**
> * print() the last item from both the year and the pop list to see what the predicted population for the year 2100 is. Use two print() functions.
> * Before you can start, you should import matplotlib.pyplot as plt. pyplot is a sub-package of matplotlib, hence the dot.
> * Use plt.plot() to build a line plot. year should be mapped on the horizontal axis, pop on the vertical axis. Don't forget to finish off with the plt.show() function to actually display the plot.

```py
# Print the last item from year and pop
print(year[-1],pop[-1])

# Import matplotlib.pyplot as plt
import matplotlib.pyplot as plt

# Make a line plot: year on the x-axis, pop on the y-axis
plt.plot(year,pop)

# Display the plot with plt.show()
plt.show()
```
---

#### ** **



> **_Instructions:_**
> *
> *
> *

```py



```
---


#### ** **



> **_Instructions:_**
> *
> *
> *

```py



```
---


#### ** **



> **_Instructions:_**
> *
> *
> *

```py



```
---


#### ** **



> **_Instructions:_**
> *
> *
> *

```py



```
---


#### ** **



> **_Instructions:_**
> *
> *
> *

```py



```
---























---
**Instructions**

It works with almost all markdown flavours (the below blank line matters).

---
