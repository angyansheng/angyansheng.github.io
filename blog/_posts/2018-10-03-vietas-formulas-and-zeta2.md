---
title: >-
  Vieta's Formulas and $\zeta(2)$
layout: post
tag: [elementary algebra, infinite series]
date: 2018-10-03 23:00:00 +0800
---

Today I came up with a new idea to prove the famous identity

$$\zeta(2)\coloneqq\sum_{n=1}^\infty\frac1{n^2}=\frac{\pi^2}6.$$

There is no shortage of existing proofs of this identity; see this [math.SE question](https://math.stackexchange.com/questions/8337/), or this [collection of proofs](http://empslocal.ex.ac.uk/people/staff/rjchapma/etc/zeta2.pdf) compiled by Robin Chapman. I was inspired by this [_illuminating_ video](https://youtu.be/d-o3eB9sfls), where 3Blue1Brown explains [an elementary proof](http://www.math.chalmers.se/~wastlund/Cosmic.pdf) based on Euclidean geometry<!-- (and some error bounding) -->, by a physical interpretation involving systems of lighthouses. My new idea comes from trying to translate this proof into the complex plane.

<!--more-->

## Vieta's formulas

The main idea in the video is to get an expression for the sum of inverse squared distances from the origin to the vertices of a certain regular $n$-gon. We first observe that when viewed on the complex plane, the vertices of this $n$-gon are the roots of some polynomial of degree $n$, and the sum of inverse squares can be computed by Vieta's formulas.

More explicitly, suppose that $\rho_1,\rho_2,\ldots,\rho_n$ are the roots of the polynomial

$$a_nz^n+a_{n-1}z^{n-1}+\cdots+a_1z+a_0=0,$$

with $a_n\neq0$ (so that there are $n$ roots) and $a_0\neq0$ (so the roots are nonzero), and we want to find the sum of inverse squares $\sum_j\frac1{\rho_j^2}$.

> The astute reader might have noticed that this objective is different from the video, which computes $\sum_j\frac1{\lvert\rho_j\rvert^2}$ instead. We chose this reformulation because it is easier to handle algebraically.

If we had wanted to find the sum of squares $\sum_j\rho_j^2$ instead, we could use the following calculation:

$$\begin{aligned}
\sum_j\rho_j^2&=\sum_{j,k}\rho_j\rho_k-\sum_{j< k}\rho_j\rho_k-\sum_{j>k}\rho_j\rho_k\\
&=\left(\sum_j\rho_j\right)^2-2\sum_{j< k}\rho_j\rho_k\\
&\overset{(* )}=\left(-\frac{a_{n-1}}{a_n}\right)^2-2\frac{a_{n-2}}{a_n}\\
&=\frac{a_{n-1}^2-2a_na_{n-2}}{a_n^2},
\end{aligned}$$

where for $(* )$ we used Vieta's formulas

$$\sum_j\rho_j=-\frac{a_{n-1}}{a_n},\qquad\sum_{j< k}\rho_j\rho_k=\frac{a_{n-2}}{a_n}.$$

To get the sum of inverse squares instead, we need to apply the above formula to some polynomial with roots $\frac1{\rho_1},\frac1{\rho_2},\ldots,\frac1{\rho_n}$. But this is simple: note that

$$\begin{aligned}
a_n\rho_j^n+a_{n-1}\rho_j^{n-1}+\cdots+a_1\rho_j+a_0&=0\\
\implies a_n+\frac{a_{n-1}}{\rho_j}+\cdots+\frac{a_1}{\rho_j^{n-1}}+\frac{a_0}{\rho_j^n}&=0,
\end{aligned}$$

so the polynomial $a_0z^n+a_1z^{n-1}+\cdots+a_{n-1}z+a_n=0$ has roots $\frac1{\rho_j}$. Now the formula above gives

$$\sum_j\frac1{\rho_j^2}=\frac{a_1^2-2a_0a_2}{a_0^2}.$$

## An Eulerian "proof"

In the video, a sequence of regular polygons is chosen such that the vertices tend to the sequence of odd integers on the real line. In our reformulation, we should thus choose a sequence of polynomials $f_n$ which tends to some power series $f$ with regularly spaced roots. For our purposes, we will choose

$$\begin{aligned}
f(z)&=\frac{e^z-1}z\\
&=1+\frac12z+\frac16z^2+\cdots,
\end{aligned}$$

which has roots $2\pi ik$ for $k\in\bb Z\backslash\\{0\\}$.

If we pretend that our sum-of-inverse-squares formula works not just for polynomials, but for general power series, then applying it to $f$ gives

$$\begin{aligned}
\sum_{k\in\bb Z\backslash\{0\}}\frac1{(2\pi ik)^2}&=\frac{(\frac12)^2-2(1)(\frac16)}{1^2}\\
-\frac2{4\pi^2}\sum_{k=1}^\infty\frac1{k^2}&=-\frac1{12}\\
\zeta(2)&=\frac{\pi^2}6,
\end{aligned}$$

which is a "proof" in the style of Euler that I think he might have enjoyed.

{% comment %}
<!-- > 
> variable change to Euler's original product for $\frac{\sin w}w$
>
> To be completely faithful to the video, we could have chosen $f(z)=e^z+1$, whose roots are the odd integer multiples of $\pi i$. This would give
>
> $$\sum_{k=1}^\infty\frac1{(2k-1)^2}=\frac{\pi^2}8,$$
>
> but it makes recovering the value of $\zeta(2)$, and the choice of 
 -->
{% endcomment %}

## A dead end?

To make the argument rigorous, we need polynomials $f_n$ whose roots all lie on a circle, with $f_n\to f$ as $n\to\infty$; a very nice choice is given by

$$\begin{aligned}
f_n(z)&=\frac{(1+\frac zn)^n-1}z\\
&=1+\frac{\binom n2}{n^2}z+\frac{\binom n3}{n^3}z^2+\cdots,
\end{aligned}$$

which has roots at $n(e^{2\pi ik/n}-1)$ for $n\nmid k$, ie. lying on a circle with radius $n$ centred at $z=-n$. As a sanity check, note that for fixed $k$, the above expression tends to $2\pi ik$; hence the roots of $f_n$ "tend pointwise" to the roots of $f$.

However, this is not enough to show that the sum-of-inverse-squares of the $n$ roots of $f_n$ tends to the sum-of-inverse-squares of the roots of $f$. This is where our argument falls short of the geometric proof, which had good control on the error of the finite approximation.

## A tour de force

To finish the argument, we have to abandon our initial hopes for a quick proof, and get some exact expressions from the sum-of-inverse-squares formula.

We fix $n$, and set $\omega=e^{2\pi i/n}$. Then the roots of $f_n$ are $\rho_{k,n}=n(\omega^k-1)$ for $1\leq k\leq n-1$. Note that

$$\begin{aligned}
\frac1n\left(\frac1{\omega^k-1}+\frac12\right)&=\frac1{2n}\frac{\omega^k+1}{\omega^k-1}\\
&=\frac1{2n}\frac{\omega^{k/2}+\omega^{-k/2}}{\omega^{k/2}-\omega^{-k/2}}\\
&=-\frac i{2n}\cot\frac{k\pi}n.
\end{aligned}$$

Hence

$$\begin{aligned}
\frac1{\rho_{k,n}}&=\frac1{2n}\left(-1-i\cot\frac{k\pi}n\right)\\
\frac1{\rho_{k,n}^2}&=\frac1{4n^2}\left(1-\cot^2\frac{k\pi}n+2i\cot\frac{k\pi}n\right).
\end{aligned}$$

We can sum this over $k$, take the real part, and compare with the sum-of-inverse-squares formula to obtain

$$\begin{aligned}
\frac1{4n^2}\sum_{k=1}^{n-1}\left(1-\cot^2\frac{k\pi}n\right)&=\frac{(\frac{\binom n2}{n^2})^2-2(1)(\frac{\binom n3}{n^3})}{1^2}\\
&=-\frac{(n-1)(n-5)}{12n^2}\\
\sum_{k=1}^{n-1}\cot^2\frac{k\pi}n&=\frac{(n-1)(n-2)}3\\
\sum_{1\leq k\leq\frac{n-1}2}\cot^2\frac{k\pi}n&=\frac{(n-1)(n-2)}6,
\end{aligned}$$

since $\cot^2(\pi-\theta)=\cot^2\theta$.

Now we are in the position to finish as in [Cauchy's proof of the identity](https://en.wikipedia.org/wiki/Basel_problem* Cauchy's_proof), by invoking the following trick: adding 1 to each term above gives

$$\sum_{1\leq k\leq\frac{n-1}2}\csc^2\frac{k\pi}n=\frac{(n-1)(n+1)}6.$$

By the elementary inequality $\sin\theta<\theta<\tan\theta$ for $\theta\in(0,\frac\pi2)$, we have

$$\begin{gathered}
\cot^2\theta<\frac1{\theta^2}<\csc^2\theta\\
\sum_{1\leq k\leq\frac{n-1}2}\cot^2\frac{k\pi}n<\sum_{1\leq k\leq\frac{n-1}2}\frac{n^2}{k^2\pi^2}<\sum_{1\leq k\leq\frac{n-1}2}\csc^2\frac{k\pi}n\\
\frac{\pi^2}6\frac{(n-1)(n-2)}{n^2}<\sum_{1\leq k\leq\frac{n-1}2}\frac1{k^2}<\frac{\pi^2}6\frac{(n-1)(n-2)}{n^2},
\end{gathered}$$

and we finish by taking $n\to\infty$.