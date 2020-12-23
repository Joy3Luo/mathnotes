---
layout: post
title: The First and Second Derivatives
date: 2020-10-06 23:18 +0800
tags: [Notes]
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

### <font color= 977FD7> The First and Second Derivatives</font>
#### <font color= 6FBCE1> The Meaning of the First Derivative</font>


The first derivative of the function $f(x)$, which we write as $f(x)$ or as $\frac{df}{dx}$, is the slope of the tangent lin to the function at the point x. To put this in non-graphical terms, the first derivative tells us how whether a function is increasing or decreasing, and by how much it is increasing or decreasing. This information is reflected in the graph of a function by the slope of the tangent line to a point on the graph, which is sometimes describe as the slope of the function. Positive slope tells us that, as x increases, $$f(x)$$ also increases. Negative slope tells us that, as x increases, $$f(x)$$ decreases. Zero slope does not tell us anything in particular: the function may be increasing, decreasing, or at a local maximum or a local minimum at that point. Writing this information in terms of derivatives, we see that:

• if $$\frac{df}{dx}(p)$$ > 0, then $$f(x)$$ is an increasing function at x = p.<br/>
• if $$\frac{df}{dx}(p)$$ < 0, then $$f(x)$$ is a decreasing function at x = p.<br/>
• if $$\frac{df}{dx}(p)$$ = 0, then x = p is called a critical point of $$f(x)$$, and we do not know anything new about the behavior of $$f(x)$$ at x = p<br/>

<font color= E675A7> For example</font>
Take $$f(x) = 3x^3 − 6x^2 + 2x − 1$$.<br/> The derivative of $$f(x)$$ is $$\frac{dy}{dx} = 9x^2 − 12x + 2$$.<br/>
At x = 0, the derivative of $$f(x)$$ is therefore 2, so we know that $$f(x)$$ is an increasing function at x = 0.<br/>
At x = 1, the derivative of $$f(x)$$ is $$\frac{df}{dx}(1) = 9 · 1^2 − 12 · 1 + 2 = 9 − 12 + 2 = −1$$<br/>
so $$f(x)$$ is a decreasing function at x = 1.

#### <font color= 6FBCE1> The Meaning of the Second Derivative</font>

The second derivative of a function is the derivative of the derivative of that function. We write it as $$f''(x)$$ or as $$\frac{d^2f}{dx^2}$$. While the first derivative can tell us if the function is increasing or decreasing, the second derivative tells us if the first derivative is increasing or decreasing. If the second derivative is positive, then the first derivative is increasing, so that the slope of the tangent line to the function is increasing as x increases. We
see this phenomenon graphically as the curve of the graph being concave up, that is, shaped like a parabola open upward. Likewise, if the second derivative is negative, then the first derivative is decreasing, so that the slope of the tangent line to the function is decreasing as x increases. Graphically, we see this as the curve of the graph being concave down, that is, shaped like a parabola open downward. At the points where the second derivative is zero, we do not learn anything about the shape of the graph: it may be concave up or concave down, or it may be changing from concave up to concave down or changing from concave down to concave up. So, to summarize:

• if $$\frac{d^2f}{dx^2}(p)$$ > 0, then $$f(x)$$ is concave up at x = p.<br/>
• if $$\frac{d^2f}{dx^2}(p)$$ < 0, then $$f(x)$$ is concave down at x = p.<br/>
• if $$\frac{d^2f}{dx^2}(p)$$ = 0, then we do not know anything new about the behavior of $$f(x)$$ at x = p.


<font color= E675A7> For example</font>
Take $$f(x) = 3x^3 − 6x^2 + 2x − 1$$ as above.<br/> The derivative of $$f(x)$$ is $$f'(x) = 9x^2 − 12x + 2$$, and $$f''(x) = 18x − 12$$.<br/>
At x = 0, the second derivative of $$f(x)$$ is -12, so we know that the graph of $$f(x)$$ is concave down at x = 0.<br/>
Likewise, at x = 1, the second derivative of $$f(x)$$ is $$f''(1) = 18 · 1 − 12 = 18 - 12 = 6$$<br/>
so the graph of $$f(x)$$ is concave up at x = 1.
