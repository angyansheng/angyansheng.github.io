---
title: "Measure Theory (XVI): Vitali's Covering Theorem"
layout: post
tag: [measure theory]
date: 2018-11-23 12:40:24 +0800
---

The final topic that we will cover in these notes is how differentiation interacts with the Lebesgue integral on $\bb R^n$, culminating in the analogues of the Fundamental Theorem of Calculus for Lebesgue integrals.

However, we first need to show a technical result known as Vitali's covering theorem. In this post, we will look at this and related results, which are also of independent interest.

<!--more-->

## Vitali's covering lemma

{% comment %}
<!-- An interval in $\bb R$ is said to be __nondegenerate__ if it contains more than one point.  Of course, if an interval contains two distinct points then it contains every point in between them, so an interval is nondegenerate if and only if it is an infinite set. -->
{% endcomment %}

Let $(X,d)$ be a metric space, with open and closed balls

$$\begin{aligned}
B(a,r)&=\{x\in X\,:\,d(a,x)< r\},\\
\overline B(a,r)&=\{x\in X\,:\,d(a,x)\leq r\}.
\end{aligned}$$

There are a few versions of Vitali's covering lemma, but in each case it roughly states that for a collection of balls, we can pick a "core" subcollection of pairwise disjoint balls. The basic idea behind the proofs are the same, so we start with the simplest case.

__Proposition__: Let $\mc F$ be a finite collection of open balls in $(X,d)$. Then there exists a subcollection $\mc G\subseteq\mc F$ of pairwise disjoint balls, such that any ball $B(a,r)\in\mc F$ intersects a ball $B(a',r')\in\mc G$ with $r'\geq r$.

__Proof__: Let $\mc F=\\{B_k=B(a_k,r_k)\\}_{k=1}^n$, with $r_1\geq r_2\geq\cdots\geq r_n$.

Inductively define $\mc G$ as follows: $B_1\in\mc G$, and for $1< k\leq n$, $B_k\in\mc G$ if and only if $B_k$ is disjoint from every ball in

$$\{B_1,B_2,\ldots,B_{k-1}\}\cap\mc G.$$

Now if $B_k\not\in\mc G$, then it intersects some $B_j\in\mc G$ with $j< k$, so $r_j\geq r_k$ and we are done. $\qed$

This has the following consequence:

__Vitali's covering lemma (finite case)__: Let $\mc F$ be a finite collection of open balls in $(X,d)$. Then there exists a subcollection $\mc G\subseteq\mc F$ of pairwise disjoint balls, such that

$$\bigcup\mc F\subseteq\bigcup\{3B\,:\,B\in\mc G\},$$

where $3B$ denotes the ball with the same centre as $B$ but with 3 times the radius.

__Proof__: Take $\mc G$ as in the previous proposition. For any $B(a,r)\in\mc F$, take $B(a',r')\in\mc G$, and a point $x$ in their intersection. Then for any $y\in B(a,r)$,

$$d(a',y)\leq d(a',x)+d(x,a)+d(a,y)< r'+r+r\leq 3r'.$$

Hence $B(a,r)\subseteq B(a',3r')$, and we finish by taking union over all $B(a,r)\in\mc F$. $\qed$

Note that the above results still hold if open balls are replaced by closed balls throughout.

For an infinite collection of balls, we can no longer sort them by radius. However, the following weaker version still holds:

__Proposition__: Let $\mc F$ be any collection of open balls in $(X,d)$, each with radius at most $R<\infty$. Then there exists a subcollection $\mc G\subseteq\mc F$ of pairwise disjoint balls, such that any ball $B(a,r)\in\mc F$ intersects a ball $B(a',r')\in\mc G$ with $2r'> r$.

__Proof__: Partition $\mc F$ into subcollections

$$\mc F_n=\{B(a,r)\in\mc F\,:\,\frac R{2^n}< r\leq\frac R{2^{n-1}}\}.$$

