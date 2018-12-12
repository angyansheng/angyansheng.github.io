---
title: 'Several Complex Variables (VI): Implicit Mapping Theorem'
layout: post
tag: [several complex variables]
date: 2018-09-10 18:12:41 +0800
---

To conclude our discussion of the analysis aspect of the several complex variables theory, we prove the holomorphic versions of the implicit and inverse mapping theorems.

<!--more-->

__Implicit function theorem__: Let $U$ be an open subset of $\bb C^n$, and let $f$ be a holomorphic function on $U$ with a zero at $\lambda$. Suppose that $\frac{\del f}{\del z_n}(\lambda)\neq0$. Then there is a polydisc

$$\Delta(\lambda,r)=\Delta(\lambda',r')\times\Delta(\lambda_n,r_n)\subseteq\bb C^{n-1}\times\bb C,$$

and a holomorphic $g:\Delta(\lambda',r')\to\Delta(\lambda_n,r_n)$, such that for $z=(z',z_n)\in\Delta(\lambda,r)$,

$$f(z)=0\quad\iff\quad g(z')=z_n.$$

__Proof__: This is an immediate consequence of the Weierstrass preparation theorem: by the given conditions, $f$ has vanishing order 1 in $z_n$ at $\lambda$. Thus there is a polydisc $\Delta(z,r)$ and a factorisation $f=uh$, where $u$ is holomorphic and nonzero, and $h$ is a Weierstrass polynomial of degree 1, ie.

$$h(z)=z_n-g(z')$$

for some holomorphic $g$ with $g(\lambda')=0$. Now the result follows from the fact that $f$ and $h$ have the same roots on $\Delta(\lambda,r)$. $\qed$

We will now generalise this result to holomorphic $F:U\to\bb C^m$. Any such map can be decomposed into coordinate functions $F(z)=(f_1(z),\ldots,f_m(z))$. Just as in (real) multivariable calculus, the non-degeneracy condition on the derivative generalises to a non-degeneracy condition on the $m\times n$ __Jacobian matrix__

$$J_F(z)\coloneqq\left(\frac{\del f_i}{\del z_j}(z)\right)_{i,j=1}^{m,n}.$$

__Implicit mapping theorem__: Let $U$ be an open subset of $\bb C^n$, and let $F:U\to\bb C^m$ be a holomorphic map, with coordinate functions $f_1,\ldots,f_m$ and a zero at $\lambda$. Suppose that the last $m$ columns of $J_f(z)$ form a non-singular $m\times m$ matrix. Then there is a polydisc

$$\Delta(\lambda,r)=\Delta(\lambda',r')\times\Delta(\lambda'',r'')\subseteq\bb C^{n-m}\times\bb C^m,$$

and a holomorphic $G:\Delta(\lambda',r')\to\Delta(\lambda^{\prime\prime},r^{\prime\prime})$, such that for $z=(z',z^{\prime\prime})\in\Delta(\lambda,r)$,

$$F(z)=0\quad\iff\quad g(z')=z''.$$

__Proof__: By induction on $m$. The case $m=1$ is exactly the implicit function theorem.

We now prove the statement for $m$ from the statement for $m-1$. First, split $J_F=(J_F',J_F^{\prime\prime})$ into its first $n-m$ and last $m$ columns, so $J_F^{\prime\prime}(\lambda)$ is non-singular. By a change of coordinates of the range $\bb C^m$, we may assume that $J_F^{\prime\prime}(\lambda)$ is the $m\times m$ identity matrix.

Now $\frac{\del f_m}{\del z_n}(\lambda)=1$, so by the implicit function theorem there exists a polydisc $\Delta(\lambda,r)$ and a holomorphic map

$$h:\Delta((\lambda_1,\ldots,\lambda_{n-1}),(r_1,\ldots,r_{n-1}))\to\Delta(\lambda_n,r_n)$$

such that for $z\in\Delta(\lambda,r)$,

$$f_m(z)=0\quad\iff\quad z_n=h(z_1,\ldots,z_{n-1}).$$

The idea is to restrict to the zero set of the last coordinate $f_m$, which is locally described by the hypersurface $(z_1,\ldots,z_{n-1},h(z_1,\ldots,z_{n-1}))$, and apply the induction hypothesis. More specifically, define the map

$$F':\Delta((\lambda_1,\ldots,\lambda_{n-1}),(r_1,\ldots,r_{n-1}))\to\bb C^{m-1}$$

by defining its coordinate functions $f'_1,\ldots,f'_{m-1}$ as

$$f'_i(z_1,\ldots,z_{n-1})=f_i(z_1,\ldots,z_{n-1},h(z_1,\ldots,z_{n-1})).$$

Then at the point $(\lambda_1,\ldots,\lambda_{n-1})$, we have $F'=0$, and

$$\begin{aligned}
\frac{\del f_i'}{\del z_j}&=\frac{\del f_i}{\del z_j}+\frac{\del f_i}{\del z_n}\frac{\del h}{\del z_j}\\
&=\begin{cases}1,&j=i+n-m\\0,&\text{else},\end{cases}
\end{aligned}$$

since $\frac{\del f_i}{\del z_n}=0$. Hence the last $m-1$ columns of $J_{F'}$ form a $(m-1)\times(m-1)$ identity matrix, so by induction hypothesis there exists (after possibly restricting to a smaller polydisc) a holomorphic map

$$G':\Delta(\lambda',r')\to\Delta((\lambda_{n-m+1},\ldots,\lambda_{n-1}),(r_{n-m+1},\ldots,r_{n-1}))$$

such that for $(z_1,\ldots,z_{n-1})\in\Delta((\lambda_1,\ldots,\lambda_{n-1}),(r_1,\ldots,r_{n-1}))$,

$$F'(z_1,\ldots,z_{n-1})=0\quad\iff\quad G'(z')=(z_{n-m+1},\ldots,z_{n-1}).$$

Hence if we define

$$G(z')\coloneqq(G'(z'),h(z',G'(z'))),$$

then for $z\in\Delta(\lambda,r)$ we have

$$\begin{aligned}
F(z)=0&\iff F'(z_1,\ldots,z_{n-1})=0\\
&\qquad\text{and }z_n=h(z_1,\ldots,z_{n-1})\\
&\iff G'(z')=(z_{n-m+1},\ldots,z_{n-1})\\
&\qquad\text{and }z_n=h(z_1,\ldots,z_{n-m},G'(z'))\\
&\iff G(z')=z'',
\end{aligned}$$

so $G$ satisfies the given conditions, and induction is complete. $\qed$

Now we give some important consequences of this theorem.

__Inverse mapping theorem__: Let $U$ be an open subset of $\bb C^n$, and let $H:U\to\bb C^n$ be a holomorphic map. Let $\lambda\in U$, and suppose that $J_H(\lambda)$ is non-singular. Then there is a neighbourhood $V\subseteq U$ of $\lambda$ such that $H$ is a biholomorphic mapping from $V$ onto some neighbourhood of $H(\lambda)$.

__Proof__: By the implicit function theorem applied to the function $F:\bb C^n\times U\to\bb C^n$ given by $F(z',z^{\prime\prime})=H(z^{\prime\prime})-z'$, we get a function $G$ on some polydisc with

$$G(z')=z''\quad\iff\quad F(z',z'')=0\quad\iff\quad H(z'')=z',$$

so $G$ is an inverse for $H$ on this polydisc. $\qed$

More generally, we have the following:

__Constant rank theorem__: Let $U$ be an open subset of $\bb C^n$, and let $F:U\to\bb C^m$ be a holomorphic map. Suppose that $J_f$ has constant rank $k$ in $U$. Then for each $\lambda\in U$, there is a neighbourhood $U_\lambda$ of $\lambda$ in which $F$ is biholomorphically equivalent to the standard projection

$$(z_1,\ldots,z_n)\mapsto(z_1,\ldots,z_k,0,\ldots,0)$$

from a neighbourhood of $0\in\bb C^n$ to a neighbourhood of $0\in\bb C^m$.

__Proof__: We may assume that $\lambda=0$ and $F(\lambda)=0$, and after a change of coordinates that the upper left $k\times k$ submatrix of $J_F(z)$ is non-singular at 0, and hence in a neighbourhood $U'$ of $0\in\bb C^n$. Define $G:U'\to\bb C^n$ by

$$G(z_1,\ldots,z_n)=(f_1(z_1,\ldots,z_n),\ldots,f_k(z_1,\ldots,z_n),z_{k+1},\ldots,z_n).$$

Then $J_G$ is non-singular in $U'$, so by inverse mapping theorem $G$ is a biholomorphic map from some neighbourhood $U^{\prime\prime}\subseteq U'$ of $0\in\bb C^n$ to another.

Now $F\circ G^{-1}$ has the form $(z_1,\ldots,z_n)\mapsto(z_1,\ldots,z_k,f_{k+1}',\ldots,f_m')$. Since its Jacobian also has rank $k$ in $U^{\prime\prime}$, we have $\frac{\del f_j'}{\del z_i}$ are identically zero for $i>k$, ie. $f_j'$ are functions in $z_1,\ldots,z_k$ alone. Now define

$$H(z_1,\ldots,z_m)=(z_1,\ldots,z_k,z_{k+1}-f_{k+1}',\ldots,z_m-f_m').$$

Note that $H$ has inverse

$$H^{-1}(z_1,\ldots,z_m)=(z_1,\ldots,z_k,z_{k+1}+f_{k+1}',\ldots,z_m+f_m'),$$

so $H$ is biholomorphic on some neighbourhood of $0\in\bb C^m$. Now

$$H\circ F\circ G^{-1}(z_1,\ldots,z_n)=(z_1,\ldots,z_k,0,\ldots,0)$$

on a neighbourhood $U$ of $0\in\bb C^m$, as desired. $\qed$

{% comment %}
()* &
{% endcomment %}