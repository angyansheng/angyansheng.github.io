---
title: "Measure Theory (IX): Littlewood's Three Principles"
layout: post
tag: [measure theory]
date: 2018-10-24 17:12:44 +0800
---

Littlewood's three principles of real analysis are succint statements about the Lebesgue measure on $\bb R^n$. Informally, they are given as follows:
1. Lebesgue measurable sets are "nearly" open sets;
2. Lebesgue measurable functions are "nearly" continuous;
3. $\lambda$-a.e. convergence is "nearly" uniform convergence.

Here, "nearly" is in the sense of "up to a set of measure $\eps$." In this post, we formalise and prove these three statements.

<!--more-->

## Littlewood's first principle

> Lebesgue measurable sets are "nearly" open sets.

The following theorem states the _regularity_ of Lebesgue measure, namely that Lebesgue measurable sets are well-approximated from the outside by open sets, and from the inside by compact sets.

__Theorem__: Let $A\subseteq\bb R^n$. Then $A$ is Lebesgue measurable if and only if for every $\eps>0$, there exists an open set $O$ such that $A\subseteq O$ and $\lambda^* (O\backslash A)<\eps$.

__Proof__: ($\Rightarrow$) We first consider the case when $\lambda(A)<\infty$. Take any countable cover $(I_k)$ of $A$ by half-open intervals with

$$\sum_{k=1}^\infty\lambda(I_k)<\lambda(A)+\frac\eps2,$$

then slightly expand each $I_k$ into a half-open interval $I_k'$ with $I_k\subseteq I_k'^\circ$ and

