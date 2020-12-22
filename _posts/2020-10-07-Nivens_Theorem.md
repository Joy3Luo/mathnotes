---
layout: post
title: Niven's Theorem2
date: 2020-10-07 23:18 +0800
tags: [Theorem]
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

## <font color= 977FD7> Niven's Theorem</font>

Niven's theorem states that if $\frac{x}{\pi}$ and $sin x$ are both <font color= E675A7> rational</font>, then the sine takes values 0, ±$\frac{1}{2}$ and ±1.<br/>
 <br/>Particular cases include<br/>
$sin (\pi) = 0 $<br/>
$sin (\frac{\pi}{2}) = 1 $<br/>
$sin (\frac{\pi}{6}) = \frac{1}{2} $<br/>

#### <font color= 6FBCE1> Question: when is sin(x) rational?</font>
If x is in whole degrees, then $x^∘=πx/180$ radians $=πp/q$ radians, so we wish to find all rational multiples of $π$ so that $sin(πp/q)$ is rational. <br/>

If $p/q∈\mathbb{Q}$, then $e^{±iπp/q}$ is an algbraic integer since $(e^{±iπp/q})^q−(−1)^p = 0$. Thus, $2sin(πp/q)=−i(e^{iπp/q}−e^{−iπp/q})$ is the difference and product of algebraic integers, and therefore an algebraic integer. However, the only rational algebraic integers are normal integers. Thus, the only values of $sin(πp/q)$ which could be rational, are those for which $2sin(πp/q)$ is an integer, that is $sin(πp/q)∈${−1,−12,0,12,1}.

-----------------------------------------
Referenced on Wolfram|Alpha:
<a href="https://www.wolframalpha.com/input/?i=niven%E2%80%99s+theorem">Niven's Theorem</a> theme.
