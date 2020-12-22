---
layout: post
title: Gaussian Quadrature
date: 2020-11-23 23:18 +0800
tags: [Notes]
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


## <font color= 977FD7>Gauss–Hermite quadrature</font>

Gauss-Hermite quadrature is used for integrating functions of the form $ \int\limits_{-\infty}^{\infty} f(x) e^{-x^{2}} \ dx $ over the infinite interval $ [-{\infty}, +{\infty}]$.

With respect to the inner product $ <f,g> = \int\limits_{-\infty}^{\infty} f(x) g(x)w(x) \ dx $,  the Hermite polynomials $H_{n}(x) = (-1)^{n} e^{x^{n}} (\frac{d^{n}}{dx^{n}})( e^{-x^{2}})$ for n > 0, and $H_{0}(x) = 1$ form an orthogonal family of polynomials with weight function $w(x) = e^{-x^{2}}$ on the entire x-axis.

#### <font color= 6FBCE1>In MatLab</font>

This function determines the abscisas (x) and weights (w) for the Gauss-Hermite quadrature of order n>1, on the interval $ [-{\infty}, +{\infty}]$.

This function is valid for any degree n≥2, as the companion matrix (of the n'th degree Hermite polynomial) is constructed as a symmetrical matrix, guaranteeing that all the eigenvalues (roots) will be real.

```matlab
function [x, w] = GaussHermite_2(n)
```

Building the companion matrix CM:

  CM is such that det(xI-CM)=L<sub>n</sub>(x), with L_n the Hermite polynomial under consideration. Moreover, CM will be constructed in such a way that it is symmetrical.

```matlab
i   = 1:n-1;
a   = sqrt(i/2);
CM  = diag(a,1) + diag(a,-1);
```
Determining the abscissas (x) and weights (w):
  - since det(xI-CM)=L<sub>n</sub>(x), the abscissas are the roots of the characteristic polynomial, i.d. the eigenvalues of CM;
  - the weights can be derived from the corresponding eigenvectors.


```matlab
[V L]   = eig(CM);
[x ind] = sort(diag(L));
V       = V(:,ind)';
w       = sqrt(pi) * V(:,1).^2;
```

## <font color= 977FD7>Gauss-Laguerre Quadrature</font>

Gauss-Laguerre quadrature is used for integrating functions of the form $ \int\limits_{0}^{\infty} f(x) e^{-x} \ dx $ over the interval $ [0, +{\infty}]$.

With respect to the inner product $ <f,g> = \int\limits_{0}^{\infty} f(x) g(x)w(x) \ dx $,  the Laguerre polynomials $L_{n}(x) = e^{x} (\frac{d^{n}}{dx^{n}})( x^{n} e^{-x})$ for n > 0, and $L_{0}(x) = 1$ form an orthogonal family of polynomials with weight function $w(x) = e^{-x}$ on the positive  x-axis.


#### <font color= 6FBCE1>In MatLab</font>

This function determines the abscisas (x) and weights (w) for the Gauss-Laguerre quadrature of order n>1, on the interval $ [0, +{\infty}]$.

Unlike the function 'GaussLaguerre', this function is valid for n≥34. This is due to the fact that the companion matrix (of the n'th degree Laguerre polynomial) is now constructed as a symmetrical matrix, guaranteeing that all the eigenvalues (roots) will be real.

```matlab
function [x, w] = GaussLaguerre_2(n, alpha)
```

Building the companion matrix CM:

CM is such that det(xI-CM)=L_n(x), with L_n the Laguerree polynomial under consideration. Moreover, CM will be constructed in such a way that it is symmetrical.

```matlab
i   = 1:n;
a   = (2*i-1) + alpha;
b   = sqrt( i(1:n-1) .* ((1:n-1) + alpha) );
CM  = diag(a) + diag(b,1) + diag(b,-1);
```
Determining the abscissas (x) and weights (w):
- since det(xI-CM)=L_n(x), the abscissas are the roots of the characteristic polynomial, i.d. the eigenvalues of CM;
- the weights can be derived from the corresponding eigenvectors.

```matlab
[V L]   = eig(CM);
[x ind] = sort(diag(L));
V       = V(:,ind)';
w       = gamma(alpha+1) .* V(:,1).^2;
```


## <font color= 977FD7>Gauss-Legendre Quadrature</font>
Gauss-Laguerre quadrature is used for integrating functions of the form $ \int\limits_{a}^{b} f(x) e^{-x} \ dx $ over the interval $ [a, b]$.



#### <font color= 6FBCE1>In MatLab</font>

This function determines the abscisas (x) and weights (w) for the Gauss-Legendre quadrature, of order n>1, on the interval [-1, +1].        

Unlike many publicly available functions, 'GaussLegendre_2' is valid for n>=46. This is due to the fact that 'GaussLegendre_2' does not rely on the build-in Matlab routine 'roots' to determine the roots of the Legendre polynomial, but finds the roots by looking for the eigenvalues of an alternative version of the companion matrix of the n'th degree Legendre polynomial. The companion matrix is constructed as a symmetrical matrix, guaranteeing that all the eigenvalues (roots) will be real. On the contrary, the 'roots' function uses a general form for the companion matrix, which becomes unstable at higher orders n, leading to complex roots.        

```matlab
function [x, w] = GaussLegendre_2(n)
```

Building the companion matrix CM:

CM is such that det(xI-CM)=P_n(x), with P_n the Legendre polynomial under consideration. Moreover, CM will be constructed in such a way that it is symmetrical.
```matlab
i   = 1:n-1;
a   = i./sqrt(4*i.^2-1);
CM  = diag(a,1) + diag(a,-1);
```
Determining the abscissas (x) and weights (w):
- since det(xI-CM)=P_n(x), the abscissas are the roots of the characteristic polynomial, i.d. the eigenvalues of CM;
- the weights can be derived from the corresponding eigenvectors.

```matlab
[V L]   = eig(CM);
[x ind] = sort(diag(L));
V       = V(:,ind)';
w       = 2 * V(:,1).^2;
```
