---
title: 'Algebraic Number Theory (II): Number Fields'
layout: post
date: 2019-01-25 17:08:43 +0800
tag: [algebraic number theory]
series-order: 2
---

A __number field__ $K$ is a subfield of $\bb C$ which is a finite extension of $\bb Q$. These are the main objects of study of algebraic number theory. In this post, we look at some basic examples and properties, and define the _trace_ and _norm_ functions in number fields.

<!--more-->

## Quadratic fields

For our first example, consider the __quadratic fields__ $\bb Q[\sqrt m]$ for any integer $m\neq0,1$. Clearly $\bb Q[\sqrt m]=\bb Q[\sqrt{d^2m}]$ for any nonzero integer $d$; hence we may assume that $m$ is squarefree. We call the fields $\bb Q[\sqrt m]$ for $m>1$ (resp. $m<0$) the __real quadratic fields__ (resp. __imaginary quadratic fields__).

When $m\neq0,1$ is squarefree, the minimal polynomial of $\sqrt m$ over $\bb Q$ is $X^2-m$, which is irreducible over $\bb Q$ (since we can check that $\sqrt m$ is not a rational number). Hence $[\bb Q[\sqrt m]:\bb Q]=2$.

__Proposition__: Every quadratic field is normal over $\bb Q$.

__Proof__: Note that the conjugates of $\sqrt m$ are $\pm\sqrt m$, both of which lie in $\bb Q[\sqrt m]$. $\qed$

Conversely, we show that these $\bb Q[\sqrt m]$ completely parametrise number fields of degree $2$ over $\bb Q$.

__Proposition__: Every number field of degree $2$ over $\bb Q$ is one of the quadratic fields.

__Proof__: If $K=\bb Q[\alpha]$ has degree $2$, then $\alpha$ is the root of some quadratic polynomial $aX^2+bX+c$ with coefficients in $\bb Z$; then the quadratic formula gives

$$\alpha=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\in\bb Q[\sqrt{b^2-4ac}].\ \qed$$

__Proposition__: The fields $\bb Q[\sqrt m]$, for $m\neq0,1$ squarefree, are pairwise non-isomorphic.

__Proof__: Let $m,n\neq0,1$ be distinct squarefree integers, and suppose that there exists a field isomorphism $\varphi:\bb Q[\sqrt m]\to\bb Q[\sqrt n]$. This is an embedding of $\bb Q[\sqrt m]$ into $\bb C$, so by normality of $\bb Q[\sqrt m]/\bb Q$ we have $\bb Q[\sqrt m]=\bb Q[\sqrt n]$. In particular, $\sqrt m\in\bb Q[\sqrt n]$.

(Alternatively, without using normality, note that $\varphi(\sqrt m)=\pm\sqrt m\in\bb Q[\sqrt n]$ implies $\sqrt m\in\bb Q[\sqrt n]$.)

Then there exists $a,b\in\bb Q$ such that

$$\begin{aligned}
\sqrt m&=a+b\sqrt n\\
\therefore m&=a^2+b^2n+2ab\sqrt n\\
\therefore\sqrt n&=\frac{m-a^2-b^2n}{2ab},
\end{aligned}$$

contradicting $\sqrt n\not\in\bb Q$. $\qed$

## Trace and norm

Let $K$ be a number field, with $[K/\bb Q]=n$. Then by [elementary field theory]({% post_url notes/2019-01-21-a-refresher-in-galois-theory %}), there are $n$ embeddings $\sigma_1,\ldots,\sigma_n$ of $K$ in $\bb C$. Now for $\alpha\in K$, define the functions

$$\begin{aligned}
T^K(\alpha)&=\sigma_1(\alpha)+\cdots+\sigma_n(\alpha),\\
N^K(\alpha)&=\sigma_1(\alpha)\cdots\sigma_n(\alpha),
\end{aligned}$$

called respectively the __trace__ and __norm__ of $\alpha$ with respect to the field $K$. We will usually write $T^K=T$ and $N^K=N$ if the field $K$ is clear from context.

Since every $\sigma_k$ fixes $\bb Q$ pointwise, it is routine to check the following:

