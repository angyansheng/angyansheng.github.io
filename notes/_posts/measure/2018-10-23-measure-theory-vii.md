---
title: 'Measure Theory (VII): The Carathéodory Construction of Measures'
layout: post
tag: [measure theory]
date: 2018-10-23 17:50:53 +0800
---

Given a measure space, we have defined the notion of Lebesgue integration (see [I]({% post_url 2018-10-20-measure-theory-iv %}), [II]({% post_url 2018-10-23-measure-theory-v %})), with many desirable properties such as linearity, monotonicity, and [limit theorems]({% post_url 2018-10-23-measure-theory-vi %}).

Embarassingly, we now have a powerful theory, but very few examples of measures to apply it to: for example, we don't even know that there exists a measure $\lambda$ on $\bb R$ such that $\lambda[a,b]=b-a$ for all $a< b$!

In this post, we describe a general construction, due to Lebesgue and Carathéodory, that yields a measure on a suitable $\sigma$-algebra $\Sigma$ over any $\Omega$.

<!--more-->

## Outer measures

An __outer measure__ on a nonempty set $\Omega$ is a function $\mu^* :\mc P(\Omega)\to[0,\infty]$ satisfying:
- $\mu^* (\emptyset)=0$;
- If $A\subseteq B\subseteq\Omega$, then $\mu^* (A)\leq\mu^* (B)$;
- If $A_1,A_2,\ldots\subseteq\Omega$, then

  $$\mu\left(\bigcup_{n=1}^\infty A_n\right)\leq\sum_{n=1}^\infty\mu(A_n).$$

Hence outer measures satisfy _monotonicity_ and _countable subadditivity_. Note that every measure is an outer measure, but not conversely.

__Proposition__: Let $\mc S\subseteq\mc P(\Omega)$ be a family of subsets of $\Omega$ such that $\emptyset\in\mc S$. Let $\mu_0:\mc S\to[0,\infty]$ be a function such that $\mu_0(\emptyset)=0$, and define $\mu^* :\mc P(\Omega)\to[0,\infty]$ by

$$\mu^* (A)=\inf\left\{\sum_{n=1}^\infty\mu_0(A_n)\,:\,A_n\in\mc S,\,A\subseteq\bigcup_{n=1}^\infty A_n\right\},$$

with the convention that $\inf(\emptyset)=\infty$. Then $\mu^* $ is an outer measure on $\Omega$.

> Intuitively, $\mu_0$ assigns a "length," "volume," or "size" to each member of $\mc S$. For any $A\subseteq\Omega$, we can try to cover $A$ with sets in $\mc S$; then the sum of "sizes" of these sets give an upper bound for the "size" of $A$, and $\mu^* (A)$ is just the infimum of this sum over all covers.
>
> In effect, by using a covering, we are approximating $A$ from the _outside_; this explains the name "outer measure."

__Proof__: Since $\\{\emptyset\\}\subseteq\mc S$ is a countable cover of $\emptyset$, we have $\mu^* (\emptyset)=0$.

If $A\subseteq B\subseteq\Omega$, then every countable cover of $B$ by sets in $\mc S$ is also a countable cover of $A$; hence $\mu^* (A)\leq\mu^* (B)$.

To prove countable subadditivity, take $A_1,A_2,\ldots\subseteq\Omega$. If $\mu^* (A_n)=\infty$ for any $n$ then there is nothing to prove. Otherwise, for any $\eps>0$, choose countable covers $(S_n^k)\subseteq\mc S$ of $A_n$, ie. $A_n\subseteq\bigcup_{k=1}^\infty S_n^k$, such that

$$\sum_{k=1}^\infty\mu_0(S_n^k)<\mu^* (A_n)+\frac\eps{2^n}.$$

Write $A=\bigcup_nA_n$. Then $(S_n^k)_ {n,k}$ is a countable cover of $A$, so

$$\mu^* (A)\leq\sum_{n,k}\mu_0(S_n^k)\leq\sum_n\mu^* (A_n)+\eps.$$

Taking $\eps\to0^+$ gives the desired result. $\qed$

## Carathéodory's criterion

As we have noted, not every outer measure $\mu^* $ is a measure in general. However, it turns out that there is a $\sigma$-algebra $\Sigma$ of subsets of $\Omega$ which are "nice" relative to $\mu^* $, such that $(\Omega,\Sigma,\mu^* \vert_\Sigma)$ is a measure space. Here we give some motivation before defining $\Sigma$.

