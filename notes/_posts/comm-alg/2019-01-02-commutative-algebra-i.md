---
title: 'Commutative Algebra (I): Radicals'
layout: post
tag: [commutative algebra]
date: 2019-01-02 14:40:09 +0800
macros: >-
  "\\nil":"\\operatorname{nil}",
  "\\rad":"\\operatorname{rad}"
---

In this post, we introduce the radical of an ideal, and the nilradical and Jacobson radical of a ring.

## Multiplicative sets

Let $A$ be a ring. A subset $S\subseteq A$ is __multiplicative__ if $1\in S$ and

$$x,y\in S\implies xy\in S.$$

Recall that for every proper ideal $I$ (ie. $I$ is disjoint from $\\{1\\}$), there exists a maximal ideal containing $I$ (disjoint from $\\{1\\}$). If we want to avoid a multiplicative set instead of $\\{1\\}$, we have a similar result, as follows.

__Proposition__: Let $S$ be a multiplicative set and $I$ be an ideal disjoint from $S$. Then there is a prime ideal containing $I$ and disjoint from $S$.

__Proof__: Consider the family of ideals which contain $I$ and are disjoint from $S$, ordered by inclusion. By Zorn's lemma, this family has a maximal element, say $P$. Now if $x,y\not\in P$, then $P+(x)$ and $P+(y)$ are ideals that intersect $S$, so

$$(P+(x))(P+(y))\subseteq P+(xy)$$

also intersects $S$. Hence $xy\not\in P$, so $P$ is a prime ideal satisfying the desired conditions. $\qed$

We will see later that the above result has a natural interpretation in the context of the localisation of a ring; it states precisely that in $S^{-1}A$, every proper ideal is contained in a maximal ideal.

## Radical of an ideal

Let $I$ be an ideal of $A$. The __radical__ of $I$ is defined as

$$\sqrt I=\{a\in A\,:\,a^n\in I\text{ for some }n\geq1\}.$$

__Proposition__: Let $I$ be an ideal of $A$. Then $\sqrt I$ is the intersection of all prime ideals containing $I$.

__Proof__: ($\subseteq$) Let $x\in\sqrt I$. For any prime ideal $P$ containing $I$, we have $x^n\in P$ for some $n\geq1$ implies $x\in P$.

($\supseteq$) Let $x\not\in\sqrt I$. Then $S=\\{x^n\,:\,n\geq0\\}$ is a multiplicative set disjoint from $I$, so by the previous proposition there exists a prime ideal $P$ containing $I$ and disjoint from $S$. In particular, $P$ does not contain $x$. $\qed$

An element $x\in A$ is __nilpotent__ if $x^n=0$ for some $n\geq1$. The set of all nilpotent elements of $A$ is called the __nilradical__ of $A$, written $\nil(A)$. Note that this is simply the radical $\sqrt{(0)}$ of the zero ideal.

__Corollary__: $\nil(A)$ is the intersection of all prime ideals of $A$. $\qed$

We say that $A$ is __reduced__ if $\nil(A)=0$. For any ring $A$, we write $A_\text{red}\coloneqq A/\nil(A)$.

__Proposition__: $A_\text{red}$ is a reduced ring.

__Proof__: If $(x+\nil(A))^n=0+\nil(A)$ then $x^n\in\nil(A)$ implies $x\in\nil(A)$. Hence the only nilpotent element of $A_\text{red}$ is zero. $\qed$

## Jacobson radical

The __Jacobson radical__ (or __radical__) of $A$, written $\rad(A)$, is the intersection of all maximal ideals of $A$.

__Proposition__: Let $x\in A$. Then $x\in\rad(A)$ if and only if for any $a\in A$, the element $1+ax$ is a unit in $A$.

__Proof__: ($\Rightarrow$) For any $a\in A$ and $x\in\rad(A)$, the element $1+ax$ is not in any maximal ideal of $A$, so $(1+ax)=A$, ie. $1+ax$ is a unit.

($\Leftarrow$) If $x\not\in\rad(A)$, then $x\not\in M$ for some maximal ideal $M$, so $M+(x)=A$. Hence there exists $m\in M$ and $a\in A$ such that $m-ax=1$, so $1+ax=m\in M$ is not a unit. $\qed$