__Proposition__: Let $K$ be a number field with $[K:\bb Q]=n$.
1. For $r\in\bb Q$, we have $T(r)=nr$ and $N(r)=r^n$.
2. For $\alpha,\beta\in K$ and $r\in\bb Q$, we have
   
   $$\begin{aligned}
   T(\alpha+\beta)&=T(\alpha)+T(\beta),&T(r\alpha)&=rT(\alpha),\\
   N(\alpha\beta)&=N(\alpha)N(\beta),&N(r\alpha)&=r^nN(\alpha).\ \qed
   \end{aligned}$$

For a concrete example, let us evaluate the trace and norm over quadratic fields.

__Proposition__: Let $K=\bb Q[\sqrt m]$, where $m\neq0,1$ is squarefree. Then for any $a,b\in\bb Q$, we have

$$\begin{aligned}
T(a+b\sqrt m)&=2a,\\
N(a+b\sqrt m)&=a^2-mb^2.
\end{aligned}$$

__Proof__: Note that each conjugate of $\sqrt m$ over $\bb Q$ determines an embedding of $K$ into $\bb C$. Hence the two embeddings of $K$ are given by

$$\sigma_\pm(a+b\sqrt m)=a\pm b\sqrt m.$$

Hence the two possible images of $a+b\sqrt m$ have sum $2a$ and product $a^2-mb^2$. $\qed$

For example, for $m=-1$, we recover the norm function over the [Gaussian integers]({% post_url 2019-01-21-algebraic-number-theory-i %}).

As a special case, we have the following interpretation for $K=\bb Q[\alpha]$:

__Proposition__: Let $\alpha\in\bb C$ be algebraic. Then $T^{\bb Q[\alpha]}(\alpha)$ and $N^{\bb Q[\alpha]}(\alpha)$ are respectively the sum and product of the conjugates of $\alpha$ over $\bb Q$.

__Proof__: If $\alpha$ has degree $d$ over $\bb Q$, then the $d$ embeddings of $\bb Q[\alpha]$ send $\alpha$ precisely to each of its $d$ conjugates. $\qed$

__Corollary__: $T^{\bb Q[\alpha]}(\alpha)$ and $N^{\bb Q[\alpha]}(\alpha)$ are rational.

__Proof__: By Vieta's formulas, the minimal polynomial of $\alpha$ over $\bb Q$ is

$$X^d-T^{\bb Q[\alpha]}(\alpha)X^{d-1}+\cdots+(-1)^dN^{\bb Q[\alpha]}(\alpha),$$

and we are done since the coefficients are rational. $\qed$

In general, we have the following result:

__Proposition__: Let $K$ be a number field with $[K:\bb Q]=n$, and let $\alpha\in K$ be an algebraic number with degree $d$ over $\bb Q$. Then

$$\begin{aligned}
T^K(\alpha)&=\frac ndT^{\bb Q[\alpha]}(\alpha),\\
N^K(\alpha)&=N^{\bb Q[\alpha]}(\alpha)^{n/d}.
\end{aligned}$$

__Proof__: This follows from the fact that every embedding of $\bb Q[\alpha]$ in $\bb C$ extends to exactly $\frac nd$ embeddings of $K$ in $\bb C$. $\qed$

__Corollary__: For any number field $K$ and any $\alpha\in K$, we have $T^K(\alpha)$ and $N^K(\alpha)$ are rational. $\qed$

## Relative trace and norm

Let $K,L$ be number fields such that $K\subseteq L$, with $[L:K]=n$. Let $\sigma_1,\ldots,\sigma_n$ be the embeddings of $L$ in $\bb C$ which fix $K$ pointwise. Now for $\alpha\in L$, define the functions

$$\begin{aligned}
T^L_K(\alpha)&=\sigma_1(\alpha)+\cdots+\sigma_n(\alpha),\\
N^L_K(\alpha)&=\sigma_1(\alpha)\cdots\sigma_n(\alpha),
\end{aligned}$$

called respectively the __relative trace__ and __relative norm__ of $\alpha$ with respect to $L/K$. This is a generalisation of the trace and norm defined previously, with $T^K=T^K_{\bb Q}$ and $L^K=L^K_{\bb Q}$. In this context, we have the following analogous results:

