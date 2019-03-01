---
title: 'Algebraic Number Theory (III): Algebraic Integers'
layout: post
date: 2019-02-08 09:12:03 +0800
tag: [algebraic number theory]
---

In this post, we study the _algebraic integers_, which are algebraic numbers with certain "integrality" properties, analogous to the integers $\bb Z$ within the rationals $\bb Q$.

<!--more-->

## Gauss's lemma

First, we consider the relation between factorisation in $\bb Z[X]$ and factorisation in $\bb Q[X]$.

__Gauss's Lemma__: Call a polynomial in $\bb Z[X]$ __primitive__ if the gcd of its coefficients is $1$. Then the product of two primitive polynomials is primitive.

__Proof__: We prove the contrapositive statement. Let $g,h\in\bb Z[X]$, and suppose some prime $p\in\bb Z$ divides every coefficient of $gh$. Now if $\varphi:\bb Z[X]\to(\bb Z/p\bb Z)[X]$ is the reduction mod $p$ ring homomorphism, we have

$$\varphi(g)\varphi(h)=\varphi(gh)=0.$$

But $\bb Z/p\bb Z$ is an integral domain, hence so is $(\bb Z/p\bb Z)[X]$. Thus either $\varphi(g)=0$ or $\varphi(h)=0$, so $p$ divides all the coefficients of either $g$ or $h$. Thus either $g$ or $h$ is not primitive. $\qed$

The following consequence is also often referred to as Gauss's lemma. Recall that a __monic polynomial__ is a polynomial with leading coefficient $1$.

__Theorem__: Let $g,h\in\bb Q[X]$ be monic polynomials, and suppose that $gh\in\bb Z[X]$. Then $g,h\in\bb Z[X]$.

__Proof__: Let $m$ (resp. $n$) be the smallest positive integer for which $mg\in\bb Z[X]$ (resp. $nh\in\bb Z[X]$). This $m$ exists since, for instance, the product of denominators of all coefficients of $g$ satisfies the property.

Now if $d$ is the gcd of the coefficients of $mg$, then in particular $d$ divides the leading coefficient, which is $m$ (since $g$ is monic). Then $\frac mdg\in\bb Z[X]$, contradicting minimality of $m$. Hence $d=1$, so $mg$ is a primitive polynomial. Similarly, $nh$ is a primitive polynomial.

By Gauss's lemma, $(mg)(nh)=mngh$ is also a primitive polynomial. But $mn$ divides all coefficients of $mngh$, so $mn=1$ implies $m=n=1$, ie. $g,h\in\bb Z[X]$. $\qed$

__Corollary__: Let $f\in\bb Z[X]$ be a monic polynomial. Then $f$ is irreducible over $\bb Z$ if and only if it is irreducible over $\bb Q$.

__Proof__: ($\Leftarrow$) Every factorisation of $f$ over $\bb Q$ is trivial (ie. one factor is constant). In particular, every factorisation of $f$ over $\bb Z$ is trivial.

($\Rightarrow$) If $f=gh$ with $g,h\in\bb Q[X]$, let $a$ be the leading coefficient of $g$. Then by replacing $g\to\frac ga$ and $h\to ah$, we may assume that $g$ is monic. Now $f$ is monic implies $h$ is also monic.

Now by the previous theorem, we have $g,h\in\bb Z[X]$, so one of them is constant by irreducibility of $f$ over $\bb Z$. Hence the original factorisation was trivial. $\qed$

## Algebraic integers

An __algebraic integer__ is a root (in $\bb C$) of some monic polynomial with coefficients in $\bb Z$. The set of all algebraic integers is denoted by $\bb A$.

__Proposition__: Let $\alpha$ be an algebraic integer, and let $g_\alpha$ be the minimal polynomial of $\alpha$ over $\bb Q$. Then $g_\alpha\in\bb Z[X]$.

