---
title: 'Several Complex Variables (V): Local Behaviour'
layout: post
tag: [several complex variables]
date: 2018-09-10 11:00:59 +0800
---

In this post, we study the local behaviour of holomorphic functions, in particular their zero sets. To be more precise, we will work towards a several variables analogue of the following result from single variable theory:

__Theorem__: Let $f$ be a function, not identically zero, holomorphic in a domain $U\subseteq\bb C$ containing 0. If $f(0)=0$, then there is a unique factorisation

$$f(z)=z^kg(z),\qquad z\in U,$$

where $k\in\bb N$ and $g$ is holomorphic with $g(0)\neq0$.

<!--more-->

__Proof__: If the power series of $f$ about $z=0$ has all zero coefficients, then $f$ vanishes in a neighbourhood of 0, so $f$ vanishes on $U$ by the identity theorem, contradiction. Hence for some $k\geq1$, we have

$$f(z)=a_kz^k+a_{k+1}z^{k+1}+\cdots,\qquad a_k\neq0,$$

so we may take $g(z)$ to be $a_k+a_{k+1}z+\cdots$ on a neighbourhood of 0 and $\frac{f(z)}{z^k}$ everywhere else. $\qed$

In this case, we say that $f$ has a __zero of order $k$__ at $z=0$.

We may interpret the above result as follows: in a neighbourhood of a zero, every holomorphic function $f$ can be factorised as a product of

- a simple function capturing the local behaviour of the zero ($z^k$, which has a zero of order $k$ at 0); and
- a locally nonzero holomorphic function ($g$).

## Vanishing order

For the case of several variables, we will proceed as usual by taking 'slices': fix $z'=(z_1,\ldots,z_{n-1})$, and view $f$ as a holomorphic function in $z_n$.

Let $f$ be a holomorphic function defined in a neighbourhood of $0\in\bb C^n$. We say that $f$ has __vanishing order $k$ in $z_n$__ at $z=0$ if $f(0,\ldots,0,z_n)$ has a zero of order $k$ at $z_n=0$. This is equivalent to the condition that 

$$f(0)=\frac{\del f}{\del z_n}(0)=\cdots=\frac{\del^{k-1}f}{\del z_n^{k-1}}(0)=0,\qquad\frac{\del^kf}{\del z_n^k}(0)\neq0$$

for $k<\infty$, and

$$f(0)=\frac{\del f}{\del z_n}(0)=\cdots=0$$

for $k=\infty$.

It is possible for $f$ to have infinite vanishing order in $z_n$ at 0; one example is $f(z)=z_1z_2\cdots z_n$. From the single variable theory, we can conclude that $f(0,\ldots,0,z_n)$ is identically zero. Note that this does _not_ imply that $f$ is identically zero, or that $f$ is a function of $z'=(z_1,\ldots,z_{n-1})$ independent of $z_n$, as we can see from the example.

However, if $f$ is not identically zero, say $f(\zeta)\neq0$, we can always extend $\\{\zeta\\}$ to a basis $\\{\hat e_1,\ldots,\hat e_{n-1},\hat e_n=\zeta\\}$ of $\bb C^n$, with dual coordinates $\hat z_1,\ldots,\hat z_n$. Now if $T$ is the change of coordinates $T(\hat z_1,\ldots,\hat z_n)=(z_1,\ldots,z_n)$, and $\hat f=f\circ T$, then

$$\hat f(0,\ldots,0,1)=f(\zeta)\neq0,$$

so $\hat f(0,\ldots,0,\hat z_n)$ is not identically zero. Hence $\hat f$ has finite vanishing order in $\hat z_n$. Thus we have shown:

__Lemma__: If $f$ is holomorphic and not identically zero around $z=0$, then there is a change of coordinates of $\bb C^n$, say $T$, so that $f\circ T$ has finite vanishing order in $z_n$ at 0. $\qed$

For an explicit example, consider $f(z_1,z_2)=z_1z_2$, which has infinite vanishing order in $z_2$. However, by changing coordinates to $\hat z_1=\frac{z_1+z_2}{\sqrt2}$, $\hat z_2=\frac{z_1-z_2}{\sqrt2}$, we have $\hat f(\hat z_1,\hat z_2)=\hat z_1^2+\hat z_2^2$, so $\hat f$ has vanishing order 2 in $\hat z_2$.

## Local behaviour of zeroes

If $f$ has vanishing order $k$ in $z_n$ at 0, then it has a zero of order $k$ on the slice $z'=0$ (ie. $(z_1,\ldots,z_{n-1})=(0,\ldots,0)$). How about on nearby slices?

