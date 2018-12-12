---
title: 'Measure Theory (III): Measurable Functions'
layout: post
tag: [measure theory]
date: 2018-10-15 15:43:40 +0800
---

One major application of measure theory is in integration theory, for situations where the usual Riemann integral does not apply. In this post, we look at _measurable functions_, which are sufficently "nice" to be integrable.

<!--more-->

From here on we will abuse notation for inverse images of functions, such as writing $f^{-1}(a)=f^{-1}(\\{a\\})$, or $f^{-1}(a,\infty]=f^{-1}((a,\infty])$.

Let $(\Omega,\Sigma)$ be a measurable space. A function $f:\Omega\to[-\infty,\infty]$ is called __$\Sigma$-measurable__ (or __measurable__ if $\Sigma$ is clear from context) if for all $a\in\bb R$, the set

$$f^{-1}(a,\infty]=\{\omega\in\Omega\,:\,f(\omega)>a\}$$

is measurable, ie. $f^{-1}(a,\infty]\in\Sigma$.

Here are some examples.

- For any $A\subseteq\Omega$, define the __characteristic function__

  $$\chi_A:\Omega\to\bb R,\qquad\omega\mapsto\begin{cases}1&\omega\in A\\0&\omega\not\in A.\end{cases}$$

  Then we have

  $$\chi_A^{-1}(a,\infty]=\begin{cases}\Omega&a<0\\A&0\leq a<1\\\emptyset&1\leq a,\end{cases}$$

  so $\chi_A$ is a measurable function if and only if $A$ is a measurable set.
- Let $(\Omega,\Sigma)=(\bb R,\mc B)$, the set of real numbers with the Borel $\sigma$-algebra. If $f:\bb R\to\bb R$ is continuous, then for any $a\in\bb R$, the set $f^{-1}(a,\infty]$ is open, hence Borel measurable. Thus $f$ is a measurable function.

__Proposition__: Let $f:\Omega\to[-\infty,\infty]$ be measurable. Then the following sets are measurable for any $a\in\bb R$:
1. $f^{-1}[-\infty, a)$;
2. $f^{-1}(a)$;
3. $f^{-1}[a,\infty]$, $f^{-1}[-\infty,a]$;
4. $f^{-1}(\infty)$, $f^{-1}(-\infty)$.

__Proof__: It suffices to note that

$$\begin{aligned}
f^{-1}[a,\infty]&=\bigcap_{n=1}^\infty f^{-1}(a-\frac1n,\infty],\\
f^{-1}[-\infty,a]&=\Omega\backslash f^{-1}(a,\infty],\\
f^{-1}[-\infty,a)&=\Omega\backslash f^{-1}[a,\infty],\\
f^{-1}(a)&=f^{-1}[-\infty,a]\cap f^{-1}[a,\infty],\\
f^{-1}(\infty)&=\bigcap_{n=1}^\infty f^{-1}(n,\infty],\\
f^{-1}(-\infty)&=\bigcap_{n=1}^\infty f^{-1}[-\infty,-n).\qed
\end{aligned}$$

## Constructing measurable functions

We would now like to build up more examples of measurable functions by $+$ and $\times$, like how we know all polynomials are continuous without using the $\eps$-$\delta$ definition. However, we need to careful since we are working with functions with values in the extended reals $[-\infty,\infty]$ instead of the reals $(-\infty,\infty)$. Let us adopt the following conventions:
- $\infty+(-\infty)$ is undefined;
- $\pm\infty+x=\pm\infty$ in all other cases;
- $0\cdot\pm\infty=0$;
- $x\cdot(\pm\infty)=\pm\infty$ in all other cases.

Now for $f,g:\Omega\to[-\infty,\infty]$, we may define the sum $f+g:\Omega\to[-\infty,\infty]$ by

$$(f+g)(\omega)=\begin{cases}f(\omega)+g(\omega)&\text{if the sum is defined}\\0&\text{else}.\end{cases}$$

The product $fg$ is defined similarly.

__Proposition__: Let $f,g$ be $\Sigma$-measurable functions. Then the functions $cf$ (for $c\in\bb R$), $\lvert f\rvert$, $f\pm g$, $\max(f,g)$, $\min(f,g)$ and $fg$ are measurable.