Inductively define subcollections $\mc G_n\subseteq\mc F_n$ as follows. Let $\mc G_1$ be a maximal subcollection of pairwise disjoint balls in $\mc F_1$ (which exists by Zorn's lemma). For $n>1$, if $\mc G_k$ has been defined for all $1\leq k< n$, let $\mc G_n$ be a maximal subcollection of pairwise disjoint balls in

$$\mc H_n=\{B\in\mc F_n\,:\,\forall C\in\bigcup_{k=1}^{n-1}\mc G_k\,[B\cap C=\emptyset]\}$$

(which exists by Zorn's lemma). Finally, let $\mc G=\bigcup_{n=1}^\infty\mc G_n$.

Now for every $B=B(a,r)\in\mc F_n$, we have one of the following:
- $B\in\mc G_n$;
- $B\in\mc H_n\backslash\mc G_n$, so $B$ intersects some ball in $\mc G_n$; or
- $B\not\in\mc H_n$, so $B$ intersects some ball in $\mc G_k$ for some $k< n$.

In any case, $B$ intersects a ball in $\mc G$ of radius $r'$ with

$$2r'\geq2\frac R{2^n}=\frac R{2^{n-1}}>r,$$

as desired. $\qed$

__Vitali's covering lemma (infinite case)__: Let $\mc F$ be a collection of open balls in $(X,d)$, each with radius at most $R<\infty$. Then there exists a subcollection $\mc G\subseteq\mc F$ of pairwise disjoint balls, such that

$$\bigcup\mc F\subseteq\bigcup\{5B\,:\,B\in\mc G\}.$$

__Proof__: Take $\mc G$ as in the previous proposition. For any $B(a,r)\in\mc F$, take $B(a',r')\in\mc G$, and a point $x$ in their intersection. Then for any $y\in B(a,r)$,

$$d(a',y)\leq d(a',x)+d(x,a)+d(a,y)< r'+r+r\leq 5r'.$$

Hence $B(a,r)\subseteq B(a',5r')$, and we finish by taking union over all $B(a,r)\in\mc F$. $\qed$

If we replace the factor $2$ in the above proofs by $1+\frac\eps2$, the constant $5$ in the above result can be improved to $3+\eps$. As before, the result holds when open balls are replaced by closed balls throughout.


## Vitali's covering theorem

For the main result of this post, we are concerned with the metric space $(\bb R^n,d)$ with Lebesgue measure $\lambda$. We show that given a "thorough" covering of a set by closed balls, there is a subcollection of pairwise disjoint balls that almost cover the set (ie. up to a $\lambda$-null set).

A ball $B(a,r)$ or $\overline B(a,r)$ in $\bb R^n$ is called __nondegenerate__ if it contains a point other than its centre $a$, or equivalently if $r>0$.

Let $A\subseteq\bb R^n$. A collection $\mc F$ of nondegenerate closed balls in $\bb R^n$ is a __Vitali cover__ of $A$ if for all $x\in A$ and $\delta>0$, there is a ball $B=B(a,r)\in\mc F$ such that $r<\delta$ and $x\in B$. In other words, every point in $A$ is covered by an arbitrarily small ball in $\mc F$.

__Vitali's Covering Theorem__: Let $A\subseteq\bb R^n$ be a set (not necessarily measurable), and let $\mc F$ be a Vitali cover of $A$. Then there exists a subcollection $\mc G\subseteq\mc F$ of pairwise disjoint balls, such that

$$\lambda(A\backslash\bigcup\mc G)=0.$$

__Proof__: Note that removing every ball of radius greater than $1$ from $\mc F$, we still end up with a Vitali cover of $A$. Hence we may assume that the balls in $\mc F$ have radius at most $1$.

Take $\mc G$ as in the last proposition. We claim that this $\mc G$ satisfies the required condition; to prove this, it suffices to show that $(A\backslash\bigcup\mc G)\cap B(0,R)$ is $\lambda$-null for every $R>0$.

Fix $\eps>0$. Let $\mc G'$ be the subcollection of balls in $\mc G$ which intersect $B(0,R)$. Note that balls in $\mc G'$ are all contained in $B(0,R+2)$, so

$$\sum_{\overline B(a,r)\in\mc G'}\lambda(\overline B(a,r))\leq\lambda(B(0,R+2))<\infty.$$

Hence there exists $\delta$ for which

$$\sum_{\overline B(a,r)\in\mc G',\,r<\delta}\lambda(\overline B(a,r))<\frac\eps{5^n}.$$

Also, note that balls in $\mc G'$ with radius at least $\delta$ have Lebesgue measure at least $\lambda(B(0,\delta))>0$; hence there are only finitely many such balls, so their union $K$ is a closed set.

Since $\mc G$ is a Vitali cover, for any point $a\in(A\backslash\bigcup\mc G)\cap B(0,R)$ there exists a small enough ball $B_a\in\mc G$ such that:
- $a\in B_a$ (so $B_a\in\mc G'$);
- $B_a\subseteq B(0,R)$; and
- $B_a\cap K=\emptyset$.

By the proposition, $B_a$ intersects some ball $C_a\in\mc G$; since $B_a\subseteq B(0,R)$, we have $C_a\in\mc G'$. However, since $B_a$ is disjoint from all balls in $\mc G'$ of radius at least $\delta$, the radius of $C_a$ is less than $\delta$.

Finally, we have $B_a\subseteq 5C_a$, so

$$\begin{aligned}
\lambda((A\backslash\bigcup\mc G)\cap B(0,R))&\leq\sum_{a\in(A\backslash\bigcup\mc G)\cap B(0,R)}\lambda(B_a)\\
&\leq\sum_{a\in(A\backslash\bigcup\mc G)\cap B(0,R)}\lambda(5C_a)\\
&\leq5^n\sum_{\overline B(a,r)\in\mc G',\,r<\delta}\lambda(\overline B(a,r))<\eps.
\end{aligned}$$

Hence $\lambda((A\backslash\bigcup\mc G)\cap B(0,R))=0$, as desired. $\qed$

__Corollary__: Let $A\subseteq\bb R^n$ be a set (not necessarily measurable) with $\lambda^* (A)<\infty$, and let $\mc F$ be a Vitali cover of $A$. Then for all $\eps>0$, there exists a __finite__ subcollection $\mc G'\subseteq\mc F$ of pairwise disjoint balls, such that

$$\lambda^* (A\backslash\bigcup\mc G')<\eps.$$

__Proof__: Let $O\subseteq\bb R^n$ be a open set such that $A\subseteq O$ and $\lambda(O)<\lambda^* (A)+1<\infty$.

Then the subcollection of balls $\mc F'\subseteq\mc F$ which are contained in $O$ still form a Vitali cover of $A$, so by Vitali's covering theorem there exists a subcollection $\mc G\subseteq\mc F'$ with $\lambda(A\backslash\bigcup\mc G)=0$. Now there exists $c>0$ such that

$$\mc G'=\{B(a,r)\in\mc G\,:\,r\geq c\}$$

satisfies $\lambda(\bigcup\mc G')>\lambda(\bigcup\mc G)-\eps$, so

$$\lambda^* (A\backslash\bigcup\mc G')\leq\lambda(A\backslash\bigcup\mc G)+\lambda(\bigcup\mc G\backslash\bigcup\mc G')<\eps.$$

Also, since balls in $\mc G'$ are pairwise disjoint, have measure at least $\lambda(B(0,c))>0$, and are contained in $O$ (which has finite measure), the collection $\mc G'$ is finite, and we are done. $\qed$