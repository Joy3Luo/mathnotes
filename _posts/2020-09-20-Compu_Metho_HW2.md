---
layout: post
title: Computational Methods HW2
date: 2020-09-20 23:18 +0800
tags: [UMD]
---

<!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-TG0XJZG53F"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'G-TG0XJZG53F');
  </script>

```matlab
%% AMSC 460 - Computational Methods Fall 2020

%%
%
% Due Date: Tuesday, September 22
%
clear all; format compact; close all; syms f(x) x y

%% HOMEWORK 2 - Problem 1

%%
% Find the multiplicity of the root r = 0 of f(x) = 1 − cos(x). Find the forward and
% backward errors for the approximate root xˆ = 10^−5.

%%
f = 1-cos(x);    % f(0) = 0, so r = 0 is a root.
diff(f);         % ans = sin(x), sin(0)=0, so r = 0 is a root of multiplicity at least 2
diff(sin(x));    % ans = cos(x), cos(x)=1, so r = 0 is a root of multiplicity 2.
%%
%    So we see that the root r = 0 has multiplicity 2.

%%
r = 0; x_hat = 10^-5; f = @(x) 1-cos(x);
fwd_err = abs(r - x_hat)
bwd_err = abs(f(x_hat))

%% HOMEWORK 2 - Problem 2

%%
% Newton’s method for solving f(x) = 0 requires computing the derivative of f each
% iteration. Suppose instead that the initial slope d = f'(x0）is kept throughout the
% iterations, i.e xn+1 = xn − f(xn)/d.
% Suppose that the root r is simple (so that f'(r)≠ 0). Find a condition on the initial
% slope d that ensures the scheme will be locally convergent. What is the order of
% convergence?

%%
%    Accordint to our class note, Newton is an FPI, with g(x) = x - f(x)/f'(x)
%    In this case, we have g(x) = x - f(x)/d
%                     then g(r) = r - f(r)/d = r - f(r)/f'(x0)
%    To get local convergence, we must have g'(r) = 1 - [ f'(x0)f'(r)- f(r)f''(x0)/[f'(x0)]^2] = 0 < 1
%               since f(r)=0     so         g'(r) = 1 - [ f'(x0)f'(r)/[f'(x0)]^2] = 0 < 1
%                              then             1 =  f'(x0)f'(r)/[f'(x0)]^2
%                                     f'(x0)f'(r) = [f'(x0)]^2
%                                           f'(r) = f'(x0)
%    Given that f'(r)≠ 0 so d = f'(x0) ≠ 0       <----  This is the condition for d
%    
%    Assume f(x)is a continuous function with a continuous second derivative,
%    and f(x) is defined on an interval I = [r-ε,r+ε], with ε> 0.
%    Given that f(r) = 0 and f''(r) ≠ 0
%    Want to show there exists a constant A such that |f''(x)|/|f'(y)| ≤ A ∀x,y∈I
%    If the initial guess x0 is suciently close to the root r
%    then the sequence {xn} converges quadratically to the root r.
%    i.e the order of cpnvergence is 2.
%    
%    Proof:
%    We assume that x_n∈ I. Since f(r) = 0,
%    A Taylor expansion of f(x) at x = x_n, evaluated at x = r is:
%    0 = f(r) = f(x_n)+(r - xn)f'(x_n) + [(r-x_n)^2 / 2] f''(ξ_n)
%    where ξ_n is between r and x_n, and hence ξ∈I
%    Then we have r - x_n = [ -2f(x_n) - f''(ξ_n)(r - x_n)^2 ] / 2f'(x_n)
%    Since x_n+1 are the Newton iterates so we have
%    r - x_n+1 = r - x_n + [f(x_n)/f'(x_n)] = - [f''(ξ_n)(r - x_n)^2]/2f'(x_n)
%    Hence | r - x_n+1 | ≤ [(r - x_n)^2 / 2]*A ≤ |r-x_n|/2  ≤ ……≤ 2^(1-n) *|r-x_0|
%    which implies that x_n -> r as n ->∞
%    
%    To show that the convergence rate of {x_n} to r is quadratic.
%    Since ξ_n is between the root r and x_n, it also converges to r as n->∞
%    The derivatives f' and f''are continuous and therefore we can write
%    lim     |x_n+1 - r| / |x_n - r|^2 =  |f''(r) / 2f'(r)|
%    n ->∞  
%    which implies the quadratic convergence of {x_n} to r.   QED


%% HOMEWORK 2 - Problem 3

%%
% Explain why between 2^53 and 2^54, the only double precision floating point numbers
% that exist are the even numbers.
eps(2^53)
%%
%    We got eps(2^53) = 2 and we know 2^53 is an even number.
%    So the smalles ε for 2^53 is 2, which means we can add 2 to 2^53 to get the next
%    floating point, the distance between each floating point is 2. 2^53 is an even number
%    and even number plus 2 is also enen, thus the only double precision floating point
%    numbers between 2^53 and 2^54 are the even numbers.

%% HOMEWORK 2 - Problem 4

%%
% (a) Express x = (12.8)_10 as a double-precision IEEE float fl(x), using the round-tonearest rule.
%%
%    (12.8)_10 = (12)_10 + (0.8)_10
%    Integer part: 12/2 = 6 remainder = 0
%                   6/2 = 3 remainder = 0
%                   3/2 = 1 remainder = 1
%                   1/2 = 0 remainder = 1   -> (12)_10 = (1100)_2
%    Fractional part: 0.8 * 2 = 1.6 = 0.6 + 1
%                     0.6 * 2 = 1.2 = 0.2 + 1
%                     0.2 * 2 = 0.4 = 0.4 + 0                     ____
%                     0.4 * 2 = 0.8 = 0.8 + 0    -> (0.8)_10 = (0.1100)_2
%                         ____                             ____
%    So (12.8)_10 = (1100.1100)_2, fl(x) = 1.[10011....01] 1001 x 2^3
%       
%    Sine b_53 = 1 and the rest of bits are Not all zero,
%    1. By truncating,  ____                       ____              [in base 10]
%        we lose R = (0.1001) x 2^(-52) x 2^3 = (0.1001) x 2^(-49) = 0.6 x 2^(-49)
%    2. By the round-tonearest rule, we add 1 to the b_52 bit to get an addition
%        of 2^(-52) x 2^3 = 2^(-49)
%    Thus we have fl(12.8) = 12.8 + 2^(-49) - 0.6 x 2^(-49) = 12.8 + 0.4 * 2^(-49)


%%
% (b) Compute the relative error d = |x − fl(x)|/|x| exactly as a base-10 number, and
% show that d satisfies the upper bound d ≤ε_mach/2.

d = abs(0.4 * 2^(-49))/abs(12.8)
eps/2 - d
%%
%    ans = 5.551115123125783e-17 > 0 so the d satisfies the upper bound d ≤ε_mach/2.

%% HOMEWORK 2 - Problem 5

%%
% Let x = 2. To avoid subtraction of nearly equal numbers, find an alternative form
% f~(h) ≡ f(h) to evaluate f(h) = x^4 − (x − h)^4 /h for small h.
% Compute f(h) using MATLAB based on the formula (1) and the alternative form
% f~(h) you propose, and report your results for h = 10^−1, 10^-2, ..., 10^-15 on a
% semilogx plot (both functions should be on the same graph). What is lim_h→0 f(h)?
% Does your modified function compute more accurately for small h?

x = 2;
f = @(h) (x^4 - (x-h).^4)./(h);


%%
%    fNew(h) = [x^4 − (x − h)^4 /h] * [(x^4 + (x − h)^4 )/(x^4 + (x − h)^4)]
%            = (x^8 - (x − h)^8 )/h(x^4 + (x − h)^4)
%    factor (x^8 - (x − h)^8 ) = h(x^4+(x-h)^4)(x^2+(x-h)^2)(2x-h)
%    Cancel the common factor : h(x^4 + (x − h)^4)
%    fNew(h) = (2x^2-2xh+h^2)(2x-h) = 4x^3 - 6x^2h + 4xh^2 - h^3                       
%%
fNew = @(h) ( 4*(x^3) - 6*(x^2)*h + 4*x*(h.^2) - (h.^3));
x = 10*ones(1,15); y = 1:1:15; h = x.^ (-y);
semilogx(h,f(h),h,fNew(h),'--')
title 'subtracting of nearly equal numbers'; legend({'f(h)','fNew(h)'});

%%
%    As h→0, the lim_h→0 f(h) should be 32. However, for very small h the error starts
%    increasing due to the subtraction of nearly equal numbers.
%    My modified function compute more accurately for small h, we can see in the graph,
%    the dash line represent the modified function and lim_h→0 fNew(h) = 32.

%% HOMEWORK 2 - Problem 6

%%
% Consider a right triangle whose legs are of length 3344556600 and 1.2222222 (seven
% 2’s). Using MATLAB to compute, how much longer is the hypotenuse than the
% longer leg? Explain how you arrived at your answer.
a = 3344556600; b = 1.2222222;
c = sqrt(vpa(a)^2 + vpa(b)^2)
c-a

%%
%    Thus the length of the hyphotenuse os greater than the length of the longer side by
%    2.233221447310594e-10
%    vpa(x) uses variable-precision floating-point arithmetic (VPA) to evaluate each element
%    of the symbolic input x to at least d significant digits, where d is the value of the digits
%    function. The default value of digits is 32. If we calculate c = sqrt(a^2+b^2) directily
%    we will get c = 0 because the square of side a is way too big than the square of side b,
%    so due to cancellation of nearly equal numbers, Matlab will "ignore" b and return c=sqrt(a^2).
%    
%    
%%
% If we can not use vpa(x) to solve this problem, we can do:
%%
%    c - a = √(a^2 +b^2) - a = [√(a^2 +b^2) - a]× [√(a^2 +b^2) + a]/[√(a^2 +b^2) + a]
%                             = [(a^2 + b^2) - a^2] / [√(a^2 +b^2) + a]
%                             = b^2 / [√(a^2 +b^2) + a]
b^2 / (sqrt(a^2+b^2)+a)
%%
%    Thus we got the same answer c - a = 2.233221447310594e-10

```
