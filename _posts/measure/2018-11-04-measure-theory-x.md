---
title: 'Measure Theory (X): The Riemann-Lebesgue Theorem'
layout: post
tag: [measure theory]
date: 2018-11-04 10:16:08 +0800
---

In this post, we characterise when a function is Riemann integrable, and show that the value of the Riemann integral coincides with the Lebesgue integral when it is defined.

<!--more-->

## The Riemann integral

A __partition__ of a closed interval $[a,b]\subseteq\bb R$ is a finite set

$$P=\{a=x_0< x_1<\cdots< x_n=b\}.$$

The __mesh__ of a partition $P=\\{x_k\\}_{k=0}^n$ is

$$|P|=\max_{1\leq k\leq n}(x_k-x_{k-1}).$$

A __tagged partition__ is a pair $(P,(t_k)_ {k=1}^n)$, where $P=\\{x_k\\}_ {k=0}^n$ is a partition and $(t_k)_ {k=1}^n$ is a sequence such that $x_{k-1}\leq t_k\leq x_k$ for all $k$.

Let $f:[a,b]\to\bb R$ be a _bounded_ function. Given a partition $P=\\{x_k\\}_ {k=0}^n$, the __upper sum__ and __lower sum__ of $f$ with respect to $P$ are

$$\begin{aligned}
U(f,P)&=\sum_{k=1}^n(x_k-x_{k-1})\sup_{[x_{k-1},x_k]}f,\\
L(f,P)&=\sum_{k=1}^n(x_k-x_{k-1})\inf_{[x_{k-1},x_k]}f.
\end{aligned}$$

Given a tagged partition $(P,(t_k)_ {k=1}^n)$, the __Riemann sum__ of $f$ with respect to $(P,(t_k)_ {k=1}^n)$ is

$$S(f,P,(t_k)_{k=1}^n)=\sum_{k=1}^n(x_k-x_{k-1})f(t_k).$$

The above definitions correspond to approximating the (signed) area under the curve $y=f(x)$ by $n$ rectangles, where the $k$-th rectangle has base $[x_{k-1},x_k]$, and height

$$\begin{cases}
\sup_{[x_{k-1},x_k]}f&\text{for the upper sum,}\\
\inf_{[x_{k-1},x_k]}f&\text{for the lower sum,}\\
f(t_k)&\text{for the Riemann sum,}\\
\end{cases}$$

respectively. From this, it is clear that

$$L(f,P)\leq S(f,P,(t_k)_{k=1}^n)\leq U(f,P).$$

Moreover, for a given partition $P$, we have $U(f,P)$ and $L(f,P)$ are the supremum and infimum of $S(f,P,(t_k)_ {k=1}^n)$ over all tags $(t_k)_{k=1}^n$, respectively.

__Proposition__: Let $f:[a,b]\to\bb R$. If $P,Q$ are partitions of $[a,b]$ with $P\subseteq Q$, then

$$L(f,P)\leq L(f,Q)\leq U(f,Q)\leq U(f,P).$$

{% comment %}
<!-- 2. If $(P,(t_k)_{k=1}^n)$ is a tagged partition of $[a,b]$, then

   $$L(f,P)\leq S(f,P,(t_k)_{k=1}^n)\leq U(f,P).$$ -->
{% endcomment %}

__Proof__: $L(f,Q)\leq U(f,Q)$ is clear.

For each segment $[x_{k-1},x_k]$ in $P$, consider the points in $Q$ in the interval, say

$$x_{k-1}=y_0< y_1<\cdots< y_m=x_k.$$

Then

$$\begin{aligned}
\sum_{i=1}^m(y_i-y_{i-1})\sup_{[y_{i-1},y_i]}f&\leq\sup_{[x_{k-1},x_k]}f\,\sum_{i=1}^m(y_i-y_{i-1})\\
&=(x_k-x_{k-1})\sup_{[x_{k-1},x_k]}f.
\end{aligned}$$

Summing over $1\leq k\leq n$ gives $U(f,Q)\leq U(f,P)$. An analogous argument gives $L(f,P)\leq L(f,Q)$. $\qed$

{% comment %}
<!-- (2): This is clear from

$$\inf_{x\in[x_{k-1,x_k}]}f(x)\leq f(t_k)\leq\sup_{x\in[x_{k-1,x_k}]}f(x).\ \qed$$ -->
{% endcomment %}

Hence $U(f,P)$ decreases and $L(f,P)$ increases when we refine a partition $P$ into a subpartition $Q$.

For well-behaved functions, we expect that the upper and lower sums converge to the same value under refinement of the partition. As such, we say that a _bounded_ function $f:[a,b]\to\bb R$ is __Darboux integrable__ to $I\in\bb R$ if

$$\inf_PU(f,P)=\sup_PL(f,P)=I,$$

with the supremum and infimum taken over all partitions $P$ of $[a,b]$. Riemann's original notion is slightly different: we say that $f$ is __Riemann integrable__ to $I\in\bb R$ if for all $\eps>0$, there exists $\delta>0$ such that