__Note__: From here on we will use the notation $A^c\coloneqq\Omega\backslash A$ for the complement of a set $A$.

Let $\mu^* $ be an outer measure on $\Omega$, and assume for the moment that $\mu^* (\Omega)<\infty$. For any $A\subseteq\Omega$, the value of $\mu^* (A)$ is the "size" of $A$ as approximated from the outside.

We can also formalise the idea of approximating $A$ from the inside, arriving at the notion of an "_inner measure_," which we will not define here. However, we note that (roughly speaking) approximating $A$ from the inside is equivalent to approximating $A^c$ from the outside; hence our outer measure $\mu^* $ gives us an inner measure

$$\mu_*(A)=\mu^* (\Omega)-\mu^* (A^c).$$

We expect that if $A$ is sufficiently "nice," then $\mu^* (A)=\mu_*(A)$; approximating $A$ from outside or inside give the same answer. This is equivalent to

$$\mu^* (A)+\mu^* (A^c)=\mu^* (\Omega).$$

In fact, we want this to hold true relative to any subset $S\subseteq\Omega$: the outer measure and inner measure of $A\cap S$ in $S$ are equal, or equivalently,

$$\mu^* (A\cap S)+\mu^* (A^c\cap S)=\mu^* (S)\qquad\text{for all }S\subseteq\Omega.$$

The above condition is known as __Carathéodory's criterion__ for $A\subseteq\Omega$. If $A$ satisfies this criterion, we say that $A$ is __$\mu^* $-measurable__.

By countable subadditivity, we have LHS $\geq$ RHS, so Carathéodory's criterion is equivalent to 

$$\mu^* (A\cap S)+\mu^* (A^c\cap S)\leq\mu^* (S)\qquad\text{for all }S\subseteq\Omega.$$

Note that this condition still makes sense if we drop the condition that $\mu^* (\Omega)<\infty$: even though our argument only makes sense for $\mu^* (S)<\infty$, the condition is trivially satisfied if $\mu^* (S)=\infty$.

It turns out that this criterion is all we need to turn an outer measure into a measure:

__Theorem (Carathéodory)__: Let $\mu^* $ be an outer measure on $\Omega$, and let $\Sigma$ be the collection of all $\mu^* $-measurable subsets of $\Omega$. Then:
1. $\Sigma$ is a $\sigma$-algebra;
2. If $\mu:\Sigma\to[0,\infty]$ is the restriction of $\mu^* $ to $\Sigma$ (ie. $\mu(A)=\mu^* (A)$ for all $A\in\Sigma$), then $\mu$ is a measure on $\Sigma$.

__Proof__: Clearly $\emptyset\in\Sigma$, and $A\in\Sigma\implies A^c\in\Sigma$. Also, $\mu^* (\emptyset)=0$. Hence it remains to show $\Sigma$ is closed under countable union, and $\mu$ is countably additive. We show this in a few steps. 

__$\Sigma$ is closed under finite union__: It suffices to show $A,B\in\Sigma\implies A\cup B\in\Sigma$; the general case follows by induction. Now for any $S\subseteq\Omega$, we have

$$\begin{aligned}
\mu^* (S)&=\mu^* (S\cap A)+\mu^* (S\cap A^c)\\
&=\mu^* (S\cap A)+\mu^* (S\cap A^c\cap B)+\mu^* (S\cap A^c\cap B^c)\\
&\geq\mu^* (S\cap(A\cup B))+\mu^* (S\cap(A\cup B)^c),
\end{aligned}$$

since $A\cup B$ is a disjoint union of $A$ and $B\cap A^c$, and $A^c\cap B^c=(A\cup B)^c$. Note that this is exactly Carathéodory's criterion for $A\cup B$; hence $A\cup B\in\Sigma$.

__$\mu$ is finitely additive__: For disjoint $A,B\in\Sigma$ disjoint, we  have

$$\begin{aligned}
\mu^* (A\cup B)&=\mu^* ((A\cup B)\cap A)+\mu^* ((A\cup B)\cap A^c)\\
&=\mu^* (A)+\mu^* (B).
\end{aligned}$$

The general case follows by induction.

__$\mu^* $ is countably additive on $\Sigma$__: For pairwise disjoint $A_1,A_2,\ldots\in\Sigma$, we have

$$\sum_{k=1}^n\mu^* (A_k)=\mu^* \left(\bigcup_{k=1}^nA_k\right)\leq\mu^* \left(\bigcup_{k=1}^\infty A_k\right),$$

