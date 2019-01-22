---
title: 'Commutative Algebra (II): Formal Power Series and Polynomials'
layout: post
date: 2019-01-22 09:49:12 +0800
tag: [commutative algebra]
macros: >-
  "\\rad":"\\operatorname{rad}",
  "\\lbb":"⟦",
  "\\rbb":"⟧"
---

In this post, we look at two important constructions of rings from a given ring $A$, namely the ring of formal power series and the polynomial ring over $A$.

## Ring of formal power series

Let $A\lbb X\rbb$ be the ring of formal power series over $A$, ie.

$$A\lbb X\rbb=\{a_0+a_1X+a_2X^2+\cdots\,:\,a_k\in A\},$$

with addition and multiplication defined formally.

__Proposition__: If $A$ is an integral domain, then so is $A\lbb X\rbb$.

__Proof__: For any $f,g\in A\lbb X\rbb$, we can write

$$\begin{aligned}
f&=a_rX^r+a_{r+1}X^{r+1}+\cdots,\\
g&=b_sX^s+b_{s+1}X^{s+1}+\cdots,
\end{aligned}$$

with $a_r,b_s\neq0$. Then

$$fg=a_rb_sX^{r+s}+\cdots\neq0.\ \qed$$

__Proposition__: A power series $a_0+a_1X+\cdots\in A\lbb X\rbb$ is a unit in $A\lbb X\rbb$ if and only if $a_0$ is a unit in $A$.

__Proof__: ($\Rightarrow$) If the given element has multiplicative inverse $b_0+b_1X+\cdots$, then $a_0b_0=1$.

($\Leftarrow$) The equation

$$\begin{aligned}
1&=(a_0+a_1X+\cdots)(b_0+b_1X+\cdots)\\
&=a_0b_0+(a_0b_1+a_1b_0)X+\cdots
\end{aligned}$$

has solution $b_0=a_0^{-1}$,

$$b_k=a_0^{-1}(a_1b_{k-1}+a_2b_{k-2}+\cdots+a_kb_0).\ \qed$$

We can also consider the formal power series ring in several variables $A\lbb X_1,\ldots,X_n\rbb$, with elements of the form

$$a_0+\sum a_iX_i+\sum a_{ij}X_iX_j+\cdots$$

This can also be considered as an element of $A\lbb X_1,\ldots,X_{n-1}\rbb\lbb X_n\rbb$; by induction, we have the obvious isomorphism

$$A\lbb X_1,\ldots,X_n\rbb\cong A\lbb X_1\rbb\cdots\lbb X_n\rbb,$$

and an element in this ring is a unit if and only if its constant term $a_0$ is a unit in $A$.

__Proposition__: $(X_1,\ldots,X_n)\subseteq\rad(A\lbb X_1,\ldots,X_n\rbb)$.

__Proof__: For any $g\in(X_1,\ldots,X_n)$ and $h\in A\lbb X_1,\ldots,X_n\rbb$, note that $1+gh$ is a unit (since it has constant term $1$); hence $g\in\rad(A\lbb X_1,\ldots,X_n\rbb)$. $\qed$

If $k$ is a field, then $(X_1,\ldots,X_n)$ is precisely the set of all non-units in $k\lbb X_1,\ldots,X_n\rbb$, so $k\lbb X_1,\ldots,X_n\rbb$ is a local ring with maximal ideal $(X_1,\ldots,X_n)$.

More generally, we can characterise the maximal ideals of $B=A\lbb X_1,\ldots,X_n\rbb$ for any ring $A$. By the previous proposition, any maximal ideal $\bf m$ of $B$ contains $(X_1,\ldots,X_n)$. Hence by the lattice isomorphism theorem, $\bf m$ is the preimage of a maximal ideal $\mf m$ of $B/(X_1,\ldots,X_n)\cong A$. Thus $\bf m=\mf m+(X_1,\ldots,X_n)$, the set of all power series with constant term in $\mf m$, and we have $\mf m=\bf m\cap A$.

## Polynomials

Let $A[X]$ be the polynomial ring over $A$, ie.

$$A[X]=\{a_0+a_1X+\cdots+a_nX^n\,:\,a_0,\ldots,a_n\in A\},$$

with the usual addition and multiplication.

__Proposition__: If $A$ is an integral domain, then so is $A[X]$.

__Proof__: Identical to the proof for $A\lbb X\rbb$. $\qed$

Similar to the case for formal power series, we can define the polynomial ring $A[X_1,\ldots,X_n]$ over several variables, with the natural isomorphism

$$A[X_1,\ldots,X_n]\cong A[X_1]\cdots[X_n].$$

However, the structure of maximal ideals in polynomial rings is more complicated. For instance, it is not true that a maximal ideal of $A[X]$ contains $X$; since $X-1$ is a non-unit, there is a maximal ideal of $A[X]$ which contains it, and that ideal cannot contain $X$.

## Reducing coefficients mod $I$

For an ideal $I\subseteq A$, let $I\lbb X\rbb$ be the set of formal power series in $A\lbb X\rbb$ with all coefficients in $I$.

We can directly check that $I\lbb X\rbb$ is an ideal of $A\lbb X\rbb$. Alternatively, we can consider the very useful __reduction mod $I$__ homomorphism

$$A\lbb X\rbb\to(A/I)\lbb X\rbb,$$

obtained by reducing each coefficient modulo $I$. (We need to check that this is indeed a ring homomorphism.) Now the kernel of this map is clearly $I\lbb X\rbb$, so in fact we have:

__Proposition__: $A\lbb X\rbb/I\lbb X\rbb\cong(A/I)\lbb X\rbb$. $\qed$

__Corollary__: If $P$ is a prime ideal of $A$, then $P\lbb X\rbb$ is a prime ideal of $A\lbb X\rbb$. $\qed$

The above discussion carries over exactly if we replace formal power series by polynomials. In particular, reduction mod $I$ is also a ring homomorphism, and $A[X]/I[X]\cong(A/I)[X]$.

We note here that there is an important difference between $I\lbb X\rbb$ and $I[X]$, in terms of the following results.

__Proposition__: For any ideal $I\subseteq A$, we have

$$I[X]=I\cdot A[X].$$

(Here the RHS is interpreted as a product of ideals in $A[X]$.)

__Proof__: ($\supseteq$) Clear.

($\subseteq$) Every polynomial in $I[X]$ is a finite sum of terms of the form $c_kX^k$, where $c_k\in I$ and $X^k\in A[X]$. $\qed$

For formal power series, $I\lbb X\rbb\supseteq I\cdot A\lbb X\rbb$ is always true, but the reverse inclusion might not hold. This is essentially because the product of two ideals is given by _finite_ sums of product terms, while a formal power series has _infinitely_ many terms. However, we have the following partial converse:

__Proposition__: For any _finitely generated_ ideal $I\subseteq A$, we have

$$I\lbb X\rbb=I\cdot A\lbb X\rbb.$$

__Proof__: If $I=a_1A+\cdots+a_rA$, then every $\sum_kc_kX^k$ in $I\lbb X\rbb$ can be written as

$$\sum_{j=1}^ra_j\sum_kb_{jk}X^k,$$

where $c_k=\sum_{j=1}^ra_jb_{jk}$. This is clearly in $I\cdot A\lbb X\rbb$. $\qed$