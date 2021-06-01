---
layout: post
title: MatLab - Runge Phenomenon
date: 2020-10-09 23:18 +0800
tags: [MatLab]
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
clear, clf

% Define Runge function on [-1,1]
x = linspace(-1,1,100);
runge = @(x) 1./(1+12*x.^2);
%plot(x,runge(x))

% Obtain polynomial coefficients
xu = linspace(-1,1,15);
yu = runge(xu);
p = polyfit(xu,yu,14);

% Evaluate on finer grid
ypoly = polyval(p,x);  % evaluate polynomial with coefficients p at points x
hold on
plot(xu,yu,'ro','MarkerSize',12)
plot(x,ypoly)
plot(x,runge(x),'LineWidth',2)
%plot(xu,yu,'ro','MarkerSize',12,x,ypoly,'LineWidth',2,'r-',x,runge(x),'LineWidth',2)
hold off
title('Runge Phenomenon (evenly spaced nodes)','FontSize',16)
g = legend({'f(x)', 'p(x)'})
set(g,'FontSize',14)

% =======================================================================
% Evaluate on Chebyshev grid
i = 1:15;
xC = cos((2*i-1)*pi/(2*15));
yC = runge(xC);
p2 = polyfit(xC,yC,14);

% Evaluate on finer grid
ypolyC = polyval(p2,x);  % evaluate polynomial with coefficients p at points x
figure
hold on
plot(xC,yC,'ro','MarkerSize',12)
plot(x,ypolyC)
plot(x,runge(x),'LineWidth',2)
hold off
%plot(xC,yC,'bo','MarkerSize',12,x,ypolyC,'r-','LineWidth',2,x,runge(x),'LineWidth',2)
title('No Runge Phenomenon (Chebyshev nodes)','FontSize',16)
h = legend('f(x)', 'p(x)')
set(h,'FontSize',14);

```