__Proposition__: Let $K,L$ be number fields such that $K\subseteq L$, with $[L:K]=n$.
1. For $\delta\in K$, we have $T(\delta)=n\delta$ and $N(\delta)=\delta^n$.
2. For $\alpha,\beta\in L$ and $\delta\in K$, we have
   
   $$\begin{aligned}
   T(\alpha+\beta)&=T(\alpha)+T(\beta),&T(\delta\alpha)&=\delta T(\alpha),\\
   N(\alpha\beta)&=N(\alpha)N(\beta),&N(\delta\alpha)&=\delta^nN(\alpha).\ \qed
   \end{aligned}$$

__Proposition__: Let $\alpha\in\bb C$ be algebraic, and let $K$ be a number field. Then $T^{K[\alpha]}_ K(\alpha)$ and $N^{K[\alpha]}_ K(\alpha)$ are respectively the sum and product of the conjugates of $\alpha$ over $K$. $\qed$

__Corollary__: $T^{K[\alpha]}_ K(\alpha)$ and $N^{K[\alpha]}_ K(\alpha)$ are in $K$. $\qed$

__Proposition__: Let $K,L$ be number fields such that $K\subseteq L$, with $[L:K]=n$, and let $\alpha\in L$ be an algebraic number with degree $d$ over $K$. Then

$$\begin{aligned}
T^L_K(\alpha)&=\frac ndT^{K[\alpha]}_ K(\alpha),\\
N^L_K(\alpha)&=N^{K[\alpha]}_ K(\alpha)^{n/d}.\ \qed
\end{aligned}$$

__Corollary__: For any number fields $K,L$ such that $K\subseteq L$, and any $\alpha\in L$, we have $T^L_K(\alpha)$ and $N^L_K(\alpha)$ are in $K$. $\qed$

Finally, we prove the _transitivity_ of the relative trace and relative norm.

__Proposition__: Let $K,L,M$ be number fields with $K\subseteq L\subseteq M$. Then for all $\alpha\in M$, we have

$$\begin{aligned}
T^L_K(T^M_L(\alpha))&=T^M_K(\alpha),\\
N^L_K(N^M_L(\alpha))&=N^M_K(\alpha).
\end{aligned}$$

__Proof__: Let $\sigma_1,\ldots,\sigma_n$ be the embeddings of $L$ in $\bb C$ fixing $K$ pointwise, and let $\tau_1,\ldots,\tau_m$ be the embeddings of $M$ in $\bb C$ fixing $L$ pointwise.

We want to compose the $\sigma_i$ with the $\tau_j$. As such, we fix a normal extension $N/\bb Q$ such that $M\subseteq N$, and choose an extension of each $\sigma_i$ and $\tau_j$ to an automorphism of $N$, which we will also denote by $\sigma_i$ and $\tau_j$. Now

$$\begin{aligned}
T^L_K(T^M_L(\alpha))&=\sum_i\sigma_i\left(\sum_j\tau_j(\alpha)\right)=\sum_{i,j}\sigma_i\circ\tau_j(\alpha),\\
N^L_K(N^M_L(\alpha))&=\prod_i\sigma_i\left(\prod_j\tau_j(\alpha)\right)=\prod_{i,j}\sigma_i\circ\tau_j(\alpha).
\end{aligned}$$

Now consider the $mn$ functions $\sigma_i\circ\tau_j\rvert_M$. Each of these is an embedding of $M$ in $\bb C$ fixing $K$ pointwise. Furthermore, if any two of them are equal, say $\sigma_i\circ\tau_j=\sigma_{i'}\circ\tau_{j'}$, then

$$\sigma_i|_ L=\sigma_i\circ\tau_j|_ L=\sigma_{i'}\circ\tau_{j'}|_ L=\sigma_{i'}|_ L,$$

so $i=i'$, hence $j=j'$. Thus the $mn$ functions $\sigma_i\circ\tau_j\rvert_M$ are pairwise distinct, so they form the complete list of embeddings of $M$ in $\bb C$ fixing $K$ pointwise (since $mn=[M:L][L:K]=[M:K]$). Therefore

$$\begin{aligned}
\sum_{i,j}\sigma_i\circ\tau_j(\alpha)&=T^M_K(\alpha),\\
\prod_{i,j}\sigma_i\circ\tau_j(\alpha)&=N^M_K(\alpha),
\end{aligned}$$

and we are done. $\qed$