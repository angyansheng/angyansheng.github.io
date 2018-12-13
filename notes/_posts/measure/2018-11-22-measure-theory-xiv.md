---
title: 'Measure Theory (XIV): Approximate Identities'
layout: post
tag: [measure theory]
date: 2018-11-22 17:07:09 +0800
---

An __approximate identity__ is a family of nonnegative functions $(K_\eps)_ {\eps>0}$ in $L^1(\bb R)$ such that:
- $\int\\!K_\eps\,d\lambda=1$ for all $\eps>0$; and
- For any $r>0$, we have

  $$\lim_{\eps\to0^+}\int\!K_\eps\chi_{[-r,r]}\,d\lambda=1.$$

In other words, most of the mass of $K_\eps$ is concentrated around the origin as $\eps\to0^+$. Such a sequence can be thought of as approximations to the [Dirac delta function](https://en.wikipedia.org/wiki/Dirac_delta_function).

<!--more-->

Here is a simple construction of an approximate identity.

__Proposition__: Let $K\geq0$ be a Lebesgue integrable function such that $\int\\!K\,d\lambda=1$, and define $K_\eps(x)=\frac1\eps K(\frac x\eps)$. Then $(K_\eps)_ {\eps>0}$ is an approximate identity.

__Proof__: Note that by a linear change of variables, we have $\int\\!K_\eps\,d\lambda=1$ and

$$\int\!K_\eps\chi_{[-r,r]}\,d\lambda=\int\!K\chi_{[-\frac r\eps,\frac r\eps]}\,d\lambda.$$

As $\eps\to0^+$, the integrand increases to $K$, so by LDCT the integral converges to $\int\\!K\,d\lambda=1$, and we are done. $\qed$

__Lemma__: (Minkowski's integral inequality) Let $f_y\in L^p(\bb R)$, and choose $g\in L^1(\bb R)$ such that $g\geq0$. Define

$$\mc F(x)=\int\!f_y(x)g(y)\,d\lambda(y).$$

Then

$$\|\mc F\|_ p\leq\int\!\|f_y\|_ pg(y)\,d\lambda(y).$$

__Proof__: Let $q$ be the conjugate index of $p$, so $\frac1p+\frac1q=1$. We have

$$\begin{aligned}
\|\mc F\|_ p^p&=\int\!|\mc F(x)|^p\,d\lambda(x)\\
&\leq\int\!|\mc F(x)|^{p-1}\int\!|f_y(x)|g(y)\,d\lambda(y)\,d\lambda(x)\\
&=\iint\!|\mc F(x)|^{p/q}|f_y(x)|g(y)\,d\lambda(x)\,d\lambda(y)\qquad(\text{Tonelli})\\
&\leq\int\!\|\mc F^{p/q}\|_ q\|f_y\|_ pg(y)\,d\lambda(y)\qquad(\text{Hölder})\\
&=\|\mc F\|_ p^{p/q}\int\!\|f_y\|_ pg(y)\,d\lambda(y).
\end{aligned}$$

Dividing both sides by $\\|\mc F\\|_ p^{p/q}$ gives the desired result. $\qed$


The following result explains the terminology: an approximate identity acts almost like an identity element with respect to convolution.

__Proposition__: Let $(K_\eps)_ {\eps>0}$ be an approximate identity. For $1\leq p<\infty$, fix $f\in L^p(\bb R)$. Then

$$\lim_{\eps\to0^+}\|f* K_\eps-f\|_ p=0.$$

__Proof__: Note that

$$\begin{aligned}
(f* K_\eps-f)(x)&=\int\!f(x-y)K_\eps(y)\,d\lambda(y)-f(x)\\
&=\int\!(\tau_yf-f)(x)K_\eps(y)\,d\lambda(y),
\end{aligned}$$

so Minkowski's integral inequality gives

$$\|f* K_\eps-f\|_ p\leq\int\!\|\tau_yf-f\|_ pK_\eps(y)\,d\lambda(y).$$

Fix $\delta>0$. Since $\lim_{y\to0}\\|\tau_yf-f\\|_ p=0$, there exists $r>0$ with $\\|\tau_yf-f\\|_ p<\frac\delta2$ for all $y\in[-r,r]$. Hence

$$\begin{aligned}
\int\!\|\tau_yf-f\|_ pK_\eps(y)\,d\lambda(y)&=\left(\int_{|y|\leq r}+
\int_{|y|>r}\right)\|\tau_yf-f\|_ pK_\eps(y)\,d\lambda(y)\\
&<\frac\delta2\int_{|y|\leq r}\!K_\eps(y)\,d\lambda(y)+2\|f\|_ p\int_{|y|>r}\!K_\eps(y)\,d\lambda(y)\\
&<\frac\delta2+\frac\delta2=\delta
\end{aligned}$$

for all small enough $\eps>0$. This proves the claim. $\qed$

## Smooth functions

Let $C^\infty(\bb R)$ denote the set of all __smooth functions__ (or infinitely-differentiable functions) on $\bb R$, and let $C^\infty_c(\bb R)$ denote the smooth functions $f$ on $\bb R$ with __compact support__, ie. $\{f\neq0\}$ is a bounded subset of $\bb R$.

To prove results about convolution against a smooth function, we need to first investigate differentiation under the Lebesgue integral.

__Proposition__: Let $f:\bb R^2\to\bb R$ be a function such that $\frac{\del f}{\del y}$ exists everywhere on $\bb R^2$. Suppose that:
- For all fixed $y\in\bb R$, the functions $f(-,y)$ and $\frac{\del f}{\del y}(-,y)$ are Lebesgue integrable; and
- There is a Lebesgue integrable function $g$ on $\bb R$ such that $\lvert\frac{\del f}{\del y}(x,y)\rvert\leq g(x)$ for all $x,y$.

Then

$$\frac d{dy}\int\!f(x,y)\,d\lambda(x)=\int\!\frac{\del f}{\del y}(x,y)\,d\lambda(x).$$

__Proof__: Let $(y_n)$ be a sequence converging to $y$. Then

$$\frac{\int\!f(x,y_n)\,d\lambda(x)-\int\!f(x,y)\,d\lambda(x)}{y_n-y}=\int\!f_n(x)\,d\lambda(x),$$

where

$$\begin{aligned}
f_n(x)&\coloneqq\frac{f(x,y_n)-f(x,y)}{y_n-y}\\
&=\frac{\del f}{\del y}(x,\xi_n(x))
\end{aligned}$$

for some $\xi_n(x)$ between $y$ and $y_n$ by the mean value theorem. In particular, $f_n(x)\leq g(x)$, and $f_n(x)\to\frac{\del f}{\del y}(x,y)$, so by LDCT we have

$$\begin{aligned}
\lim_{n\to\infty}\frac{\int\!f(x,y_n)\,d\lambda(x)-\int\!f(x,y)\,d\lambda(x)}{y_n-y}&=\lim_{n\to\infty}\int\!f_n(x)\,d\lambda(x)\\
&=\int\!\frac{\del f}{\del y}(x,y)\,d\lambda(x).
\end{aligned}$$

Since this holds for any sequence $(y_n)\to y$, we conclude that

$$\begin{aligned}
\frac d{dy}\int\!f(x,y)\,d\lambda(x)&=\lim_{y'\to y}\frac{\int\!f(x,y')\,d\lambda(x)-\int\!f(x,y)\,d\lambda(x)}{y'-y}\\
&=\int\!\frac{\del f}{\del y}(x,y)\,d\lambda(x),
\end{aligned}$$

as desired. $\qed$

__Proposition__: Let $f\in L^p(\bb R)$ and $g\in C^\infty_c(\bb R)$. Then $f* g\in C^\infty(\bb R)$. If $f$ has compact support, then $f* g$ has compact support.

__Proof__: By the previous proposition, we have

$$\begin{aligned}
(f* g)'(x)&=\frac d{dx}\int\!f(y)g(x-y)\,d\lambda(y)\\
&=\int\!f(y)g'(x-y)\,d\lambda(y)\\
&=(f* g')(x).
\end{aligned}$$

By induction, we have $(f* g)^{(n)}=f* g^{(n)}$; in particular, $f* g\in C^\infty(\bb R^n)$.

If $f,g$ have compact support, say $\\{f\neq0\\}\subseteq[-M,M]$ and $\\{g\neq0\\}\subseteq[-N,N]$, then $f(x-y)g(y)$ is identically zero for all $\lvert x\rvert>M+N$, since the triangle inequality implies that either $\lvert x-y\rvert>M$ or $\lvert y\rvert>N$. Hence $\\{f* g\neq0\\}\subseteq[-M-N,M+N]$, so $f* g$ has compact support. $\qed$

Combining all the results above, we can show that $C^\infty_c(\bb R)$ is dense in $L^p(\bb R)$.

__Theorem__: Let $1\leq p<\infty$. For any $f\in L^p(\bb R)$ and $\delta>0$, there exists $g\in C^\infty_c(\bb R)$ such that $\\|f-g\\|_ p<\delta$.

__Proof__: Fix $K\in C^\infty_c(\bb R)$ such that $K\geq0$ and $\int\\!K\,d\lambda=1$ (for instance

$$K(x)=\begin{cases}C\exp\left(-\frac1{1-x^2}\right),&|x|\leq1\\0,&|x|>1\end{cases}$$

for a suitable $C>0$). Then $K_\eps(x)=\frac1\eps K(\frac x\eps)$ forms an approximate identity with $K_\eps\in C^\infty_c(\bb R)$ for all $\eps>0$.

Pick $N>0$ large enough such that $\\|f-f\chi_{[-N,N]}\\|_ p<\frac\delta2$ (such an $N$ exists by LDCT). Then pick $\eps>0$ small enough such that with

$$g=f\chi_{[-N,N]}* K_\eps\in C^\infty_c(\bb R),$$

we have $\\|g-f\chi_{[-N,N]}\\|_ p<\frac\delta2$. Then $\\|g-f\\|_ p<\delta$, so $g$ satisfies all desired conditions. $\qed$