since $\mu^* $ is monotone. Taking $n\to\infty$ gives

$$\sum_{k=1}^\infty\mu^* (A_k)\leq\mu^* \left(\bigcup_{k=1}^\infty A_k\right).$$

But the reverse inequality follows from countable subadditivity; hence $\sum_k\mu^* (A_k)=\mu^* (\bigcup_kA_k).$

__$\Sigma$ is closed under countable union__: For $A_1,A_2,\ldots\in\Sigma$, let $B_n=\bigcup_{k\leq n}A_k$ and $\tilde A_n=B_n\backslash B_{n-1}$. Then $(\tilde A_n)$ are pairwise disjoint, and induction yields $\bigcup_{k\leq n}\tilde A_k=\bigcup_{k\leq n}A_k$. Hence by replacing $(A_n)$ with $(\tilde A_n)$, we may assume that $(A_n)$ are pairwise disjoint.

Write $A=\bigcup_{k=1}^\infty A_k$. Since $\Sigma$ is closed under finite union, we have $B_n\in\Sigma$. Thus for any $S\subseteq\Omega$, we have

$$\begin{aligned}
\mu^* (S)&=\mu^* (S\cap B_n^c)+\mu^* (S\cap B_n)\\
&\geq\mu^* (S\cap A^c)+\sum_{k=1}^n\mu^* (S\cap A_k),
\end{aligned}$$

since $B_n\subseteq A$ implies $S\cap B_n^c\supseteq S\cap A^c$, and

$$S\cap B_n=\bigcup_{k=1}^nS\cap A_n$$

is a disjoint union.

Taking $n\to\infty$ gives

$$\begin{aligned}
\mu^* (S)&\geq\mu^* (S\cap A^c)+\sum_{k=1}^\infty\mu^* (S\cap A_k)\\
&\geq\mu^* (S\cap A^c)+\mu^* \left(\bigcup_{k=1}^\infty S\cap A_k\right)\\
&=\mu^* (S\cap A^c)+\mu^* (S\cap A).
\end{aligned}$$

This is exactly Carathéodory's criterion for $A$, so $A\in\Sigma$, and we are done. $\qed$

The above construction, taking a function $\mu_0:\mc S\to[0,\infty]$ to an outer measure $\mu^* :\mc P(\Omega)\to[0,\infty]$, to a measure $\mu:\Sigma\to[0,\infty]$, is known as the __Carathéodory construction__.

## Complete measure spaces

A measure space $(\Omega,\Sigma,\mu)$ is called __complete__ if any subset of a $\mu$-null set is in $\Sigma$. Note that by monotonicity, any such subset is also $\mu$-null.

Completeness implies certain desirable properties of the measure space, such as the following.

__Proposition__: Let $(\Omega,\Sigma,\mu)$ be a complete measure space. If $f$ is measurable and $g=f$ a.e., then $g$ is measurable.

__Proof__: For any $a\in\bb R$, note that

$$\{g>a\}=(\{f>a\}\cup S_1)\backslash S_2,$$

where $S_1=\\{f\leq a,\,g>a\\}$ and $S_2=\\{f>a,\,g\leq a\\}$ are both subsets of the $\mu$-null subset $\\{f\neq g\\}$, and thus are both measurable. Hence $\\{g>a\\}$ is measurable for all $a\in\bb R$, so $g$ is measurable. $\qed$

__Proposition__: Let $\mu^* $ be an outer measure on $\Omega$. Then the measure space $(\Omega,\Sigma,\mu)$ obtained from the Carathéodory construction on $\mu^* $ is complete.

__Proof__: Note that if $\mu(A)=0$, then

$$\begin{aligned}
\mu^* (S)&=\mu^* (A\cap S)+\mu^* (A^c\cap S)\\
&=\mu^* (A^c\cap S)
\end{aligned}$$

for all $S\subseteq\Omega$, since $\mu^* (A\cap S)\leq\mu(A)=0$. Hence for all $B\subseteq A$, we have

$$\begin{aligned}
\mu^* (B^c\cap S)&\geq\mu^* (B\cap S)+\mu^* (B^c\cap S)\\
&\geq\mu^* (S).
\end{aligned}$$

Hence equality holds everywhere above; in particular, the Carathéodory criterion holds for $B$, so $B\in\Sigma$. $\qed$


<!-- é -->