__Proof__: Note that $cf=0=\chi_\emptyset$ if $c=0$, which is measurable.

Otherwise, observe that

$$\begin{aligned}
(cf)^{-1}(a,\infty]&=\begin{cases}f^{-1}(\frac ac,\infty]&c>0\\f^{-1}[-\infty,\frac ac)&c<0,\end{cases}\\
(\max(f,g))^{-1}(a,\infty]&=f^{-1}(a,\infty]\cup g^{-1}(a,\infty],\\
(f+g)^{-1}(a,\infty]&=\bigcup_{q\in\bb Q}(f^{-1}(q,\infty]\cap g^{-1}(a-q,\infty]\\
&\cup\begin{cases}(f^{-1}(\infty)\cap g^{-1}(-\infty))\cup(f^{-1}(-\infty)\cap g^{-1}(\infty))&a<0\\\emptyset&a\geq0.\end{cases}
\end{aligned}$$

Hence $cf$, $\max(f,g)$ and $f+g$ are measurable, so

$$\begin{aligned}
\min(f,g)&=-\max(-f,-g)\\
f-g&=f+(-g)
\end{aligned}$$

are measurable as well.

Define $f^+=\max(f,0)$ and $f^-=-\min(f,0)$, which are measurable. Then $\lvert f\rvert=f^++f^-$ is also measurable. Now

$$(f^2)^{-1}(a,\infty]=\begin{cases}(|f|)^{-1}(\sqrt a,\infty]&a\geq0\\\Omega&a<0,\end{cases}$$

so $f^2$ is measurable. Hence

<!-- $$fg=\begin{cases}\frac{(f+g)^2-(f-g)^2}4&\text{in }f^{-1}((-\infty,\infty))\cap g^{-1}((-\infty,\infty))\\0&\text{in }(f^{-1}(\{0\})\cap g^{-1}(\{\pm\infty\}))\cup(f^{-1}(\{\pm\infty\})\cap g^{-1}(\{0\})\\\infty&\text{else}\end{cases}$$ -->
$$fg=\begin{cases}\frac{(f+g)^2-(f-g)^2}4&f,g\neq\pm\infty\\0&(f,g)=(0,\pm\infty)\text{ or }(\pm\infty,0)\\\infty&\text{else}\end{cases}$$

is also measurable, and we are done. $\qed$

The functions $f^+=\max(f,0)$ and $f^-=-\min(f,0)$ defined in the proof are called the __positive part__ and __negative part__ of $f$ respectively. Note that:
- $f^+,f^-\geq0$;
- $f^+-f^-=f$; and
- $f^++f^-=\lvert f\rvert$.

__Corollary__: $f$ is measurable if and only if $f^+$ and $f^-$ are both measurable.

> In the future, we will use the decomposition $f=f^+-f^-$ to extend the definition of the Lebesgue integral from nonnegative measurable functions to general measurable functions.

Now we check that measurability is also well-behaved under limits:

__Proposition__: Let $(f_n)$ be a sequence of $\Sigma$-measurable functions. Then $\inf f_n$, $\sup f_n$, $\liminf f_n$ and $\limsup f_n$ are measurable.

__Proof__: If $f=\inf f_n$ then

$$f^{-1}(a,\infty]=\bigcap_{n=1}^\infty f_n^{-1}(a,\infty],$$

so $f$ is measurable. Then $\sup f_n=-\inf(-f_n)$ is also measurable. Now

$$\begin{aligned}
\liminf_{n\to\infty}f_n&=\sup_{n\geq1}\inf_{m\geq n}f_n,\\
\limsup_{n\to\infty}f_n&=\inf_{n\geq1}\sup_{m\geq n}f_n,
\end{aligned}$$

so $\liminf f_n$, $\limsup f_n$ are also measurable. $\qed$

## Step functions

A __step function__ on a measurable space $(\Omega,\Sigma)$ is a linear combination of measurable characteristic functions, ie. a function of the form

$$\sum_{k=1}^nc_k\chi_{A_k},$$

where $c_k\in\bb R$ and $A_k\in\Sigma$. Clearly if $f,g$ are step functions and $c\in\bb R$, then $cf$ and $f+g$ are also step functions.

__Proposition__: A function $f$ on a measurable space $(\Omega,\Sigma)$ is a step function if and only if it is measurable and $f(\Omega)$ is finite.

__Proof__: ($\Rightarrow$) If $f$ is a step function, then $f=\sum_{k=1}^nc_k\chi_{A_k}$ is a sum of measurable functions, and hence is measurable. Moreover,

$$f(\Omega)\subseteq\left\{\sum_{k=1}^n\eta_kc_k\,:\,\eta_k\in\{0,1\}\right\},$$

so $\lvert f(\Omega)\rvert\leq2^n$ is finite.

($\Leftarrow$) If $f(\Omega)\in\\{c_1,\ldots,c_m\\}$, then $A_k=f^{-1}(c_k)$ are pairwise disjoint measurable sets whose union is $\Omega$. Now $f=\sum_{k=1}^nc_k\chi_{A_k}$ holds in each $A_k$, so it must hold in all of $\Omega$, so $f$ is a step function. $\qed$

Since the above decomposition can be performed for any step function, we get:

__Proposition__: Any step function on a measurable space $(\Omega,\Sigma)$ can be written in the form $\sum_{k=1}^ma_k\chi_{B_k}$ where $a_k\in\bb R$ and $B_k\in\Sigma$ are pairwise disjoint.

In defining the Lebesgue integral, we will often need to approximate measurable functions by using step functions. The following result assures us that we can always do so.

__Theorem__: A function $f:\Omega\to[-\infty,\infty]$ is measurable if and only if there is a sequence of step functions $(f_n)$ such that $\lim_{n\to\infty}f_n(\omega)=f(\omega)$ for all $\omega\in\Omega$. Moreover:
- if $f\geq0$, then $f_n$ can be chosen such that $0\leq f_1\leq f_2\leq\cdots$;
- if $f$ is bounded, then $f_n$ can be chosen to converge to $f$ uniformly on $\Omega$.

__Proof__: ($\Leftarrow$) Note that $f_n$ measurable implies $f=\lim_nf_n$ is measurable.

($\Rightarrow$) For each $n\geq1$, consider the _truncation_ of $f$ to $[-n,n]$, given by

$$F_n(\omega)=\begin{cases}n&f(\omega)>n\\f&-n\leq f(\omega)\leq n\\-n&f(\omega)<-n.\end{cases}$$

Note that $F_n=\min(\max(f,-n),n)$, so $F_n$ is measurable. Also,

$$F_n(\omega)=\begin{cases}n&f(\omega)=\infty\\f(\omega)&f(\omega)\neq\pm\infty,\,n>|f(\omega)|\\-n&f(\omega)=-\infty,\end{cases}$$

so $\lim_{n\to\infty}F_n(\omega)=f(\omega)$ for all $\omega\in\Omega$.

Now define

$$f_n=\frac1n\lfloor nF_n\rfloor,$$

and note that $0\leq F_n-f_n<\frac1n$. Hence

$$\lim_{n\to\infty}f_n(\omega)=\lim_{n\to\infty}F_n(\omega)=f(\omega).$$

If $f\geq0$, then $F_n\geq0$, and so $f_n\geq0$. Also, note that $\lfloor2x\rfloor\geq2\lfloor x\rfloor$ for all $x\in\bb R$, which implies $f_n\leq f_{2n}$. Hence we get the desired increasing sequence by replacing $(f_n)$ with $(f_{2^n})$.

If $f$ is bounded, then $F_n=f$ for all $n>\sup_\Omega\lvert f\rvert$, so $\sup_\Omega\lvert f-f_n\rvert\leq\frac1n$ gives $(f_n)\to f$ uniformly on $\Omega$. $\qed$

{% comment %}
<!-- ## Complete measure spaces

A measure space $(\Omega,\Sigma,\mu)$ is called __complete__ if any subset of a $\mu$-null set is in $\Sigma$.

__Proposition__: Let $(\Omega,\Sigma,\mu)$ be a complete measure space. If $f$ is measurable and $g=f$ a.e., then $g$ is measurable. -->
{% endcomment %}