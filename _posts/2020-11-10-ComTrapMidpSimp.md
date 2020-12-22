---
title: Composite Numerical Integration
categories: [Notes]
comments: true
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


## <font color= 977FD7> Numerical Integration</font>

We will derive and analyse various numerical methods for approximating definite integrals of the form

$ I(f)=\int_{a}^{b} f(x) d x $

with $ [a, b] $ some finite interval. The approximation of $ I(f) $ is commonly known as numerical integration or quadrature. There are several motivations for performing numerical integration

1. It is often the case that the integrand $ f(x) $ are only known at few points.

2. Not every integrand has an antiderivative that is an elementary function.

3. Even if an explicit antiderivative formula exists, it might not be the most efficient way of computing the definite integral. This is the case when the antiderivative is given as an infinite sum or product.


<font color= E675A7> The simplest method for approximating $ I(f)=\int_{a}^{b} f(x) d x $ is as follows.</font>


Given an integrand $ f(x) $ on $ [a, b], $ construct a family of approximating function $ \left(f_{n}\right), n \geqslant 1, $ where $ n $ refers to the number of subintervals on $ [a, b] . $

Define

$ I_{n}(f):=I\left(f_{n}\right)=\int_{a}^{b} f_{n}(x) d x $

and the error function

$ E_{n}(f):=I(f)-I_{n}(f)=\int_{a}^{b}\left[f(x)-f_{n}(x)\right] d x $

In a relatively simple case, one usually requires that

$ \left\|\|f-f_{n}\right\|\|_{\infty} \longrightarrow 0 $ as $ n \longrightarrow \infty, $

since

$\left\|E_{n}(f)\right\|\leqslant \int_{a}^{b}\left\|f(x)-f_{n}(x)\right\| d x$



$ \leqslant(b-a)\left\|\|f-f_{n}\right\|\|_{\infty} \longrightarrow 0 $ as $ n \longrightarrow \infty $


#### <font color= 6FBCE1> Simple Trapezoidal Rule </font>


We approximate the integrand $ f(x) $ using linear interpolation $ p_{1}(x), $ this simply refers to the straight line joining the points $ (a, f(a)) $ and $ (b, f(b)) . $ Referring to the Lagrange's formula, we have the following approximation

$ f(x) \approx p_{1}(x)=\left(\frac{x-b}{a-b}\right) f(a)+\left(\frac{x-a}{b-a}\right) f(b)=\frac{(b-x) f(a)+(x-a) f(b)}{b-a} $

This gives rise to the Simple Trapezoidal Rule



$ I_{1}(f)=\int_{a}^{b} \frac{(b-x) f(a)+(x-a) f(b)}{b-a} d x=\left(\frac{b-a}{2}\right)[f(a)+f(b)] $

(Simple Trapezoidal)

which is simply the area of trapezoid.


#### <font color= 6FBCE1> Error Analysis </font>


To analyse the error, assume $ f \in C^{2}[a, b] . $ For a linear interpolant, the interpolation error formula (IEF) gives



$ \begin{aligned} f(x)-\frac{(b-x) f(a)+(x-a) f(b)}{b-a} \end{aligned}$
$ \begin{aligned} = f(x)-p_{1}(x) & =(x-a)(x-b) \frac{f^{\prime \prime}(\xi)}{2} \\ &=(x-a)(x-b) f[a, b, x] \end{aligned} $



where $ f[a, b, x] $ is the second order divided difference. since $ g(x)=(x-a)(x-b) \leqslant 0 $ on $ [a, b],$ it follows from the Mean Value Theorem for Integrals that there exists an $ \xi \in[a, b] $ such that

$ E_{1}(f)=\int_{a}^{b} f(x)-p_{1}(x) d x=\int_{a}^{b}(x-a)(x-b) f[a, b, x] d x $

$ =f[a, b, \xi] \int_{a}^{b}(x-a)(x-b) d x $

$ =\left[\frac{f^{\prime \prime}(\eta)}{2}\right]\left[-\frac{1}{6}(b-a)^{3}\right], $ for some $ \eta \in[a, b] $

Writing $ b-a $ as $ h, $ we have



$ E_{1}(f)=-\left[\frac{f^{\prime \prime}(\eta)}{12}\right] h^{3} \quad $ for some $ \eta \in[a, b] $



#### <font color= 6FBCE1> In MatLab </font>

```matlab

function In = trapezcomp(f,a,b,n)

% composite trapezoidal function integrator
%
% INPUTS:
% f: the function to integrate
% a: lower bound of integration
% b:upper bound of integration
% n:number of points
% Initialization

h=(b-a)/n ;
x=a;
%composite rule

In = f(a);
for k=2:n
x=x+h;
In = In + 2.*f(x);
end
In =( In + f(b) ) * h * 0.5;

% end of function
==========================================================
function MF=midpoint_rule(f,a,b,n)
h=(b-a)/n;
ci=linspace( a+h/2, b-h/2, n-1); % ci are your evaluation points
y = f(ci); % This evaluates the function f , which is another matlab function
MF=h*sum(y); % you can just add up the vector y and multiply by h
end

==========================================================

function simps(f,a,b,n)
h=(b-a)/n;
sum_even=0;
for i=1:n/2-1
x(i) = a + 2*i*h;
sum_even = sum_even + f(x(i));
end

sum_odd = 0;
for i=1:n/2
x(i) = a + (2*i-1)*h;
sum_odd = sum_odd + f(x(i));
end

integral = h*(f(a)+2*sum_even+4*sum_odd+f(b))/3; % this needs to be changed accordingly with the specific problem you have at hand , before proceeding the command line
function y = f(x)
y = exp(x);
```