$$|S(f,P,(t_k)_{k=1}^n)-I|<\eps$$

for all tagged partitions $(P,(t_k)_{k=1}^n)$ of $[a,b]$ with $\lvert P\rvert<\delta$.

__Theorem__: Let $f:[a,b]\to\bb R$ be a bounded function, and let $I\in\bb R$. Then $f$ is Darboux integrable to $I$ if and only if $f$ is Riemann integrable to $I$.

__Proof__: ($\Leftarrow$) For $\eps>0$, fix a partition $P$ of mesh less than $\delta$. Note that $U(f,P)$ is the supremum of the Riemann sum of $f$ over all tags of $P$, so $U(f,P)\leq I+\eps$. Similarly, we have $L(f,P)\geq I-\eps$. Since $\eps>0$ was arbitrary, we have

$$\inf_PU(f,P)\leq I\leq\sup_PL(f,P),$$

and we are done by noting that $\inf_PU(f,P)\geq\sup_PL(f,P)$, so all three terms are equal.

($\Rightarrow$) Let $M=\sup_{[a,b]}\lvert f\rvert<\infty$.

For $\eps>0$, choose a partition $P_0=\\{x_k\\}_{k=0}^n$ such that $U(f,P_0)<I+\frac\eps2$ and $L(f,P_0)>I-\frac\eps2$. Now take

{% comment %}
<!-- $$\delta=\min\left(\min_{1\leq k\leq n}(x_k-x_{k-1}),\frac\eps{2Mn}\right)>0.$$ -->
{% endcomment %}
$$\delta=\frac\eps{2Mn}>0.$$

Now for any partition $P$ with mesh $\lvert P\rvert<\delta$, consider the points in $P$ contained in the interval $[x_{k-1},x_k]$, say

$$x_{k-1}\leq y_0< y_1<\cdots< y_m\leq x_k.$$

Then

$$\begin{aligned}
\sum_{i=1}^m(y_i-y_{i-1})\sup_{[y_{i-1},y_i]}f&\leq\sup_{[x_{k-1},x_k]}f\sum_{i=1}^m(y_i-y_{i-1})\\
&=(y_m-y_0)\sup_{[x_{k-1},x_k]}f\\
&\leq(x_k-x_{k-1})\sup_{[x_{k-1},x_k]}f.
\end{aligned}$$

Summing over all $k$, RHS gives $U(f,P_0)$. On the other hand, LHS gives $U(f,P)$, minus the terms corresponding to intervals of $P$ that do not lie in any $[x_{k-1},x_k]$. Note that there are at most $n-1$ such intervals (because each such interval must contain some $x_k$ for $1\leq k\leq n-1$), so the missing terms have sum  at most

$$(n-1)|P|M<(n-1)\frac\eps{2Mn}M<\frac\eps2.$$

Thus for any choice of tags $(t_k)_{k=1}^n$, we have

$$\begin{aligned}
S(f,P,(t_k)_{k=1}^n)&\leq U(f,P)\\
&< U(f,P_0)+\frac\eps2\\
&< I+\eps.
\end{aligned}$$

Similarly we have $S(f,P,(t_k)_{k=1}^n)>I-\eps$, and we are done. $\qed$

When $f$ is Darboux or Riemann integrable, the value of $I$ is called the __Riemann integral__ of $f$, and written as

$$I=\int_a^b\!f=\int_a^b\!f(x)\,dx.$$


## The Riemann-Lebesgue theorem

__Riemann-Lebesgue theorem__: Let $f:[a,b]\to\bb R$ be a bounded function. Then $f$ is Riemann integrable if and only if $f$ is continuous $\lambda$-a.e. on $[a,b]$.

__Proof__: ($\Rightarrow$) Since $f$ is Darboux integrable, there is a sequence of partitions $(P_n)$ of $[a,b]$ such that

$$\lim_{n\to\infty}U(f,P_n)=\lim_{n\to\infty}L(f,P_n)=\int_a^b\,f(x)\,dx.$$

By replacing $P_n$ by $P_1\cup\cdots\cup P_n$, we may assume that $P_n\subseteq P_{n+1}$ for all $n$. Also, by passing to a subsequence, we may assume that

$$U(f,P_n)-L(f,P_n)<\frac1{4^n}$$

for all $n$.

Let $T_n$ be the union of the intervals $J$ determined by $P_n$ on which

$$\sup_Jf-\inf_Jf\geq\frac1{2^n}.$$

By the inequality above, the total length of these intervals is less than $\frac1{2^n}$. Hence $\lambda(T_n)<\frac1{2^n}$, so

$$T=\bigcup_{n=1}^\infty P_n\cup\bigcup_{n=1}^\infty\bigcap_{m=n}^\infty T_n$$

is a countable union of $\lambda$-null sets, which is also $\lambda$-null.

