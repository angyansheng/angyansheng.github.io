---
title: 'Measure Theory (XVIII): The Lebesgue Differentiation Theorem'
layout: post
tag: [measure theory]
date: 2018-12-29 14:25:55 +0800
macros: >-
  "\\Var":"\\operatorname{Var}"
---

In this post, we prove the analogues of the Fundamental Theorem of Calculus for the Lebesgue integral on $\bb R$.

<!--more-->

## Lebesgue differentiation theorem

The following lemma shows that given two integrable functions on $[a,b]$, if their Lebesgue integrals agree on every interval, then they are equal $\lambda$-a.e.

__Lemma__: Let $f:[a,b]\to\bb R$ be Lebesgue integrable on $[a,b]$, such that

$$\int_a^x\!f\,d\lambda=0\quad\text{for all }x\in[a,b].$$

Then $f=0$ $\lambda$-a.e. on $[a,b]$.

__Proof__: Let

$$\mc S\coloneqq\left\{E\subseteq[a,b]\text{ measurable}\,:\,\int_E\!f\,d\lambda=0\right\}.$$

Note that $\mc S$ contains every open interval $(x,y)\subseteq[a,b]$, since $\int_x^y\\!f\,d\lambda=\int_a^y\\!f\,d\lambda-\int_a^x\\!f\,d\lambda=0$. Also, by countable additivity of the Lebesgue integral, $\mc S$ is closed under countable disjoint union. Hence $\mc S$ contains every open set in $[a,b]$.

Now $\mc S$ clearly contains every $\lambda$-null subset of $[a,b]$. Since every Lebesgue measurable subset of $[a,b]$ is the disjoint union of an open set and a $\lambda$-null set, $\mc S$ in fact contains every measurable subset of $[a,b]$. In particular, we have $\\{f>0\\}\in\mc S$, so

$$\int_{\{f>0\}}\!f\,d\lambda=\int_a^b\!f^+\,d\lambda=0,$$

so $f^+=0$ $\lambda$-a.e. Similarly, we have $f^-=0$ $\lambda$-a.e., so $f=f^+-f^-=0$ $\lambda$-a.e. $\qed$

Recall the first fundamental theorem of calculus for Riemann integrals:

__FTC I__: Let $f:[a,b]\to\bb R$ be Riemann integrable, and define $F(x)=\int_a^x\\!f(t)\,dt$. Then $F$ is differentiable on $[a,b]$, and $F'=f$. $\qed$

We can now prove the analogous result for the Lebesgue integral:

__Lebesgue Differentiation Theorem__: $f:[a,b]\to\bb R$ be Lebesgue integrable, and define $F(x)=\int_a^x\\!f\,d\lambda$. Then $F$ is differentiable on $[a,b]$ $\lambda$-a.e., and $F'=f$ $\lambda$-a.e.

__Proof__: We first consider the case where $0\leq f\leq M$ for some $M>0$, so $F$ is increasing. We proved in the [previous post]({% post_url 2018-11-23-measure-theory-xvii %}) that $F$ is of bounded variation on $[a,b]$, so by the last theorem of the previous post, $F$ is differentiable on $[a,b]$ $\lambda$-a.e., and

$$\int_a^x\!F'\,d\lambda\leq\Var_{[a,x]}F=F(x)-F(a).$$

Let $g=M-f$ and $G(x)=\int_a^x\\!g\,d\lambda=M(x-a)-F(x)$. Applying the same reasoning, we have

$$\begin{aligned}
\int_a^x\!(M-F')\,d\lambda&=\int_a^x\!|G'|\,d\lambda\\
&\leq\Var_{[a,x]}G\\
&=G(x)-G(a)\\
&=M(x-a)-F(x)+F(a).
\end{aligned}$$

Now adding these two inequalities gives

$$\int_a^x\!M\,d\lambda\leq M(x-a),$$

which is in fact an equality, so equality holds everywhere above; in particular, we have

$$\int_a^x\!F'\,d\lambda=F(x)-F(a)=\int_a^x\!f\,d\lambda.$$

By our Lemma above, this implies that $F'-f=0$ for $\lambda$-a.e. $x\in[a,b], and we are done for this case.

For the case where $f\geq0$, take the sequences of functions

$$f_n=\min(f,n),\qquad F_n=\int_a^x\!f_n\,d\lambda.$$

Since $0\leq f_1\leq f_2\leq\cdots$ and $f_n\to f$ pointwise, by MCT and the previous case we have

$$\begin{aligned}
\int_a^x\!F'\,d\lambda&=F(x)-F(a)\\
&=\lim_{n\to\infty}(F_n(x)-F_n(a))\\
&=\lim_{n\to\infty}\int_a^x\!f_n\,d\lambda\\
&=\int_a^x\!f\,d\lambda,
\end{aligned}$$

so $F'-f=0$ for $\lambda$-a.e. $x\in[a,b]$.

Finally, for general $f$, write $F_\pm(x)=\int_a^x\\!f^\pm\,d\lambda$, so

$$F'=F_+'-F_-'=f^+-f^-=f\quad\lambda\text{-a.e.},$$

and we are done. $\qed$

With the notation above, we have

$$\begin{aligned}
F'(x)&=\lim_{h\to0^+}\frac{F(x+h)-F(x-h)}{2h}\\
&=\lim_{h\to0^+}\frac1{2h}\int_{x-h}^{x+h}f\,d\lambda\\
&=f(x)\quad\lambda\text{-a.e.}
\end{aligned}$$

## Lebesgue points

Let $f:[a,b]\to\bb R$ be Lebesgue integrable. A point $x\in[a,b]$ is called a __Lebesgue point__ of $f$ if

$$\lim_{h\to0^+}\frac1{2h}\int_{x-h}^{x+h}|f(y)-f(x)|\,d\lambda(y)=0.$$

This says that the "average variation" of $f$ in an interval around $x$ goes to $0$ as the interval shrinks.

__Theorem__: Let $f:[a,b]\to\bb R$ be Lebesgue integrable. Then $x$ is a Lebesgue point for $f$ for $\lambda$-a.e. $x\in[a,b]$.

__Proof__: Let $r\in\bb Q$. By the Lebesgue differentiation theorem on the function $\lvert f-r\rvert$, there is a $\lambda$-null set $N_r$ such that

$$\lim_{h\to0^+}\frac1{2h}\int_{x-h}^{x+h}|f-r|\,d\lambda=|f(x)-r|$$

for all $x\not\in N_r$.

Now $N=\bigcup_{r\in\bb Q}N_r$ is also $\lambda$-null. For $x\not\in N$, pick a sequence of rationals $r_n$ converging to $f(x)$, so

$$\begin{aligned}
\lim_{h\to0^+}\frac1{2h}\int_{x-h}^{x+h}|f(y)-f(x)|\,d\lambda(y)&=\lim_{n\to\infty}\lim_{h\to0^+}\frac1{2h}\int_{x-h}^{x+h}|f-r_n|\,d\lambda\\
&=\lim_{n\to\infty}|f(x)-r_n|\\
&=0,
\end{aligned}$$

where the first line follows from LDCT since $\lvert f-r_n\rvert$ is bounded above uniformly by $\lvert f\rvert+\sup_n\lvert r_n\rvert$, which is Lebesgue integrable. $\qed$