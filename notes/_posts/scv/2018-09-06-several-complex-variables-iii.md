---
title: "Several Complex Variables (III): Hartogs's Phenomenon"
layout: post
tag: [several complex variables]
date: 2018-09-06 11:24:38 +0800
---

One of the most dramatic differences between theory of single variable and several variable holomorphic functions is __Hartogs's phenomenon__: for $n>1$, there are domains (nonempty connected open sets) $U\subsetneq V\subseteq\bb C^n$ such that _every_ holomorphic function on $U$ extends to a holomorphic function on $V$.

<!--more-->

This is in stark contrast to the $n=1$ case: if $p\in V\cap\del U$, then $f(z)=\frac1{z-p}$ is holomorphic in $U$ but does not extend to $V$.

## A class of examples

Consider the polydisc $\Delta(0,r)\subseteq\bb C^n$ ($n\geq2$), with polyradius $r=(r_1,\ldots,r_n)$. We can view the first $n-1$ coordinates and the $n$-th coordinate separately:

$$\Delta(0,r)=\Delta(0,r')\times\Delta(0,r_n),\qquad z=(z',z_n).$$

where $r'=(r_1,\ldots,r_{n-1})$, $z'=(z_1,\ldots,z_{n-1})$. We can picture this as if the $n$-th coordinate $z_n$ were drawn vertically, with the other $n-1$ coordinates $z'$ drawn horizontally.

Take any region $U\subseteq\Delta(0,r)$. For each $z'\in\Delta(0,r')$, we can consider the vertical slice

$$U_{z'}\coloneqq\{z_n\in\bb C\,:\,(z',z_n)\in U\}\subseteq\Delta(0,r_n).$$

(picture)

Intuitively, to guarantee that every holomorphic function on $U$ extends to $\Delta(0,r)$, $U$ has to be 'large' in some sense. The technical conditions we need are as follows.

__Theorem__: Assume that $f$ is a holomorphic function on $U$ such that:

1. For some $s< r_n$, we have $\Delta(0,r)\backslash U\subseteq\Delta(0,r')\times\overline\Delta(0,s)$, ie. any vertical slice of $U$ contains the annulus $\Delta(0,r_n)\backslash\overline\Delta(0,s)$;
2. $U_{z'}=\Delta(0,r_n)$ for all $z'$ in some open subset of $\Delta(0,r')$, ie. over some horizontal open set, the vertical slice is all of the disc $\Delta(0,r_n)$.

Then every holomorphic function on $U$ has a holomorphic extension to $\Delta(0,r)$.

__Proof__: For $s<\tilde s< r_n$, consider the function $f_{\tilde s}:\Delta(0,r')\times\Delta(0,\tilde s)\to\bb C$ given by

$$f_{\tilde s}(z',z_n)\coloneqq\frac1{2\pi i}\int_{\del\Delta(0,\tilde s)}\!\frac{f(z',\zeta)}{\zeta-z_n}d\zeta.$$

By condition 1, $\del\Delta(0,\tilde s)$ is contained in every vertical slice, so this integral is well-defined.

Note that $f_{\tilde s}$ is:

- continuous: the integrand is continuous in $(z',z_n)$;
- analytic in $z_n$: for fixed $z'$, $f_{\tilde s}$ is a Cauchy integral in $z_n$;
- analytic in $z'$: for fixed $z_n$, the integrand is an absolutely convergent power series about $z'$, so by exchanging summation and integral we get a power series for $f_{\tilde s}$.

Thus by Osgood's lemma, $f_{\tilde s}$ is analytic in its domain of definition. (See the [previous post]({% post_url 2018-09-04-several-complex-variables-ii %}) for results on equivalent definitions of holomorphic functions.)

Moreover, by the Cauchy integral formula, the integral above is independent of the contour, as long as $z_n$ lies in the region bounded by the contour. Hence for any other $s<\tilde s_0< r_n$, the functions $f_{\tilde s}$ and $f_{\tilde s_0}$ agree on their common domain of definition. Now gluing together all the $f_{\tilde s}$ gives a function $\hat f$ holomorphic on $\Delta(0,r)$ (since it is holomorphic on each $\Delta(0,r')\times\Delta(0,\tilde s)$).

It remains to show that $\hat f=f$ in $U$. By condition 2 and the Cauchy integral formula, this holds in the vertical slices over some horizontal open set, so $\hat f=f$ in some open subset of $U$. Now we finish by applying the following theorem to $g=\hat f-f$. $\qed$

__Identity theorem__: Let $g$ be holomorphic in some domain $U\subseteq\bb C^n$, such that $g$ and its partial derivatives of all orders vanish at some point in $U$. Then $g\equiv0$ on $U$.

The proof is the same as in the one variable case:

__Proof__: Consider the set $S$ of all points in $U$ at which $g$ and its partial derivatives of all orders vanish. Note that this is the intersection of the zero sets of each partial derivative, which are all closed sets, so $S$ is closed. On the other hand, if $\zeta\in S$ then the power series for $g$ is identically zero in some neighbourhood $W$ of $\zeta$, so $W\subseteq S$; hence $S$ is open. Therefore $S$ is a nonempty clopen subset of the connected set $U$, so $S=U$. In particular, $g$ vanishes on $U$. $\qed$

## Examples

We now explicitly construct domains $U$ on which Hartogs's phenomenon holds.

Take any compact $K\subseteq\Delta(0,r)$ such that $U=\Delta(0,r)\backslash K$ is connected. Then $U$ satisfies conditions 1 and 2, so any holomorphic function on $U$ has a holomorphic extension to $\Delta(0,r)$.

__Corollary__: A holomorphic function in $n\geq2$ variables cannot have isolated zeroes.

__Proof__: Otherwise, assume without loss of generality that $f$ has isolated zero at $0$, so it is the only zero of $f$ in a sufficiently small $\Delta(0,r)$. Take $K=\overline\Delta(0,\frac r2)$, $U=\Delta(0,r)\backslash K$, so $\frac1f$ has a holomorphic extension from $U$ to $\Delta(0,r)$, agreeing with $\frac1f$ everywhere on $\Delta(0,r)\backslash\\{0\\}$ by identity theorem. In particular, $\frac1f$ has finite limit as $z\to0$, contradiction. $\qed$

The above result corresponds to the idea that the zero set of a $n$-variable holomorphic function should have dimension $n-1$ instead of 0. This will only be made rigorous later in the course, when we develop the concept of dimension for analytic varieties.

For our next example, consider the __Hartogs figure__

$$U=\{(z_1,z_2)\in\Delta(0,(1,1))\,:\,|z_1|<\frac12\text{ or }|z_2|>\frac12\}.$$

The cross-section of $U$ along the two real axes $x_1,x_2$ (ie. $y_1=y_2=0$) is shown below. As the picture suggests, $U$ is homeomorphic to $\Delta(0,(1,1))$.

(diagram)

Again, $U$ satisfies conditions 1 and 2, so any holomorphic function on $U$ has a holomorphic extension to $\Delta(0,(1,1))$.


{% comment %}
()* &
{% endcomment %}