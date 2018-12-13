---
title: 'Measure Theory (XIII): Convolution on $L^p(\bb R)$'
layout: post
tag: [measure theory]
date: 2018-11-22 15:46:08 +0800
---

In this section, we investigate the convolution operation on $L^p(\bb R)$, which is a form of averaging of functions. More generally, all of the results below have analogues in $L^p(\bb R^n)$.

<!--more-->

## Translation of functions

{% comment %}
<!-- Note that the Lebesgue measure $\lambda$ on $\bb R$ is translation invariant. Hence we expect that the Lebesgue integral for a function is also translation invariant. More specifically, given $y\in\bb R$ and $f$ a Lebesgue measurable function $f:\bb R\to[-\infty,\infty]$, define the translation $\tau_yf:\bb R\to[-\infty,\infty]$ by

$$(\tau_yf)(x)=f(x-y).$$

Note that $\tau_yf$ is Lebesgue measurable, since

$$(\tau_yf)^{-1}(a)=y+f^{-1}(a)\coloneqq\{y+s\,:\,s\in f^{-1}(a)\},$$

and the translation invariance of $\lambda$ implies that translates of Lebesgue measurable sets are also Lebesgue measurable.

Now if $\varphi=\sum_{k=1}^na_k\chi_{E_k}$ is a Lebesgue measurable step function, then

$$\begin{aligned}
\int\!\tau_y\varphi\,d\lambda&=\sum_{k=1}^na_k\lambda(y+E_k)\\
&=\sum_{k=1}^na_k\lambda(E_k)\\
&=\int\!\varphi\,d\lambda.
\end{aligned}$$

Thus if $g\geq0$ is measurable, pick a sequence of measurable step functions $0\leq\varphi_1\leq\varphi_2\leq\cdots$ with limit $g\geq0$, so $0\leq\tau_y\varphi_1\leq\tau_y\varphi_2\leq\cdots$ is a sequence of measurable step functions with limit $\tau_yg$. By MCT, we have

$$\begin{aligned}
\int\!\tau_yg\,d\lambda&=\lim_{n\to\infty}\int\!\tau_y\varphi_n\,d\lambda\\
&=\lim_{n\to\infty}\int\!\varphi_n\,d\lambda\\
&=\int\!g\,d\lambda.
\end{aligned}$$

Hence we have the following: -->
{% endcomment %}

Recall the following proposition during our study of [the Lebesgue measure]({% post_url 2018-10-24-measure-theory-viii %}):

__Proposition__: Let $f:\bb R^n\to[-\infty,\infty]$, $x\in\bb R^n$, and $c>0$. Define $g(\omega)=f(\omega-x)$ and $h(\omega)=f(\frac\omega c)$. Then:
1. $f$ is Lebesgue measurable if and only if $g$ is Lebesgue measurable, if and only if $h$ is Lebesgue measurable;
2. $f$ is Lebesgue integrable if and only if $g$ is Lebesgue integrable, if and only if $h$ is Lebesgue integrable, in which case we have

$$\int\!g\,d\lambda=\int\!f\,d\lambda,\qquad\int\!h\,d\lambda=c^n\int\!f\,d\lambda.\ \qed$$

Essentially, this says that the Lebesgue measure behaves as expected under a linear change of variables.

Given $y\in\bb R$ and $f$ a Lebesgue measurable function $f:\bb R\to[-\infty,\infty]$, define the translation $\tau_yf:\bb R\to[-\infty,\infty]$ by

$$(\tau_yf)(x)=f(x-y).$$

Then we can restate part of the above proposition as follows:

__Proposition__: For any Lebesgue integrable function $f$ and $y\in\bb R$, we have $\int\\!\tau_yf\,d\lambda=\int\\!f\,d\lambda$. $\qed$

<!-- __Proof__: Note that

$$\begin{aligned}
\int\!\tau_yf\,d\lambda&=\int\!\tau_yf^+\,d\lambda-\int\!\tau_yf^-\,d\lambda\\
&=\int\!f^+\,d\lambda-\int\!f^-\,d\lambda=\int\!f\,d\lambda.\ \qed
\end{aligned}$$ -->

__Corollary__: If $1\leq p\leq\infty$ and $f\in L^p(\bb R)$, then $\tau_yf\in L^p(\bb R)$ and $\\|\tau_yf\\|_p=\\|f\\|_p$. $\qed$

__Proposition__: If $1\leq p<\infty$ and $f\in L^p(\bb R)$, then $\lim_{y\to0}\\|\tau_yf-f\\|_p=0$.

__Proof__: If $\tilde f(x)=f(-x)$ then

$$\lim_{y\to0^-}\|\tau_yf-f\|_ p=\lim_{z\to0^+}\|\tilde f-\tau_z\tilde f\|_ p,$$

so it suffices to prove the limit for $y\to0^+$.

For the half-open interval $H=[a,b)$, we have

$$\|\tau_y\chi_H-\chi_H\|_p=\|\chi_{[b,b+y)}-\chi_{[a,a+y)}\|_ p\leq2y^{1/p},$$

which goes to $0$ as $y\to0^+$. Hence for linear combinations of such functions $\psi=\sum_{k=1}^na_k\chi_{H_k}$, we have

$$\|\tau_y\psi-\psi\|_ p\leq\sum_{k=1}^na_k\|\tau_y\chi_{H_k}-\chi_{H_k}\|_ p,$$

which also goes to $0$ as $y\to0^+$.

Take any $\eps>0$. For $g\in\mc L^p(\bb R)$ with $g\geq0$, take a sequence of measurable step functions $0\leq\varphi_1\leq\varphi_2\leq\cdots$ with limit $g$. By MCT, there exists some $\\|g-\varphi_j\\|_ p<\frac\eps5$.

