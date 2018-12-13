---
title: 'Calculating By Hand (I): $\ln2$'
layout: post
date: 2018-08-16 14:51:33 -0400
tag: [infinite series]
---
Over the Simcoe Day long weekend, I got back into one of my (many) nerdy interests: pen-and-paper calculation.

No, not basic arithmetic (${+}{-}{\times}{\div}$); anyone can multiply two 10-digit numbers together, if they're patient (and careful!) enough. I'm talking about the _funky_ buttons on the calculator, like $\sqrt[n]{\quad}$, $\ln$, $\exp$, $\sin$, $\pi$, &hellip; They never taught you how to do _those_ in school, did they?

In this series of posts, I'll be exploring different ways of calculating mathematical functions and constants by hand.

<!--more-->
{% comment %}
<!-- ## Why calculate by hand?

First, some thoughts on why you might want to learn this skill. (This tangentially-related ramble can be safely skipped.)

> I won't pretend that you need this skill in daily life. (Imagine: "Grapes cost $\sqrt{2+\sqrt2}$ dollars per kg at store A but $e^{3/5}$ dollars per kg at store B; which is cheaper?" Or worse: "You find yourself locked in a room with nothing but a pencil, and the passcode for the door is the first 10 decimal digits of $\sin1^\circ$.") Even in a technical setting, a calculator or computer is usually within reach.
>
> However, I feel that as a math major, it's easy to get caught up in the abstract, without really being familiar with basics. Similarly, in computer science, it's easy to throw all the number-crunching to the machine without knowing anything that happens under the hood. I imagine that many math/CS graduates routinely work with Galois extensions of $\bb Q$, or million-variable optimisation problems for neural networks, but can't work out whether $\ln2$ is closer to 0.6 or 0.7; and to me that seems somewhat strange.
>
> In that regard, pen-and-paper calculation of mathematical functions can be seen as some form of "advanced numeracy," the natural next step in the skill progression of counting, doing groceries, and filing taxes.
>
> Then again, the _real_ reason I picked up this skill was because it was _fun_. Isn't it fun to figure out, by yourself, whether $\ln2$ is closer to 0.6 or 0.7?

With that being said, it's time to get down to the math! -->
{% endcomment %}
## The goal: $\ln2$

For concreteness, we first need to pick a number to compute, preferably something that looks simple but lies beyond what we already know how to calculate. $\sqrt2$, $\ln2$, $e$ and $\pi$ are all good choices for this purpose. Here we focus on $\ln2$ to illustrate the general principles of pen-and-paper calculation, but we will also look at the others in future posts.

For reference, the humble calculator can give us the answer instantly:

$$\ln2=0.693147181\ldots$$

