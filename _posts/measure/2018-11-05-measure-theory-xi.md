---
title: 'Measure Theory (XI): $L^p$ Spaces'
layout: post
tag: [measure theory]
date: 2018-11-05 13:52:44 +0800
---

Let $(\Omega,\Sigma,\mu)$ be a measure space. For $1\leq p<\infty$, define the set

$$\mc L^p(\Omega,\Sigma,\mu)\coloneqq\{f:\Omega\to[-\infty,\infty]\,:\,\int\!|f|^p\,d\mu<\infty\}.$$

Also, for $p=\infty$, define

$$\mc L^\infty(\Omega,\Sigma,\mu)\coloneqq\{f:\Omega\to[-\infty,\infty]\,:\,\exists M<\infty[|f|\leq M\ \mu\text{-a.e.}]\}.$$

<!--more-->

We will write $\mc L^p(\mu)$ or simply $\mc L^p$ if the measure space $(\Omega,\Sigma,\mu)$ is clear from context.

__Proposition__: For $1\leq p\leq\infty$, if $f,g\in \mc L^p$ and $c\in\bb R$, then $cf,f+g\in \mc L^p$.

__Proof__: For $1\leq p<\infty$, note that

$$\begin{aligned}
\int\!|cf|^p\,d\mu&=|c|^p\int\!|f|^p\,d\mu<\infty,\\
\int\!|f+g|^p\,d\mu&\leq\int\!|2\max(f,g)|^p\,d\mu\\
&\leq2^p\int\!(|f|^p+|g|^p)\,d\mu<\infty.
\end{aligned}$$

For $p=\infty$, note that $\lvert f\rvert\leq M$ and $\lvert g\rvert\leq N$ $\mu$-a.e. imply $\lvert cf\rvert\leq\lvert c\rvert M$ and $\lvert f+g\rvert\leq M+N$ $\mu$-a.e. $\qed$

This shows that $\mc L^p$ is a vector space for all $1\leq p\leq\infty$.

## Hölder's and Minkowski's inequalities

There is a natural way of measuring the "size" of $\mc L^p$ functions: for $f\in \mc L^p$, define the __$p$-norm__ of $f$ as

$$\|f\|_p\coloneqq\left(\int\!|f|^p\,d\mu\right)^{1/p}$$

if $1\leq p<\infty$, and

$$\|f\|_\infty\coloneqq\inf\{M\geq0\,:\,|f|\leq M\ \mu\text{-a.e.}\}$$

if $p=\infty$. By the definition of $\mc L^p$, we have $\\|f\\|_p<\infty$ for $f\in \mc L^p$.

It turns out that if $1< p<\infty$, then $\mc L^p$ is closely related to $\mc L^q$ when $\frac1p+\frac1q=1$. In this case, we call $p$ and $q$ __conjugate indices__. Note that this condition is equivalent to any of the following:
- $q=\frac p{p-1}$
- $p-1=\frac pq$

