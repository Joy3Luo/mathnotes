---
title: Homework - Computational Methods HW4
categories: [Homeworks]
comments: true
---

```matlab
%% AMSC 460 - Computational Methods Fall 2020

%%
%
%Due Date: Tuesday, October 13
%
clear all; format compact; close all; syms f(x) x y z

%% HOMEWORK 4 - Problem 1

%%
% Show that the spectral radius ρ(A) of an n × n matrix A satisfies the inequality
% ρ(A) ≤ ||A|| ,where the norm is any matrix operator norm.

%%
img = imread('amsc460hw4p1.PNG'); imshow(img)


%% HOMEWORK 4 - Problem 2

%%
% Consider the following system of equations.
% f1(x, y, z) = x^2 + y^2 + z^2 − 1 = 0,
% f2(x, y, z) = 2x^2 + y^2 − 4z = 0, f3(x, y, z) = 3x^2 − 4y + z^2 = 0
% This system can be concisely represented as F(x) = 0, where F(x) = (f1, f2, f3)^T,
% x = (x, y, z)^T and 0 = (0, 0, 0)^T.

%%
% (i) Find the Jacobian matrix DF(x).
clear all;
syms x y z;
DFx = jacobian([x^2 + y^2 + z^2,2*x^2 + y^2 - 4*z, 3*x^2 - 4*y + z^2], [x, y, z])

%%
% (ii) (MATLAB) Starting with the initial condition x0 = (0.5, 0.5, 0.5)^T, implement 5
% steps of the multivariable Newton method to find the approximation x5.

x0 = [0.5; 0.5 ; 0.5]
i = 0;
while i < 5
    DFx0(1,1) = 2*x0(1); DFx0(1,2) = 2*x0(2); DFx0(1,3) = 2*x0(3);
    DFx0(2,1) = 4*x0(1); DFx0(2,2) = 2*x0(2); DFx0(2,3) = -4;
    DFx0(3,1) = 6*x0(1); DFx0(3,2) = -4; DFx0(3,3) = 2*x0(3);
    Fx0 =[ (x0(1)^2 + x0(2)^2 + x0(3)^2 -1) ; (2*x0(1)^2 + x0(2)^2 - 4*x0(3)); (3*x0(1)^2 - 4*x0(2) + x0(3)^2)];
    S = DFx0\Fx0;
    x1 = x0 - S;
    x0 = x1
    i = i+1;
    fprintf('\tAfter %g steps\n', i)
end


%%
% (iii) Compute the absolute backward error of the approximate solution x5 in the 2-norm.
cond(Fx0 - DFx0*x0)

%%


%% HOMEWORK 4 - Problem 3

%%
% Write down the polynomial that interpolates f(x) = e^x at the points x0 = 0 and
% x1 = 1 in Lagrange form and Newton form (using divided differences). Check that
% these polynomials are the same.

img = imread('amsc460hw4p3.PNG'); imshow(img)


%% HOMEWORK 4 - Problem 4

%%
% The Vandermonde matrix can be badly conditioned and is not ideal for solving
% many interpolation problems. On the other hand, some of this ill-conditioning can
% be mitigated by scaling the data. Suppose we are given data points (x0, y0), ..,(xn, yn)
% with x0 < x1 < ... < xn. Consider scaling the x values by letting zi = xi - α/β
% where α and β are given numbers with β > 0. The data points (xi, yi) change to
% (zi, yi), and the interpolation polynomial changes to
% pn(z) = a0 + a1z + · · · + anzn.

%%
% (a) The original data interval is x0 ≤ x ≤ xn. What is the data interval when using
% z = (x − α)/β? What matrix equation must be solved to find the a’is in the above formula for pn(z)?

img = imread('amsc460hw4p4.PNG'); imshow(img)


%%
% (b) Taking a hint from the previous step, the data will be scaled so that the new
% data interval is instead −1 ≤ z ≤ 1. What must α and β be here?
%%
%    Then z0 = (x0-α)/β = -1  => x0 = -β+α
%    and  zn = (xn-α)/β = 1   => xn =  β+α
%    Then x0 + xn = -β+α+β+α = 2α
%         =>      α = (x0 + xn) / 2
%    and  xn - x0 = β+α - (-β+α) = 2β
%         =>      β = (xn - x0) / 2

%%
% (c) Consider the following population data for the USA over the 100 year period
% between 1900 and 2000.
% The y values represent the population of the USA in millions. Using the direct
% approach (Vandermonde), plot the interpolation function using the original xi
% data. You should use MATLAB’s vander command to construct the Vandermode matrix V .
% Using MATLABs cond commmand, what is the condition
% number cond(V) of the associated Vandermonde matrix V ?

x = [1900 1910 1920 1930 1940 1950 1960 1970 1980 1990 2000];
y = [76.21; 92.23; 106; 123.2; 151.3; 179.3; 203.3; 226.5; 248.8; 281.4; 308.7]*1000000;
V = vander(x)
%%
cond(V)
%%
p = V\y;
t = linspace(1900,2000,11);
f = polyval(p,t);
plot(x,y,'o',t,f,'r-+')
legend({'given y', 'estimate y using Vandermonde'})

%%
% (d) Using the same population data from part (c), scale the data to [−1, 1] and find
% the coefficients for pn(z). What is the condition number in this case? Once the a'is are computed
% the resulting (unscaled) polynomial is
% pn(x) = a0 + a1(x − α/β) + · · ·an(x − α/β)^n.
%
% Plot this function and compare it with the function you found in part (c). Com-
% ment on the difference between the two.

a = (2000+1900)/2; % α = (x0 + xn) / 2
b = (2000-1900)/2; % β = (xn - x0) / 2
disp('Scale the data to [−1, 1]：')
z = (x-a)/b
%%
disp('The new Vandermode matrix V：')
Vz = vander(z)
%%
disp('The new condition number：')
cond(Vz)
%%
disp('the coefficients for pn(z)：')
p2 = Vz\y
%%
t = linspace(-1,1,11);
f2 = polyval(p2,t);
plot(z,y,'o',t,f2,'g-+')
legend({'given y', 'estimate y using Vandermonde'})
%%
%    The y using interpolation function in 4(d) is more accurate,
%    Also the condition number in 4(d) is way smaller than the condition number in 4(c)

```
