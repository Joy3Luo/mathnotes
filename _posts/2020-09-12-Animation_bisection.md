---
title: Animation of bisection method In MatLab
categories: [Notes]
comments: true
---

```matlab
% Script: Animation of bisection method
% ======================================
% Variables Needed: Bracket [a,b]
%                   Function f(x)
%                   Tolerance 'tol'
% ======================================
% Enter initial bracket [a,b], anonymous function f(x), and tolerance 'tol'
a = 0;
b = 2;
f = @(x) cos(x);
tol = .0001;

% Plot starts here
figure,hold on
xvals = linspace(a,b,200);
plot(xvals,f(xvals),'r-')                         % Plot function f
line([a,b],[0,0])                                 % Plot y=0 line
title('Bisection Method for solving cos(x) = 0','FontSize',24)
set(gca,'FontSize',20)                            % Set axis font size

% Set x and y limits of the plot (ylim should be changed depending on f)
xlim([a b])
ylim([-2 2])

% Bisection Method begins here
if sign(f(a))*sign(f(b)) >= 0
  error('f(a)f(b)<0 not satisfied!') %ceases execution
end

fa=f(a);
fb=f(b);

counter = 0;                         % Counter for number of steps taken

while (b-a)/2>tol
  c=(a+b)/2;
  err = abs(pi/2 - c);               % Keep track of absolute error
  % Plot successive iterates
  h3 = plot(c,f(c),'ro','MarkerFaceColor','red','MarkerSize',10);
  h1 = line([a,b],[-2,-2],'LineWidth',10);  

    % Plot textbox with approximate root
    txt = strcat('Root Estimate =  ',num2str(c));
    txt2 = strcat('Error =  ',num2str(err));
    txt3 = strcat('Iterations = ', num2str(counter));
    h2 = text(.15,-1,txt,'FontSize',24);
    h4 = text(.15,-1.25,txt2,'FontSize',24);
    h5 = text(.15,-.75,txt3,'FontSize',24);
  waitforbuttonpress;

  fc=f(c);
  if fc == 0              %c is a solution, done
    break
  end
  if sign(fc)*sign(fa)<0  %a and c make the new interval
    b=c;fb=fc;
  else                    %c and b make the new interval
    a=c;fa=fc;
  end
  counter = counter + 1;
  % Delete previous iterative steps in plot
  delete(h1), delete(h2), delete(h3), delete(h4), delete(h5)
end

xc=(a+b)/2;              %new midpoint is best estimate
plot(xc,f(xc),'MarkerSize',60);
err = abs(pi/2 - c);
    txt = strcat('Root Estimate =  ',num2str(c));
    txt2 = strcat('Error =  ',num2str(err));
    txt3 = strcat('Iterations = ', num2str(counter));
    h2 = text(.15,-1,txt,'FontSize',24);
    h4 = text(.15,-1.25,txt2,'FontSize',24);
    h5 = text(.15,-.75,txt3,'FontSize',24);

=============================================================

% BISECTION METHOD
% =================================================
% Computes approximate solution of f(x)=0
% Input: anonymous function f; a,b such that f(a)*f(b)<0,
%        and tolerance tol
% Output: Approximate solution xc
% =================================================
function [xc,err] = bisect(f,a,b,tol)
if sign(f(a))*sign(f(b)) >= 0
  error('f(a)f(b)<0 not satisfied!') %ceases execution
end
fa = f(a);
fb = f(b);
k=0;
while (b-a)/2 > tol
  c = (a+b)/2;
  fc = f(c);
  k = k+1;
  fprintf('\tAfter %g steps, root = %.15g\n',k,c)
  if fc == 0              %c is a solution, done
    break
  end
  if sign(fc)*sign(fa) < 0  %a and c make the new interval
    b = c; fb = fc;
  else                    %c and b make the new interval
    a = c; fa = fc;
  end
end
xc = (a+b)/2;               %new midpoint is best estimate

```
