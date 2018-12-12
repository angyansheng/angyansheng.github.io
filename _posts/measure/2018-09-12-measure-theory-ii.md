---
title: 'Measure Theory (II): Measures'
layout: post
tag: [measure theory]
date: 2018-09-12 11:37:47 +0800
---

Recall that we [defined $\sigma$-algebras]({% post_url 2018-09-11-measure-theory-i %}) as the natural setting for defining a _measure_, which should capture some basic intuitive properties of the "size," "length," or "volume" of a set.

<!--more-->

Formally, given a $\sigma$-algebra $\Sigma$ on a set $\Omega$ (which we think of as the collection of all _measurable_ subsets of $\Omega$), we define a __measure__ on $\Sigma$ to be a function $\mu$ satisfying:

- $\mu:\Sigma\to[0,\infty]$;
- $\mu(\emptyset)=0$;
- If $A_1,A_2,\ldots\in\Sigma$ are disjoint, then

$$\mu\left(\bigcup_{k=1}^\infty A_k\right)=\sum_{k=1}^\infty\mu(A_k).$$

The most important axiom here is the last one, which states the _countable additivity_ property for measures. Just as in the definition of a $\sigma$-algebra, countable additivity implies finite additivity, by taking $A_k=\emptyset$ for all $k>N$.

Note that in order for these axioms to make sense, we need $\emptyset$ to be measurable, and countable unions of measurable sets to be measurable. This justifies two of the axioms defining a $\sigma$-algebra.

Given a set $\Omega$ and a $\sigma$-algebra $\Sigma$ on $\Omega$, we call the pair $(\Omega,\Sigma)$ a __measurable space__. If $\mu$ is a measure on $\Sigma$, we call the triple $(\Omega,\Sigma,\mu)$ a __measure space__, and any $A\in\Sigma$ is called __$\Sigma$-measurable__, __$\mu$-measurable__, or simply __measurable__ if the measure space is clear from context.

For example, for any set $\Omega$, let $\mu:\mc P(\Omega)\to[0,\infty]$ be given by $\mu(A)=\lvert A\rvert$ if $A$ is finite, and $\mu(A)=\infty$ if $A$ is infinite. Then it is easy to check that $\mu$ is a measure on $\mc P(\Omega)$, called the __counting measure__ on $\Omega$.

__Proposition__: Let $(\Omega,\Sigma,\mu)$ be a measure space, and let $A,B\in\Sigma$ with $A\subseteq B$. Then

- $\mu(A)\leq\mu(B)$;
- If $\mu(B)<\infty$, then $\mu(B\backslash A)=\mu(B)-\mu(A)$.

__Proof__: Both parts follow from the fact that $B$ is the disjoint union of $A$ and $B\backslash A$. $\qed$

The following result states that, when passing to the limit, the measure of nested sequences of sets behave as expected.

__Proposition__: Let $(\Omega,\Sigma,\mu)$ be a measure space, and let $A_1,A_2,\ldots\in\Sigma$.

1. If $A_1\subseteq A_2\subseteq\cdots$, then

   $$\mu\left(\bigcup_{k=1}^\infty A_k\right)=\lim_{k\to\infty}\mu(A_k);$$
2. If $A_1\supseteq A_2\supseteq\cdots$, and $\mu(A_{k_0})<\infty$ for some $k_0$, then

   $$\mu\left(\bigcap_{k=1}^\infty A_k\right)=\lim_{k\to\infty}\mu(A_k).$$

__Proof__: (1): Let $B_n=A_n\backslash A_{n-1}$. By induction, we have $A_n=\bigcup_{k=1}^nB_k$, so $B_n$ is disjoint from $B_1,\ldots,B_{n-1}$. Thus

$$\begin{aligned}
\mu\left(\bigcup_{k=1}^\infty A_k\right)&=\mu\left(\bigcup_{k=1}^\infty B_k\right)\\
&=\sum_{k=1}^\infty\mu(B_k)\\
&=\lim_{n\to\infty}\sum_{k=1}^n\mu(B_k)\\
&=\lim_{n\to\infty}\mu\left(\bigcup_{k=1}^nB_k\right)\\
&=\lim_{n\to\infty}\mu(A_n).
\end{aligned}$$

(2): Since $A_{k_0}\backslash A_{k_0+1}\subseteq A_{k_0}\backslash A_{k_0+2}\subseteq\cdots$, we have

$$\begin{aligned}
\mu\left(\bigcap_{k=1}^\infty A_k\right)&=\mu(A_{k_0})-\mu\left(A_{k_0}\backslash\bigcap_{k=1}^\infty A_k\right)&&(\because\mu(A_{k_0})<\infty)\\
&=\mu(A_{k_0})-\mu\left(\bigcup_{k=1}^\infty A_{k_0}\backslash A_k\right)\\
&=\mu(A_{k_0})-\lim_{k\to\infty}\mu(A_{k_0}\backslash A_k)&&(\text{by }(1))\\
&=\mu(A_{k_0})-\lim_{k\to\infty}(\mu(A_{k_0})-\mu(A_k))&&(\because\mu(A_{k_0})<\infty)\\
&=\lim_{k\to\infty}\mu(A_k).\qed
\end{aligned}$$

Note that the finiteness assumption in (2) is necessary: for example, if $\Omega=\bb N$, $\mu$ is the counting measure, and $A_n=\\{n,n+1,\ldots\\}$, then each $A_n$ has measure $\infty$, but the intersection has measure zero!

In general, we have the subadditivity property for measures:

__Proposition__: Let $(\Omega,\Sigma,\mu)$ be a measure space, and let $A_1,A_2,\ldots\in\Sigma$. Then

$$\mu\left(\bigcup_{k=1}^\infty A_k\right)\leq\sum_{k=1}^\infty\mu(A_k).$$

__Proof__: Let $B_n=A_n\backslash\bigcup_{k=1}^{n-1}A_k$. By induction, we have $\bigcup_{k=1}^nA_k=\bigcup_{k=1}^nB_k$, so $B_n$ is disjoint from $B_1,\ldots,B_{n-1}$. Thus

$$\begin{aligned}
\mu\left(\bigcup_{k=1}^\infty A_k\right)&=\mu\left(\bigcup_{k=1}^\infty B_k\right)\\
&=\sum_{k=1}^\infty\mu(B_k)\\
&\leq\sum_{k=1}^\infty\mu(A_k),
\end{aligned}$$

since $B_k\subseteq A_k$. $\qed$

A measure also formalises the idea of a "small," "thin," or "sparse" set. More precisely, given a measure space $(\Omega,\Sigma,\mu)$, a __$\mu$-null set__ is defined as any $N\in\Sigma$ with $\mu(N)=0$. Then for any property $P$ defined on the elements of $\Omega$, we say that $P$ holds __almost everywhere__ (or __a.e.__) if $P$ only fails on a $\mu$-null set.

{% comment %}
()* &
{% endcomment %}