__Lemma__ (Young's inequality): Let $1< p<\infty$, and let $q=\frac p{p-1}$. Then for all $a,b\geq0$, we have

$$ab\leq\frac{a^p}p+\frac{b^q}q,$$

with equality if and only if $a^p=b^q$.

__Proof__: Since the exponential function is strictly convex, by Jensen's inequality we have

$$e^{\lambda x+(1-\lambda)y}\leq\lambda e^x+(1-\lambda)e^y$$

for any $x,y\geq0$, $0<\lambda<1$, with equality if and only if $x=y$. The claim follows by setting $\lambda=\frac1p$ (so $1-\lambda=\frac1q$), $x=a^p$ and $y=b^q$. $\qed$

__Proposition__ (Hölder's inequality): Let $1\leq p<\infty$, and let $q=\frac p{p-1}$. If $f\in \mc L^p$ and $g\in \mc L^q$, then $fg\in \mc L^1$ and

$$\|fg\|_1\leq\|f\|_p\|g\|_q.$$

More precisely, we have

$$\|f\|_p=\sup_{\|g\|_q\leq1}\left|\int\!fg\,d\mu\right|.$$

__Proof__: If $p=1$, note that $\lvert fg\rvert\leq\lvert f\rvert\\|g\\|_\infty$ holds $\mu$-a.e. The statement now follows by integration.

For the last equality, choose $g\equiv1$, which has $\infty$-norm equal to $1$.

If $p>1$, by Young's inequality and integration we have

$$\int\!\frac{|f|}{\|f\|_p}\frac{|g|}{\|g\|_q}\,d\mu\leq\frac1p\int\!\frac{|f|^p}{\|f\|_p^p}\,d\mu+\frac1q\int\!\frac{|g|^q}{\|g\|_q^q}\,d\mu.$$

Now LHS is equal to $\dfrac{\\|fg\\|_1}{\\|f\\|_p\\|g\\|_q}$, while RHS is equal to $\frac1p+\frac1q=1$, and the inequality is proven.

Equality holds when, for instance,

$$\frac{|f|^p}{\|f\|_p^p}=\frac{|g|^q}{\|g\|_q^q},$$

ie. when $\lvert g\rvert$ is proportional to $\lvert f\rvert^{p/q}$. Hence for the last equality, we may take

$$g=\frac{|f|^{p/q}}{\||f|^{p/q}\|_q},$$

which clearly has $q$-norm equal to $1$. $\qed$

{% comment %}
<!-- Note that Hölder's inequality also holds for $(p,q)=(1,\infty)$ or $(\infty,1)$:

__Proposition__: If $f\in L^1$ and $g\in L^\infty$, then $fg\in L^1$ and

$$\|fg\|_1\leq\|f\|_1\|g\|_\infty.$$

Moreover, we have

$$\|f\|_1=\sup_{\|g\|_\infty\leq1}\left|\int\!fg\,d\mu\right|.$$

__Proof__: Note that $\lvert fg\rvert\leq\lvert f\rvert\\|g\\|_\infty$ holds $\mu$-a.e. The statement now follows by integration.

For the last equality, choose $g\equiv1$, which has $\infty$-norm equal to $1$. $\qed$ -->
{% endcomment %}

However, the last equality in the theorem might not hold for $(p,q)=(\infty,1)$, as the following example shows.

__Example__: Let $\Omega=\\{x\\}$ be a singleton set, and $\mu$ be the measure on $\Omega$ with $\mu(x)=\infty$. If $f(x)=1$ then $\\|f\\|_\infty=1$, while

$$\|g\|_1\leq1\implies g(x)=0,$$

so $\sup_{\\|g\\|_1\leq1}\left\lvert\int\\!fg\,d\mu\right\rvert=0.$

__Proposition__ (Minkowski's inequality): Let $1\leq p\leq\infty$. If $f,g\in \mc L^p$, then

$$\|f+g\|_p\leq\|f\|_p+\|g\|_p.$$

__Proof__: We first split

$$\|f+g\|_p^p\leq\int\!|f||f+g|^{p-1}\,d\mu+\int\!|g||f+g|^{p-1}\,d\mu.$$

Now $p-1=\frac pq$, so Hölder's inequality gives

$$\begin{aligned}
\int\!|f||f+g|^{p-1}\,d\mu&=\int\!|f||f+g|^{p/q}\,d\mu\\
&\leq\|f\|_p\||f+g|^{p/q}\|_q\\
&=\|f\|_p\left(\int\!|f+g|^p\,d\mu\right)^{1/q}\\
&=\|f\|_p\|f+g\|_p^{p/q}.
\end{aligned}$$

Applying the same argument to the other term, we have

$$\|f+g\|_p^p\leq(\|f\|_p+\|g\|_p)\|f+g\|_p^{p/q}.$$

Dividing both sides by $\|f+g\|_p^{p/q}$, and noting that $p-\frac pq=\frac pp=1$, gives the desired result. $\qed$

This inequality can be interpreted as the triangle inequality; hence the $p$-norm is a seminorm on $\mc L^p$.

## The quotient space $L^p$

Now we can take the quotient of $\mc L^p$ by the subspace of measurable functions with $p$-norm $0$, namely those which are zero $\mu$-a.e.; this is the same as considering equivalence classes of $\mc L^p$ functions under the equivalence relation of $\mu$-a.e. equality. We denote the quotient space by $L^p(\Omega,\Sigma,\mu)$, $L^p(\mu)$, or simply $L^p$.

Since equivalent $\mc L^p$ functions have the same $p$-norm, the $p$-norm is also defined on the quotient space $L^p$, where it is in fact a norm.

Hence $L^p$ is a normed vector space of "$\mc L^p$ functions defined up to $\mu$-null sets." Note that the elements of $L^p$ are not actual functions, but only equivalence classes of functions: for example, if $x\in\Omega$ and $\mu(\\{x\\})=0$, then for any equivalence class $[f]\in L^p$, the value $f(x)$ is not well-defined.

{% comment %}
<!-- A word on notation: in most sources, the space $L^p$ in fact denotes the _quotient space_, whereas in this set of notes $L^p$ denotes the original function space. However, it is easy to verify that all our results hold even if the hypotheses are weakened to hold only $\mu$-a.e., so all our results here pass over to the quotient space. -->
{% endcomment %}

## The Riesz-Fischer Theorem

We now show that the $L^p$ is actually complete under the $p$-norm, ie. $L^p$ is a Banach space.

__Riesz-Fischer theorem__: Let $1\leq p\leq\infty$. Then any Cauchy sequence $([f_k])$ in $L^p$ has a limit $[f]\in L^p$.

__Proof__: Take representatives $f_k\in\mc L^p$, so the sequence $(f_k)$ in $\mc L^p$ satisfies the following property: for any $\eps>0$, there exists $N\geq1$ such that $\\|f_k-f_j\\|_ p<\eps$ for all $k,j\geq N$. Now we need to show that there exists $f\in\mc L^p$ with $\lim_{k\to\infty}\\|f_k-f\\|_ p=0$.

By taking $\eps=\frac1{2^i}$, there exists $1\leq k_1< k_2<\cdots$ such that $\\|f_{k_i}-f_{k_{i+1}}\\|_p\leq\frac1{2^i}$ for all $i\geq1$. Now consider the functions

$$g_n=|f_{k_1}|+\sum_{i=1}^n|f_{k_i}-f_{k_{i+1}}|.$$

Note that $0\leq g_1\leq g_2\leq\cdots$, and

$$\lim_{n\to\infty}g_n=g=|f_{k_1}|+\sum_{i=1}^\infty|f_{k_i}-f_{k_{i+1}}|.$$

By Minkowski's inequality, we have

$$\|g_n\|_p\leq\|f_{k_1}\|_p+\sum_{i=1}^n\|f_{k_i}-f_{k_{i+1}}\|_p<\|f_{k_1}\|_p+1,$$

so by monotone convergence theorem we have

$$\begin{aligned}
\int\!g^p\,d\mu&=\lim_{n\to\infty}\int\!g_n^p\,d\mu\\
&\leq(\|f_{k_1}\|_p+1)^p<\infty.
\end{aligned}$$

Hence the set $S=\\{g=\infty\\}$ is $\mu$-null. Thus the function

$$f(\omega)=\begin{cases}f_{k_1}(\omega)+\sum_{i=1}^\infty(f_{k_{i+1}}(\omega)-f_{k_i}(\omega))&\omega\not\in S\\0&\omega\in S\end{cases}$$

is finite-valued (since the series converges absolutely in $\Omega\backslash S$) and satisfies $\lvert f\rvert\leq g$, so $f\in\mc L^p$.

Note that the partial sums of $f$ on $\Omega\backslash S$ form the sequence $(f_{k_i})$, so $f-f_{k_n}\to0$ $\mu$-a.e. Also,

$$|f-f_{k_n}|=\left|\sum_{i=n+1}^\infty(f_{k_{i+1}}-f_{k_i})\right|\leq g,$$

so by LDCT we have

$$\lim_{n\to\infty}\int\!|f-f_{k_n}|^p\,d\mu=\int\!\lim_{n\to\infty}|f-f_{k_n}|^p\,d\mu=0,$$

so $\\|f-f_{k_n}\\|_ p\to0$. Hence $([f_{k_n}])\to[f]$ in $L^p$.

Now the Cauchy sequence $([f_k])$ in $L^p$ has a convergent subsequence, so the whole sequence converges to $[f]$ as well, as desired. $\qed$


{% comment %}
<!-- We call a sequence $(f_k)$ in $\mc L^p$ __$p$-Cauchy__ if the sequence of equivalence classes $([f_k])$ is Cauchy in $L^p$. This is 

Since the $p$-norm on $L^p$ is induced from $\mc L^p$, the theorem is equivalent to the following statement in $\mc L^p$:

Let $(f_k)$ be a sequence in $\mc L^p$ such that for any $\eps>0$, there exists $N\geq1$ such that $\\|f_k-f_j\\|_p<\eps$ for all $k,j\geq N$. Then 

> Of course, the $p$-Cauchy sequences correspond to actual Cauchy sequences in the quotient space,  -->
{% endcomment %}