__Proof__: Let $f\in\bb Z[X]$ be the monic polynomial of minimal degree which has $\alpha$ has a root. Then $f=g_\alpha h$ for some $h\in\bb Q[X]$, which is monic since $f$ and $g_\alpha$ are monic. Now the previous theorem gives $g_\alpha,h\in\bb Z[X]$, and we are done. (Note that by minimality of $f$, we in fact have $f=g_\alpha$ and $h=1$.) $\qed$

__Corollary__: An algebraic number is an algebraic integer if and only if its minimal polynomial over $\bb Q$ lies in $\bb Z[X]$. $\qed$

__Corollary__: Let $K$ be a number field, and let $\alpha\in K$ be an algebraic integer. Then $T^K(\alpha)$ and $N^K(\alpha)$ are integers.

__Proof__: Let $d$ be the degree of $\alpha$ over $\bb Q$. Recall that the minimal polynomial of $\alpha$ over $\bb Q$ is of the form

$$X^d-T^{\bb Q[\alpha]}(\alpha)X^{d-1}+\cdots+(-1)^dN^{\bb Q[\alpha]}(\alpha),$$

which lies in $\bb Z[X]$ by the previous result. Hence $T^{\bb Q[\alpha]}(\alpha)$ and $N^{\bb Q[\alpha]}(\alpha)$ are integers.

Now if $[K:\bb Q]=n$, then we have proved in the [previous post]({% post_url 2019-01-25-algebraic-number-theory-ii %}) that

$$\begin{aligned}
T^K(\alpha)&=\frac ndT^{\bb Q[\alpha]}(\alpha),\\
N^K(\alpha)&=T^{\bb Q[\alpha]}(\alpha)^{n/d},
\end{aligned}$$

so $\frac nd\in\bb Z_{>0}$ implies the desired result. $\qed$

Now we can easily identify the algebraic integers in the examples of number fields that we have seen.

__Proposition__: A rational number is an algebraic integer if and only if it is a rational integer, ie. $\bb A\cap\bb Q=\bb Z$.

__Proof__: Note that if $q\in\bb Q$, then $X-q$ is the minimal polynomial of $q$ over $\bb Q$, and this has integer coefficients if and only if $q\in\bb Z$. $\qed$

__Proposition__: Let $m\in\bb Z$ be squarefree. Then the set of algebraic integers in $\bb Q[\sqrt m]$ is

$$\bb A\cap\bb Q[\sqrt m]=\begin{cases}
\bb Z[\sqrt m],&\text{if }m\equiv2,3\pmod4,\\
\bb Z\left[\frac{1+\sqrt m}2\right],&\text{if }m\equiv1\pmod4.
\end{cases}$$

__Proof__: Let $\alpha=r+s\sqrt m$, with $r,s\in\bb Q$. If $s\neq0$ then $\alpha\not\in\bb Q$, so its minimal polynomial has degree at least $2$. On the other hand, $\alpha$ is a root of

$$(X-r)^2-ms^2=X^2-2rX+r^2-ms^2,$$

so this is the minimal polynomial of $\alpha$. Hence $\alpha$ is an algebraic integer if and only if $2r$ and $r^2-ms^2$ are both integers.

($\supseteq$) For $m\equiv2,3\pmod4$, $\alpha\in\bb Z[\sqrt m]$ implies $r,s\in\bb Z$, so clearly $2r,r^2-ms^2\in\bb Z$.

For $m\equiv1\pmod4$, $\alpha\in\bb Z\left[\frac{1+\sqrt m}2\right]$ implies $2r,2s\in\bb Z$ and $2r\equiv2s\pmod2$. Hence

$$(2r)^2-m(2s)^2\equiv0\pmod4,$$

so $r^2-ms^2\in\bb Z$.

($\subseteq$) Note that $2r\in\bb Z$ and $(2r)^2-m(2s)^2\in\bb Z$ implies $(2s)^2\in\bb Z$, so $2s\in\bb Z$.

For $m\equiv2,3\pmod4$, if $2r$ is odd, then

$$(2r)^2\equiv1\equiv m(2s)^2\pmod4,$$