Write $\varphi_j=\sum_{k=1}^nb_k\chi_{E_k}$. For each $E_k$, there exists pairwise disjoint half-open intervals $H_{k,l}\subseteq E_k$ with

$$\lambda(E_k\backslash\bigcup_lH_{k,l})<\frac\eps{5nb_k^p},$$

so writing $\psi=\sum_{k=1}^nb_k\sum_l\chi_{H_{k,l}}$, we have

$$\|\varphi_j-\psi\|_ p\leq\sum_{k=1}^n\frac\eps{5n}\leq\frac\eps5.$$

Now

$$\begin{aligned}
\|\tau_yg-g\|_ p&\leq\|\tau_y(g-\psi)\|_ p+\|\tau_y\psi-\psi\|_ p+\|\psi-g\|_ p\\
&<\frac{2\eps}5+\frac\eps5+\frac{2\eps}5=\eps
\end{aligned}$$

for all small enough $y>0$, so $\\|\tau_yg-g\\|_ p\to0$ as $y\to0^+$ for all nonnegative $g\in\mc L^p(\bb R)$.

Finally, for general $f\in\mc L^p(\bb R)$, we have

$$\|\tau_yf-f\|_ p\leq\|\tau_yf^+-f^+\|_ p+\|\tau_yf^--f^-\|_ p,$$

which goes to $0$ as $y\to0^+$, and we are done. $\qed$

Note that the above proposition is false for $p=\infty$; an easy counterexample is $f=\chi_{[0,1]}$.

## Convolution of functions

We are now ready to define the convolution of two functions. The proof of existence also gives us an estimate of its $p$-norm.

__Proposition__: Let $1\leq p\leq\infty$, $f\in L^p(\bb R)$, and $g\in L^1(\bb R)$. Then:
- For $\lambda$-a.e. $x\in\bb R$, the function $h_x(y)\coloneqq f(x-y)g(y)$ is Lebesgue integrable; and
- The function

  $$(f* g)(x)\coloneqq\begin{cases}\int\!h_x(y)\,d\lambda(y),&\text{if the integral exists}\\0,&\text{otherwise}\end{cases}$$

  satisfies $f* g\in L^p(\bb R)$ and $\\|f* g\\|_ p\leq\\|f\\|_ p\\|g\\|_ 1$.

__Proof__: We first prove the case $p=\infty$. Here we have

$$|(f* g)(x)|\leq\|h_x\|_ 1\leq\|f\|_ \infty\|g\|_ 1$$

by Hölder's inequality, and we are done.

Now assume $1\leq p<\infty$, and let $q$ be the conjugate index of $p$ (ie. $\frac1p+\frac1q=1$). Take any $u\in L^q(\bb R)$ with $\\|u\\|_ q\leq1$. Since $\bb R$ is $\sigma$-finite and $\lambda$ is complete, Tonelli's theorem gives

$$\begin{aligned}
&\quad\int\!\left(\int\!|h_x(y)|\,d\lambda(y)\right)|u(x)|\,d\lambda(x)\\
&=\int\!\left(\int\!|u(x)||\tau_yf(x)|\,d\lambda(x)\right)|g(y)|\,d\lambda(y)\\
&\leq\|f\|_ p\|u\|_ q\int\!|g|\,d\lambda\qquad(\text{Hölder})\\
&\leq\|f\|_ p\|g\|_ 1.
\end{aligned}$$

by picking $u$ supported on all of $\bb R$, we see that $\left(\int\\!\lvert h_x(y)\rvert\,d\lambda(y)\right)\lvert u(x)\rvert<\infty$ for $\lambda$-a.e. $x\in\bb R$, ie. $h_x$ is Lebesgue integrable for $\lambda$-a.e. $x\in\bb R$. Also, by Hölder's inequality, the supremum of LHS over all $\\|u\\|_ q\leq1$ is $\\|\int\\!\lvert h_x\rvert\,d\lambda\\|_ p$, so

$$\|f* g\|_ p\leq\left\|\int\!|h_x|\,d\lambda\right\|_ p\leq\|f\|_ p\|g\|_ 1,$$

as desired. $\qed$

__Proposition__: Let $1\leq p\leq\infty$, and let $f\in L^p(\bb R)$, $g,h\in L^1(\bb R)$. Then $f* g=g* f$ and $f* (g* h)=(f* g)* h$.

__Proof__: By a change of variables, we have

$$\begin{aligned}
(f* g)(x)&=\int\!f(x-y)g(y)\,d\lambda(y)\\
&=\int\!f(x-(x-z))g(x-z)\,d\lambda(z)\\
&=\int\!g(x-z)f(z)\,d\lambda(z)\\
&=(g* f)(x).
\end{aligned}$$

Also, by the Fubini-Tonelli theorem, we have

$$\begin{aligned}
(f* (g* h))(x)&=\int\!f(x-y)(g* h)(y)\,d\lambda(y)\\
&=\int\!f(x-y)\left(\int\!g(y-z)h(z)\,d\lambda(z)\right)\,d\lambda(y)\\
&=\int\!h(z)\left(\int\!f(x-y)g(y-z)\,d\lambda(y)\right)\,d\lambda(z)\\
&=\int\!h(z)\left(\int\!f(x-(x-y'))g(x-y'-z)\,d\lambda(y')\right)\,d\lambda(z)\\
&=\int\!h(z)(f* g)(x-z)\,d\lambda(z)\\
&=((f* g)* h)(x),
\end{aligned}$$

as desired. $\qed$