__Proposition__: If $f$ is holomorphic in a neighbourhood $U\subseteq\bb C^n$ of 0 and has finite vanishing order $k$ in $z_n$ at 0, then there is a polydisc $\overline\Delta(0,r')\times\overline\Delta(0,r_n)\subseteq U$ such that for each $z'\in\overline\Delta(0,r')$, the function

$$f_{z'}:z_n\mapsto f(z',z_n)$$

has exactly $k$ zeroes in $\Delta(0,r_n)$, counting multiplicity, and no zeroes on $\del\Delta(0,r_n)$.

__Proof__: Note that the zero of $f_0$ at $z_n=0$ is of finite order $k$, and thus is isolated. Hence we can take $r_n>0$ small enough such that the only zero of $f_0$ in $\overline\Delta(0,r_n)$ is the one at $z_n=0$.

Let $\delta=\inf_{\del\Delta(0,r_n)}\lvert f(0,z_n)\rvert$. For any $r>0$ small, $f$ is uniformly continuous on the compact set $\overline\Delta(0,r)\times\del\Delta(0,r_n)\subseteq U$, so there exists $0< r'< r$ such that

$$\begin{aligned}
|f_{z'}(z_n)-f_0(z_n)|&=|f(z',z_n)-f(0,z_n)|\\
&<\delta\qquad\text{for all }z'\in\overline\Delta(0,r'),\,|z_n|=r_n.
\end{aligned}$$

Then for each $z'\in\Delta(0,r')$, $f_{z'}$ has no zeroes on $\del\Delta(0,r_n)$, and by Rouché's theorem has the same number of zeroes in $\Delta(0,r_n)$ as $f_0$, namely $k$. $\qed$

We now want a simple function that has the same zeroes $\beta_1,\ldots,\beta_k$ as $f_{z'}$; a good candidate is the unique monic polynomial of degree $k$ with zeroes $\beta_j$, namely

$$h_{z'}(z_n)=\prod_{j=1}^k(z_n-\beta_j)=z_n^k+a_1z_n^{k-1}+\cdots+a_k,$$

where $\beta_j$ and $a_j$ are functions of $z'$. This gives us the factorisation that we want: $f_{z'}$ can be uniquely written as the product of

- a simple function capturing the local properties of the zeroes ($h_{z'}$); and
- a locally nonzero holomorphic function ($\frac{f_{z'}}{h_{z'}}$, because all its singularities are removable).

In fact, we can say more about $h_{z'}$. Note that $a_j$ are the elementary symmetric functions in the zeroes, which can be written as polynomials in the sums of powers

$$\begin{aligned}
s_m&=\sum_{j=1}^k\beta_j^m\\
&=\frac1{2\pi i}\int_{\del\Delta(0,r_n)}\!\zeta^m\frac{f_{z'}'(\zeta)}{f_{z'}(\zeta)}d\zeta\\
&=\frac1{2\pi i}\int_{\del\Delta(0,r_n)}\!\zeta^m\frac{\frac{\del f}{\del\zeta}(z',\zeta)}{f(z',\zeta)}d\zeta.
\end{aligned}$$

From the expression above, we see that every $s_m$, and hence every $a_j$, is analytic in $z'$. 

Motivated by the above discussion, we define a __Weierstrass polynomial__ of degree $k$ in $z_n$ to be a function of the form

$$h(z)=h(z',z_n)=z_n^k+a_1(z')z_n^{k-1}+\cdots+a_k(z'),$$

where $a_j$ are analytic functions in $n-1$ variables $z'$, with $a_j(0)=0$. Then what we have shown above is the following:

__Weierstrass Preparation Theorem__: If $f$ is holomorphic in a neighbourhood $U\subseteq\bb C^n$ of 0 and has finite vanishing order $k$ in $z_n$ at 0, then there is a neighbourhood $V\subseteq U$ of 0 in which there is a unique factorisation

$$f=uh,$$

where $h$ is a Weierstrass polynomial of degree $k$ in $z_n$, and $u$ is holomorphic with $u(0)\neq0$. $\qed$

For later use, we also prove the following related theorem, which is a generalisation of the division algorithm for polynomials.

__Weierstrass Division Theorem__: If $f$ is holomorphic and $h$ is a Weierstrass polynomial of degree $k$ in a neighbourhood $U\subseteq\bb C^n$ of 0, then there is a neighbourhood $V\subseteq U$ of 0 in which there is a unique representation

$$f=gh+q,$$

where $g$ is holomorphic and $q$ is a Weierstrass polynomial of degree less than $k$.

__Proof__: Take $V$ to be a small enough polydisc $\Delta(0,r')\times\Delta(0,r_n)$ such that for each $z'\in\overline\Delta(0,r')$, the slice $h_{z'}$ has exactly $k$ zeroes in $\Delta(r_n)$, and none on the boundary. Let

$$g(z)=\frac1{2\pi i}\int_{\del\Delta(0,r_n)}\!\frac{f_{z'}(\zeta)}{h_{z'}(\zeta)}\frac{d\zeta}{\zeta-z_n}.$$

Note that $g$ is holomorphic in $z_n$ (Cauchy integral) and $z'$ (integrand is holomorphic), so $g$ is holomorphic. Now take $q=f-gh$, so

$$q(z)=\frac1{2\pi i}\int_{\del\Delta(0,r_n)}\!\frac{f_{z'}(\zeta)}{h_{z'}(\zeta)}\frac{h_{z'}(\zeta)-h_{z'}(z_n)}{\zeta-z_n}d\zeta.$$

Note that for fixed $z'$, the function $\frac{h_{z'}(\zeta)-h_{z'}(z_n)}{\zeta-z_n}$ is a polynomial in $z_n$ with degree less than $k$; hence $q$ is a Weierstrass polynomial of degree less than $k$.

For uniqueness, suppose that we have two representations

$$f=gh+q=\tilde gh+\tilde q.$$

Then $q-\tilde q=h(g-\tilde g)$, where on each slice $z'$, the LHS is a polynomial in $z_n$ with degree less than $k$, and the RHS has $k$ zeroes. Hence both sides are identically zero, so $(g,q)=(\tilde g,\tilde q)$. $\qed$


{% comment %}
()* &
{% endcomment %}