With more computing power, we can of course extend this even further; the current record is [500 billion digits](http://www.numberworld.org/digits/Log(2)/).

We will be a bit less ambitious, and just ask to compute by hand __the value of $\ln2$ to 8 decimal places__. In fact, here we have a subtle issue with rounding off (consider $0.999\ldots$ and $1.000\ldots$), but for our purposes we will be satisfied with any answer that is within $\frac12\times10^{-8}$ of the true value.

The first step is to notice that we can only make progress by using properties of the $\ln$ function. Each property can lead to an algorithm to compute the digits of $\ln2$, which can be more or less suited to hand calculation. We will consider three different approaches below.

## $\ln$ as an inverse function

The most obvious approach might be to use the fact that $\ln$ is the inverse function to $\exp$; ie. calculating $\ln2$ is equivalent to solving the equation $e^x=2$. For instance, we might use the Newton method on $f(x)=e^x-2$:

$$x_{n+1}=x_n-\frac{f(x_n)}{f'(x_n)}=x_n-1+\frac2{e^{x_n}}$$

{% comment %}
% The problem is that to solve this nonlinear equation, we now need to make _many_ evaluations of the $$\exp$$ function!

% For example, we can use the method of bisection:

% $$\begin{aligned}
% e^0=1.000<2&\implies0<\ln2\\
% e^1\approx2.718>2&\implies0<\ln2<1\\
% e^{1/2}\approx1.649<2&\implies\frac12<\ln2<1\\
% e^{3/4}\approx2.117>2&\implies\frac12<\ln2<\frac34\\
% e^{5/8}\approx1.868<2&\implies\frac58<\ln2<\frac34\\
% &\vdots
% \end{aligned}$$
% To go further with this approach, we need to repeatedly evaluate the $$\exp$$ function, or calculate fractional powers of 2.


% Iterating the above with initial guess $$x_0=1$$ gives

% $$\begin{aligned}
% x_1&=1-1+\frac2{e^1}\\
% &\approx0.736\\
% x_2&=0.736-1+\frac2{e^{0.736}}\\
% &\approx0.694\\
% &\vdots
% \end{aligned}$$

{% endcomment %}

Here we immediately run into a problem: we have traded one evaluation of $\ln$ for _several_ evaluations of $\exp$ --- which we also don't know how to calculate by hand!

This is a general feature of root-finding algorithms: the function needs to be computed at several points to close in on the root. As such, root-finding could be valuable for functions with easily computed inverses, such as square roots, but are of no help for finding $\ln2$.


## $\ln$ and integration

Another idea is to notice that $\ln x$ is the antiderivative of $\frac1x$, so

$$\ln2=\int_1^2\!\frac{dx}x.$$

Now we can approximate this integral by splitting up the interval $[1,2]$ into $n$ equal parts, and applying a quadrature rule (in other words, performing numerical integration). For instance, the right Riemann sum for this integral is

$$\begin{aligned}
\ln2&\approx\frac1n\left(\frac1{1+\frac1n}+\frac1{1+\frac2n}+\cdots+\frac12\right)\\
&=\frac1{n+1}+\frac1{n+2}+\cdots+\frac1{2n}.
\end{aligned}$$

A more accurate estimate is given by the trapezoidal rule:

$$\begin{aligned}
\ln2&\approx\frac1n\left(\frac{\frac12}1+\frac1{1+\frac1n}+\frac1{1+\frac2n}+\cdots+\frac{\frac12}2\right)\\
&=\frac{\frac12}n+\frac1{n+1}+\frac1{n+2}+\cdots+\frac{\frac12}{2n}\\
&=\frac1{n+1}+\frac1{n+2}+\cdots+\frac1{2n-1}+\frac3{4n}.
\end{aligned}$$

For instance, choosing $n=5$ gives:

$$\ln2\approx\frac16+\frac17+\frac18+\frac19+\frac3{20}:\qquad
\begin{aligned}
&\mathbin{\phantom{+}}
  0.16667\\
&+0.14286\\
&+0.125\\
&+0.11111\\
&+0.15\\
\hline
&\mathbin{\phantom{=}}
0.69564\\
\hline
\end{aligned}$$

This is $2.5\times10^{-3}$ off the correct value, which seems great for just 5 terms. Of course, choosing larger $n$ will give better results.

However, before committing to this method and going into a reciprocal calculating frenzy, it would be prudent to perform an error analysis. The trapezoid rule has error $O(\frac1{n^2})$. To get an error of less than $\frac12\times10^{-8}$, we would need $n\sim\sqrt{2\times10^8}$ --- on the order of 10000 terms!

More generally, if a quadrature rule gives error $O(\frac1{n^m})$, then we need $O(10^{k/m})$ terms to get to $k$-digit accuracy. Hence the exponential growth in the number of terms required affects not only the trapezoidal rule, but also higher-order methods such as Simpson's rule. There are other methods for numerical integration, such as Gaussian quadrature and Romberg integration, which converge much faster, but require taking square roots or dividing by large integers. Hence, it is hard to implement numerical integration methods by hand to more than a couple of digits of accuracy.


## $\ln$ and power series

A third approach is to look at the power series for $\ln$ around 1, namely

$$\ln(1+x)=x-\frac{x^2}2+\frac{x^3}3-\frac{x^4}4+-\cdots,\qquad x\in(-1,1].$$

The obvious substitution is $x=1$, which gives

$$\ln2=1-\frac12+\frac13-\frac14+-\cdots.$$

As pretty as this series is, it is nearly useless for hand computation: the error of this alternating series is roughly the size of the last term used, ie. $O(\frac1n)$ if we use $n$ terms. This translates to $\sim10^8$ terms for 8-digit accuracy, which is even worse than using the trapezoidal rule.

> As an aside, note that
>
> $$\begin{aligned}
&1-\frac12+\frac13-\frac14+\cdots+\frac1{2n-1}-\frac1{2n}\\
&=\left(1+\frac12+\frac13+\cdots+\frac1{2n}\right)-2\left(\frac12+\frac14+\cdots+\frac1{2n}\right)\\
&=\left(1+\frac12+\frac13+\cdots+\frac1{2n}\right)-\left(1+\frac12+\cdots+\frac1n\right)\\
&=\frac1{n+1}+\frac1{n+2}+\cdots+\frac1{2n},
\end{aligned}$$
>
> which is just the right Riemann sum that we have seen previously.

A smarter idea is to substitute $x=-\frac12$, yielding

$$\begin{aligned}
\ln2&=-\ln\frac12\\
&=\frac12+\frac12\left(\frac12\right)^2+\frac13\left(\frac12\right)^3+\frac14\left(\frac12\right)^4+\cdots,
\end{aligned}$$

which converges faster than the geometric series with ratio $\frac12$. In other words, the error of this series after $n$ terms is $O(\frac1{2^n})$, so only $O(k)$ terms are needed to get $k$-digit accuracy. Great!

Let's try this out numerically with the first 5 terms:

$$\ln2\approx\frac12+\frac1{2\cdot2^2}+\frac1{3\cdot2^3}+\frac1{4\cdot2^4}+\frac1{5\cdot2^5}:\qquad
\begin{aligned}
&\mathbin{\phantom{+}}
0.5\\
&+\phantom{0.}125\\
&+\phantom{0.0}4167\\
&+\phantom{0.0}1563\\
&+\phantom{0.00}625\\
\hline
&\mathbin{\phantom{+}}0.68855\\
\hline
\end{aligned}$$

We also have a good error bound:

$$\begin{aligned}
\frac1{6\cdot2^6}+\frac1{7\cdot2^7}+\cdots&<\frac16\left(\frac1{2^6}+\frac1{2^7}+\cdots\right)\\
&=\frac1{6\cdot2^5}=5.2\times10^{-3},
\end{aligned}$$

which is comparable to the actual error of $4.6\times10^{-3}$.

Similarly, we have an error bound of $\frac1{(n+1)2^n}$ after the first $n$ terms of the series. This is smaller than $\frac12\times10^{-8}$ when $n\geq23$, ie. only 23 terms are needed to get 8-digit accuracy.

## Conclusion

We now have a working algorithm for calculating $\ln2$, namely by using 23 terms of the power series expansion of $\ln(1-\frac12)$. Although not as ridiculously impossible as the other methods we have seen, this is still no small amount of manual work --- perhaps a weekend project, if you're so inclined.

There is a natural question to ask at this point: "Can we do better?" Going down this rabbit hole is when the fun really begins. In the next post, we will cover some neat tricks to cut down the amount of computation even further.

{% comment %}
()*&
{% endcomment %}