$$\lambda(I_k')<\lambda(I_k)+\frac\eps{2^{k+1}}.$$

Then $O=\bigcup_kI_k'^\circ$ is an open set (hence Lebesgue measurable) containing $A$, with

$$\begin{aligned}
\lambda(O)&\leq\sum_{k=1}^\infty\lambda(I_k')\\
&<\sum_{k=1}^\infty\lambda(I_k)+\frac\eps2\\
&<\lambda(A)+\eps.
\end{aligned}$$

Thus $\lambda(O\backslash A)=\lambda(O)-\lambda(A)<\eps$.

Now consider the case $\lambda(A)=\infty$. Since $[-m,m)^n\in\mc H_n$ is Lebesgue measurable with finite Lebesgue measure, so is $A_m=A\cap[-m,m)^n$. Hence there exists $O_m\subseteq\bb R^n$ open with $\lambda(O_m\backslash A_m)<\frac\eps{2^m}$, so by taking $O=\bigcup_mO_m$, we have

$$\begin{aligned}
O\backslash A&\subseteq\bigcup_{m=1}^\infty O_m\backslash A_m\\
\implies\lambda(O\backslash A)&\leq\sum_{m=1}^\infty\lambda(O_m\backslash A_m)<\eps.
\end{aligned}$$

($\Leftarrow$) For each $m\geq1$, there exists an open set $A\subseteq O_m\subseteq\bb R^n$ such that $\lambda^* (O_m\backslash A)<\frac1m$. Now $S=\bigcap_mO_m$ is Borel (hence Lebesgue measurable), contains $A$, and

$$\lambda^* (S\backslash A)\leq\lambda^* (O_m\backslash A)<\frac1m$$

for all $m$, so $\lambda^* (S\backslash A)=0$. Since the Lebesgue measure is complete, $S\backslash A$ is Lebesgue measurable; hence $A=S\backslash(S\backslash A)$ is also Lebesgue measurable. $\qed$

__Corollary__: If $A\subseteq\bb R^n$ is Lebesgue measurable and $\lambda(A)<\infty$, then for every $\eps>0$ there exists a compact set $K\subseteq A$ such that $\lambda(A\backslash K)<\eps$.

__Proof__: Let $A_m=A\cap[-m,m]^n$. Note that $(A_m)$ is an increasing sequence of Lebesgue measurable sets with union $A$, so $\lambda(A_m)\to\lambda(A)$. In particular, there exists $N\geq1$ with $\lambda(A_N)>\lambda(A)-\frac\eps2$.

Now $[-N,N]^n\backslash A_N$ is measurable, so by Littlewood's first principle there exists an open set $[-N,N]^n\backslash A_N\subseteq O\subseteq\bb R^n$ with

$$\lambda(O\backslash([-N,N]^n\backslash A_N))<\frac\eps2.$$

Take $K=A_N\backslash O=[-N,N]^n\backslash O$, so $K\subseteq A_N$ and $K$ is closed and bounded, hence compact. Now

$$A_N\backslash K=A_N\cap O\subseteq O\backslash([-N,N]^n\backslash A_N),$$

so $\lambda(A\backslash K)\leq\lambda(A\backslash A_N)+\lambda(A_N\backslash K)<\eps$, as desired. $\qed$

## Lusin's theorem

Littlewood's second principle states:

> Lebesgue measurable functions are "nearly" continuous.

This is formalised in the following result:

__Lusin's theorem__: Let $E\subseteq\bb R^n$ be Lebesgue measurable, with $\lambda(E)<\infty$. Then a function $f:E\to\bb R$ is measurable if and only if for any $\eps>0$, there exists a compact set $K\subseteq E$ with $\lambda(E\backslash K)<\eps$, such that $f\vert_K$ is continuous on $K$.

__Proof__: ($\Leftarrow$) For each $m\geq1$, there exists $K=K_m$ in the statement of the theorem for $\eps=\frac1m$. Note that $f^{-1}(a,\infty)\cap K_m$ is an open set in $K$, hence Borel, hence Lebesgue measurable. Also, $f^{-1}(a,\infty)\cap K_m^c$ has measure $<\eps$. Thus

$$f^{-1}(a,\infty)=\bigcup_{m=1}^\infty(f^{-1}(a,\infty)\cap K_m)\cup\bigcap_{m=1}^\infty(f^{-1}(a,\infty)\cap K_m^c),$$

where the first term is Lebesgue measurable, and the second term is a subset of the $\lambda$-null set $\bigcap_mK_m^c$, and is thus also Lebesgue measurable. Thus $f^{-1}(a,\infty)$ is Lebesgue measurable for all $a\in\bb R$, so $f$ is Lebesgue measurable.

($\Rightarrow$) We proceed by first showing the statement for some special cases.

__$f$ is a measurable step function__: If $f(E)=\\{a_1,\ldots,a_m\\}$, then for each $k$ there exists $K_k\subseteq f^{-1}(a_k)$ compact such that 

$$\lambda(f^{-1}(a_k)\backslash K_k)<\frac\eps m.$$

Hence $K=\bigcup_kK_k$ is a compact subset of $E$ with

$$\lambda(E\backslash K)\leq\sum_{k=1}^m\lambda(f^{-1}(a_k)\backslash K_k)<\eps.$$

Furthermore, $\bb R^n$ is a normal Hausdorff (ie. $T_4$) space, so each $K_k$ is separated from $\bigcup_{j\neq k}K_j$ by an open set $O$; in other words,

$$K_k\subseteq O\subseteq\left(\bigcup_{j\neq k}K_j\right)^c.$$

Hence $f^{-1}(a_k)\cap K=K_k=K_k\cap O$ is open in $K$ for every $k$, so $f\vert_K$ is continuous on $K$.

__$f$ is a bounded measurable function__: Let $(\varphi^\pm_k)$ be two sequences of nonnegative step functions which converge uniformly to $f^\pm$ respectively. Let $\varphi_k=\varphi^+_k-\varphi^-_k$; then $(\varphi_k)$ is a sequence of step functions converging uniformly to $f$.

For each $k\geq1$, take $K_k\subseteq E$ compact such that $\lambda(K_k^c)<\frac\eps{2^k}$ and $\varphi_k\vert_{K_k}$ is continuous on $K_k$. Then $K=\bigcap_kK_k$ is compact, with

$$\lambda(K^c)\leq\sum_{k=1}^\infty\lambda(K_k^c)<\eps,$$

and $(\varphi_k\vert_K)$ is a sequence of continuous functions converging pointwise to $f\vert_K$; hence $f\vert_K$ is continuous on $K$, and the convergence is uniform in $K$.

__$f$ is measurable__: Since

$$\bigcap_{k=1}^\infty\{|f|>k\}=\emptyset,$$

there exists $N\geq1$ with $\lambda\\{\lvert f\rvert>N\\}<\frac\eps2$. Now there exists $K\subseteq E\backslash\\{\lvert f\rvert>N\\}$ compact with $\lambda((E\backslash\\{\lvert f\rvert>N\\})\backslash K)<\frac\eps2$ and $f\vert_K$ is continuous on $K$; then

$$\lambda(E\backslash K)\leq\lambda((E\backslash\{|f|>N\})\backslash K)+\lambda\{|f|>N\}<\eps,$$

and we are done. $\qed$

## Egorov's theorem

Littlewood's third principle states:

> $\lambda$-a.e. convergence is "nearly" uniform convergence.

This notion is captured by the following theorem, which in fact holds for general measure spaces.

__Egorov's theorem__: Let $(\Omega,\Sigma,\mu)$ be a finite measure space (ie. $\mu(\Omega)<\infty$). Let $f,f_1,f_2,\ldots:\Omega\to\bb R$ be $\mu$-measurable functions such that $(f_n)$ converges $\mu$-a.e. to $f$. Then for any $\eps>0$, there exists $K\in\Sigma$ such that $\mu(K^c)<\eps$ and $f_n\to f$ uniformly on $K$.

__Proof__: For $m,n\geq1$, let $E_{mn}=\\{\lvert f-f_n\rvert>\frac1m\\}$, which is $\mu$-measurable. Note that for fixed $m$, we have $\lvert f-f_n\rvert\leq\frac1m$ holds for all large enough $n$ $\mu$-a.e.; in other words

$$\bigcap_{k=1}^\infty\bigcup_{n=k}^\infty E_{mn}$$

is $\mu$-measurable, hence $\mu$-null. Thus there exists $k_m$ such that $F_m=\bigcup_{n=k_m}^\infty E_{mn})$ satisfies $\mu(F_m)<\frac\eps{2^m}$. By possibly replacing each $k_m$ by a bigger number, we may assume that $k_1< k_2<\cdots$.

Now take $K=\bigcap_mF_m^c$; then

$$\begin{aligned}
\mu(K^c)&=\mu\left(\bigcup_{m=1}^\infty F_m\right)\\
&\leq\sum_{m=1}^\infty\mu(F_m)<\eps,
\end{aligned}$$

Now for every $\omega\in K=\bigcap_m\bigcap_{n\geq k_m}E_{mn}^c$, by definition we have

$$|f(\omega)-f_n(\omega)|\leq\frac1m\quad\text{for all }n\geq k_m.$$

Hence $(f_n)\to f$ uniformly on $K$. $\qed$

__Proposition__: Let $(\Omega,\Sigma,\mu)=(E,\Sigma_E,\lambda)$, where $E\subseteq\bb R^n$ is Lebesgue measurable with $\lambda(E)<\infty$, and $\Sigma_E$ is the collection of Lebesgue measurable subsets of $E$. Then the set $K$ in Egorov's theorem can be chosen to be compact.

__Proof__: Take $\tilde K\subseteq E$ with $\lambda(E\backslash\tilde K)<\frac\eps2$, such that $(f_k)\to f$ uniformly on $\tilde K$. By regularity of $\lambda$, there exists $K\subseteq\tilde K$ compact with $\lambda(\tilde K\backslash K)<\frac\eps2$. Then 

$$\lambda(E\backslash K)\leq\lambda(E\backslash\tilde K)+\lambda(\tilde K\backslash K)<\eps,$$

and $(f_k)\to f$ uniformly on $K$. $\qed$