which has no solution. Hence $2r$ is even, in which case

$$(2r)^2\equiv0\equiv m(2s)^2\pmod4,$$

so $2s$ is also even. Thus $r,s\in\bb Z$, so $\alpha\in\bb Z[\sqrt m]$.

For $m\equiv1\pmod4$, note that

$$(2r)^2\equiv m(2s)^2\equiv(2s)^2\pmod4,$$

so $2r\equiv2s\pmod2$. Hence $r-s,2s\in\bb Z$, so

$$\alpha=(r-s)+2s\frac{1+\sqrt m}2\in\bb Z\left[\frac{1+\sqrt m}2\right].\ \qed$$

## Integral extensions

For another perspective, we have an algebraic criterion for checking when an algebraic number is an algebraic integer. The following is a special form of the Cayley-Hamilton theorem.

__Theorem__: Let $\alpha\in\bb C$. Then the following are equivalent:
1. $\alpha$ is an algebraic integer;
2. The ring $\bb Z[\alpha]$ has finitely generated additive group;
3. $\alpha$ is contained in some subring of $\bb C$ with finitely generated additive group;
4. $\alpha A\subseteq A$ for some finitely generated additive group $A\subseteq\bb C$.

__Proof__: ($1\Rightarrow2$): Let $n$ be the degree of $\alpha$. Note that for every $k\geq n$, we can rewrite $\alpha^k$ as a $\bb Z$-linear combination of lower powers of $\alpha$. Hence $\bb Z[\alpha]$ is generated by

$$\{1,\alpha,\ldots,\alpha^{n-1}\}$$

as an abelian group.

($2\Rightarrow3\Rightarrow4$): Clear.

($4\Rightarrow1$): This is an application of the [determinant trick]({% post_url 2019-01-28-commutative-algebra-iii %}). In more detail, let $\\{a_1,\ldots,a_n\\}$ generate $A$. Then $\alpha a_i\in A$, so we have an $n\times n$ matrix $M$ with entries in $\bb Z$ such that

$$\begin{pmatrix}\alpha a_1\\\vdots\\\alpha a_n\end{pmatrix}=M\begin{pmatrix}a_1\\\vdots\\a_n\end{pmatrix}.$$

Hence

$$(\alpha I-M)\begin{pmatrix}a_1\\\vdots\\a_n\end{pmatrix}=\begin{pmatrix}0\\\vdots\\0\end{pmatrix}.$$

Since not all the $a_i$ are zero, we have $\det(\alpha I-M)=0$. But when we expand out this determinant, we get a monic polynomial in $\alpha$ of degree $n$ with coefficients in $\bb Z$. Hence $\alpha$ is an algebraic integer. $\qed$

__Corollary__: If $\alpha$ and $\beta$ are algebraic integers, then so are $\alpha+\beta$ and $\alpha\beta$.

__Proof__: By the above theorem, $\bb Z[\alpha]$ and $\bb Z[\beta]$ have finitely generated additive groups, say with generators $\\{a_1,\ldots,a_n\\}$ and $\\{b_1,\ldots,b_m\\}$ respectively. 

Consider the ring $\bb Z[\alpha,\beta]$. Its elements are $\bb Z$-linear combinations of products of elements of $\bb Z[\alpha]$ with elements of $\bb Z[\beta]$. Now each of these products is a $\bb Z$-linear combination of the terms

$$\{a_ib_j\,:\,1\leq i\leq n,\,1\leq j\leq m\},$$

so this is a finite generating set for $\bb Z[\alpha,\beta]$ as an additive group. 

Now $\alpha+\beta$ and $\alpha\beta$ are elements of $\bb Z[\alpha,\beta]$, so they are algebraic integers by the above theorem. $\qed$

__Corollary__: $\bb A$ is a ring. $\qed$

__Corollary__: The set of algebraic integers in any number field form a ring. $\qed$

For any number field $K$, we will refer to the set of algebraic integers $\bb A\cap K$ in $K$ as the __number ring__ corresponding to $K$.