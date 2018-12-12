---
title: 'Several Complex Variables (IV): Domains of Holomorphy'
layout: post
tag: [several complex variables]
date: 2018-09-06 16:02:45 +0800
---

In this post, we will look at _domains of holomorphy_, which are (roughly speaking) domains which do not exhibit [Hartogs's phenomenon]({% post_url 2018-09-06-several-complex-variables-iii %}) anywhere. Historically, characterising domains of holomorphy was a central problem in several complex variables theory; here we will only present some basic results.

<!--more-->

## Domains of holomorphy

An open set $U\subseteq\bb C^n$ is called a __domain of holomorphy__ if there is a holomorphic function $f$ on $U$ such that for any $w\in\del U$ and any polyradius $r$, there is no holomorphic function on $\Delta(w,r)$ that is equal to $f$ on any component of $\Delta(w,r)\cap U$. Intuitively, this means that $f$ has no local holomorphic extension across any boundary point of $U$.

Note that this is not the same as saying that $f$ has no global extension to a larger domain. For instance, the principal branch of $\log$ on $\bb C\backslash(-\infty,0)$ has no holomorphic (or even continuous) extension to a larger domain. However, any point on $(-\infty,0)$ has a neighbourhood where $\log$ has a branch agreeing with the principal branch on, say, the upper half plane.

This definition is only useful for more than one variable, because of the following:

__Proposition__: Any domain $U\subseteq\bb C$ is a domain of holomorphy.

__Proof__: For any $p\in\del U$, the function $f(z)=\frac1{z-p}$ does not have a holomorphic extension to any neighbourhood of $p$. $\qed$

Now we give some simple constructions of domains of holomorphy.

__Proposition__: If $U\subseteq\bb C^n$ and $V\subseteq\bb C^m$ are domains of holomorphy, then so is $U\times V$.

__Proof__: Take any $(p,q)\in\del(U\times V)=(\del U\times V)\cup(U\times\del V)$; without loss of generality assume $(p,q)\in\del U\times V$. Since $U$ is a domain of holomorphy, there exists $f$ holomorphic on $U$ which cannot be extended on any polydisc around $p$. Hence the function $F(u,v)\coloneqq f(u)$ has no holomorphic extension on any polydisc around $(p,q)$. $\qed$

In particular, any polydisc is a domain of holomorphy. Compare this with the Hartogs figure (constructed in the [previous post]({% post_url 2018-09-06-several-complex-variables-iii %})), which is homeomorphic to a polydisc but _not_ a domain of holomorphy.

__Proposition__: Any convex domain $U\subseteq\bb C^n$ is a domain of holomorphy.

__Proof__: At any point $p\in\del U$, there is a supporting hyperplane of $U$, ie. a real-valued $\bb R$-linear functional $\ell:\bb C^n\to\bb R$ with $\ell(u)>\ell(p)$ for all $u\in U$. Now we have

$$\ell(z)=\sum_{k=1}^n\alpha_kz_k+\beta_k\overline{z_k},$$

and since $\ell$ is real-valued we have $\beta_k=\overline{\alpha_k}$. Hence $\ell(z)=\Re h(z)$, where $h(z)=2\sum\alpha_kz_k$ is a $\bb C$-linear functional. Hence $f(z)=\frac1{h(z)-h(p)}$ is holomorphic on $U$ and has no holomorphic extension on any polydisc around $p$. $\qed$

## The Cartan-Thuller theorem

If a domain $U$ is not a domain of holomorphy, ie. $U$ exhibits Hartogs's phenomenon, then there exists a point $p\in\del U$ such that every holomorphic function on $U$ can be extended to a neighbourhood of $p$; in particular, $f$ cannot blow up near $p$. It is natural to ask if this property characterises domains of holomorphy.

The above notion is formalised as follows. Given $K\subseteq U$, define the __holomorphically convex hull__ of $K$ to be

$$\hat K\coloneqq\{w\in U\,:\,|f(w)|\leq\|f\|_K\text{ for all }f\text{ holomorphic on }U\},$$

where $\lVert f\rVert_K=\sup_{z\in K}\lvert f(z)\rvert$. We say that $U$ is __holomorphically convex__ if $\hat K$ is compact for all compact $K\subseteq U$.

Why does this capture the property of blowing up at a boundary point? Note that for $K$ compact, 

- $\hat K$ is bounded: take $f$ to be the coordinate functions $z_k$; 
- $\hat K$ is relatively closed in $U$: $\hat K$ is the intersection of closed sets in $U$, one for each $f$.

Hence $\hat K$ fails to be compact exactly when it accumulates at some point $p\in\del U$, in which case no holomorphic function on $U$ blows up near $p$.

__Cartan-Thuller theorem__: A domain $U\subseteq\bb C^n$ is a domain of holomorphy if and only if it is holomorphically convex.

__Proof__: $(\Rightarrow)$: Let $K\subseteq U$ be compact. Then there exists $s>0$ such that $\Delta(a,\hat s)\coloneqq\Delta(a,(s,\ldots,s))\subseteq U$ for all $a\in K$. By estimates from the Cauchy integral formula, we have

$$\left|\frac{\del^{i_1+\cdots+i_n}}{\del z_1^{i_1}\cdots\del z_n^{i_n}}f(a)\right|\leq\frac{i_1!\cdots i_n!}{r^{i_1+\cdots+i_n}}\|f\|_{\bigcup_{a\in K}\Delta(a,\hat s)},$$

for all $a\in K$, and thus for all $a\in\hat K$. Hence the power series for $f$ about $a$ converges in $\Delta(a,\hat s)$ for all $a\in\hat K$.

As noted before, if $\hat K$ is not compact then it shares some boundary point $b$ with $U$. Take $a\in\hat K\cap\Delta(b,\hat s)$, so $b\in\Delta(a,\hat s)$. But every holomorphic function $f$ has an extension to $\Delta(a,\hat s)$, which is a neighbourhood of $b$, contradicting the fact that $U$ is a domain of holomorphy. Hence $\hat K$ is compact for all compact $K\subseteq U$, so $U$ is holomorphically convex.

$(\Leftarrow)$: Let $\\{K_j\\}$ be an increasing sequence of compact subsets of $U$ such that every compact subset of $U$ is contained in some $K_j$; for instance, we can take

$$K_j\coloneqq\{z\in\Delta(0,(j,\ldots,j))\,:\,d(z,\bb C^n\backslash U)\leq\frac1j\}.$$

Since $U$ is holomorphically convex, $\hat K_j$ is compact.

Let $\\{w_j\\}$ be an enumeration of a countable dense subset of $U$ (for instance, the points in $U$ with all real and imaginary coordinates rational), and let $S_j$ be the sphere of maximal radius contained in $U$ centred at $w_j$. Since $S_j$ is either all of $\bb C^n$ or contains points close to $\del U$, there exists $z_j\in S_j\backslash\hat K_j$.

By definition of $\hat K_j$, there exists a holomorphic function $f_j$ with $f_j(z_j)=1$ and $\lVert f_j\rVert_{K_j}<1$. By taking $f_j$ to a large power, we may assume that $\lVert f_j\rVert_{K_j}<2^{-j}$. Now on each $K_j$, the sum $\sum_{j=1}^\infty jf_j$ converges uniformly, so the product $f\coloneqq\prod_{j=1}^\infty(1-f_j)^j$ converges uniformly as well. Note that $f$ is:

- holomorphic on $U$;
- not identically zero: the infinite product converges, hence is nonzero, on $K_1$;
- has a zero at $z_j$ of total order at least $j$ (ie. all terms of order less than $j$ in the power series for $f$ at $z_j$ vanish).

Let $\Delta$ be a ball of radius $\delta$ centred at some $p\in\del U$. Then any component $\mc C$ of $U\cap\Delta$ contains a subsequence $w_{j_k}\to p$, say with $\lvert w_{j_k}-p\rvert<\frac\delta2$. Then the radius of $S_{j_k}$ is less than $\frac\delta2$, so $\mc C$ contains every $S_{j_k}$, and in particular every $z_{j_k}$. Hence $\mc C$ contains a sequence of zeroes of $f$ of arbitrarily high total order with limit $p$.

Now if $\hat f$ is a holomorphic continuation of $f$ from $\mc C$ to $\Delta$, then $\hat f$ and its partial derivatives of all orders must vanish at $p$, so $\hat f\equiv0$ on $\Delta$, contradicting the fact that $f$ is not identically zero on $U$. Hence $U$ is a domain of holomorphy. $\qed$

 
{% comment %}
()* &
{% endcomment %}