For any $x\in[a,b]\backslash T$, we have $x\not\in T_n$ for all large $n$. Now $x$ is contained in the interior of some interval $J_n$ determined by $P_n$ (since $x\not\in P_n$), on which

$$|f(y)-f(x)|<\frac1{2^n}\quad\text{for all }y\in J_n.$$

Hence $f$ is continuous at $x$ for all $x\in[a,b]\backslash T$, so $f$ is continuous $\lambda$-a.e.

($\Leftarrow$) Let $M=\sup_{[a,b]}\lvert f\rvert<\infty$.

Let $N$ be the set of discontinuities of $f$, which is $\lambda$-null. For any $\eps>0$, cover $N$ by disjoint open intervals $L_1,\ldots,L_n$ with $\sum_i\lambda(L_i)<\frac\eps{4M}$.

Now $f$ is continuous on $S=[a,b]\backslash\bigcup_iL_i$, which is compact, so $f$ is uniformly continuous on $S$. Hence $S$ can be written as a union of closed intervals $J_1,\ldots,J_m$ with disjoint interior, such that

$$\sup_{J_i}f-\inf_{J_i}f<\frac\eps{2(b-a)}.$$

Consider the partition $P$ of $[a,b]$ determined by the endpoints of all $J_i$ and $L_i$. Then

$$\begin{aligned}
U(f,P)-L(f,P)&=\sum_{i=1}^m\lambda(J_i)(\sup_{J_i}f-\inf_{J_i}f)+\sum_{i=1}^n\lambda(L_i)(\sup_{L_i}f-\inf_{L_i}f)\\
&<(b-a)\frac\eps{2(b-a)}+\frac\eps{4M}2M\\
&=\frac\eps2+\frac\eps2=\eps.
\end{aligned}$$

Hence $\inf_PU(f,P)-\sup_PL(f,P)=0$, so $f$ is Darboux (hence Riemann) integrable. $\qed$

Now we relate the Riemann integral to the Lebesgue integral. Note that given a bounded function $f:[a,b]\to\bb R$, and a partition $P=\\{x_k\\}_{k=0}^n$ of $[a,b]$, we can define the step functions

$$\begin{aligned}
\varphi&=\sum_{k=1}^n\chi_{[x_{k-1},x_k]}\sup_{[x_{k-1},x_k]}f\\
\psi&=\sum_{k=1}^n\chi_{[x_{k-1},x_k]}\inf_{[x_{k-1},x_k]}f.
\end{aligned}$$

Then the Lebesgue integrals of $\varphi$ and $\psi$ are exactly the upper and lower sums:

$$\begin{aligned}
U(f,P)&=\int_{[a,b]}\!\varphi\,d\lambda,\\
L(f,P)&=\int_{[a,b]}\!\psi\,d\lambda.
\end{aligned}$$

We use this observation to show that the Riemann integral, when it is defined, is equal to the Lebesgue integral:

__Theorem__: Let $f:[a,b]\to\bb R$ be a bounded function. If $f$ is Riemann integrable, then $f$ is Lebesgue integrable on $[a,b]$, with

$$\int_{[a,b]}\!f\,d\lambda=\int_a^b\!f(x)\,dx.$$

__Proof__: Let $M=\sup_{[a,b]}\lvert f\rvert<\infty$.

Since $f$ is Darboux integrable, there is a sequence of partitions $(P_n)$ of $[a,b]$ such that

$$\lim_{n\to\infty}U(f,P_n)=\lim_{n\to\infty}L(f,P_n)=\int_a^b\,f(x)\,dx.$$

By replacing $P_n$ by $P_1\cup\cdots\cup P_n$, we may assume that $P_n\subseteq P_{n+1}$ for all $n$.

Let $\varphi_n,\psi_n$ be the step functions on $[a,b]$ associated to the partition $P_n$, constructed as above. Then $\varphi_1\geq\varphi_2\geq\cdots\geq f$, so the sequence $(\varphi_n)$ converges pointwise to a function $\Phi\geq f$. Now

$$\begin{aligned}
\int_a^b\!f(x)\,dx&=\lim_{n\to\infty}U(f,P_n)\\
&=\lim_{n\to\infty}\int_{[a,b]}\!\varphi_n\,d\lambda\\
&=\int_{[a,b]}\!\Phi\,d\lambda.
\end{aligned}$$

Similarly, $(\psi_n)$ converge to $\Psi\leq f$, and

$$\int_a^b\!f(x)\,dx=\int_{[a,b]}\!\Psi\,d\lambda.$$

Now $\Phi\geq f\geq\Psi$ and $\int\\!(\Phi-\Psi)\,d\lambda=0$ implies $\Phi=\Psi$ $\lambda$-a.e., so $\Phi=f$ $\lambda$-a.e. implies

$$\int_a^b\!f(x)\,dx=\int_{[a,b]}\!\Phi\,d\lambda=\int_{[a,b]}\!f\,d\lambda,$$

and we are done. $\qed$