---
title: 'Measure Theory (VI): Convergence Theorems'
layout: post
tag: [measure theory]
date: 2018-10-23 12:04:55 +0800
---

In this post, we will see that the Lebesgue integral is well-behaved under limits. More precisely, the Lebesgue integral commutes with limit operations in many situations.

<!--more-->

## Monotone convergence theorem

__Monotone convergence theorem__: Let $0\leq f_1\leq f_2\leq\cdots$ be a sequence of measurable functions, and let $f=\lim_nf_n$. Then

$$\int\!f\,d\mu=\lim_{n\to\infty}\int\!f_n\,d\mu.$$

__Proof__: Note that $f\geq f_n$ implies $\int\\!f\,d\mu\geq\lim_{n\to\infty}\int\\!f_n\,d\mu$.

On the other hand, pick any nonnegative step function $\Phi\leq f$, and let $\nu(S)=\int_S\\!\Phi\,d\mu$ for all $S\in\Sigma$; we have previously shown that $\nu$ is a measure. Now let

$$S_n=\{\omega\in\Omega\,:\,f_n(\omega)\geq c\Phi(\omega)\},$$

and recall that $S_1\subseteq S_2\subseteq\cdots$ and $\bigcup_nS_n=\Omega$. Hence

$$\begin{aligned}
\lim_n\int\!f_n\,d\mu&\geq\lim_n\int_{S_n}f_n\,d\mu\\
&\geq c\lim_n\int_{S_n}\Phi\,d\mu\\
&=c\lim_n\nu(S_n)\,d\mu\\
&=c\nu(\Omega)=c\int\!\Phi\,d\mu.
\end{aligned}$$

Now $c\to1^-$ gives $\lim_n\int\\!f_n\,d\mu\geq\int\\!\Phi\,d\mu$. Taking supremum over all $\Phi\leq f$ gives $\int\\!f\,d\mu\leq\lim_{n\to\infty}\int\\!f_n\,d\mu$, and we are done. $\qed$

One feature of measure theory is that we can usually weaken the assumptions to hold $\mu$-a.e. instead of everywhere. For instance, we can do this in the case of MCT, as follows:

__Corollary__: Let $(f_n)$ be a sequence of measurable functions such that $f_n\geq0$ and $f_n\leq f_{n+1}$ hold __$\mu$-a.e.__ for each $n$. Suppose that $f$ is a measurable function such that $(f_n)\to f$ __$\mu$-a.e.__ Then

$$\int\!f\,d\mu=\lim_{n\to\infty}\int\!f_n\,d\mu.$$

__Proof__: By countable additivity of $\mu$, the set

$$S=\bigcup_{n=1}^\infty\{f_n<0\}\cup\bigcup_{n=1}^\infty\{f_n< f_{n+1}\}\cup\{(f_n)\not\to f\}$$

is of measure 0. Thus if we define

$$\tilde f_n=f_n\chi_{\Omega\backslash S},\qquad\tilde f=f\chi_{\Omega\backslash S},$$

then $0\leq\tilde f_1\leq\tilde f_2\leq\cdots$ and $(\tilde f_n)\to\tilde f$ on all of $\Omega$, so MCT implies

$$\int\!f\,d\mu=\int\!\tilde f\,d\mu=\lim_{n\to\infty}\int\!\tilde f_n\,d\mu=\lim_{n\to\infty}\int\!f_n\,d\mu.\ \qed$$


## Fatou's lemma

__Fatou's lemma__: Let $(f_n)$ be a sequence of nonnegative measurable functions. Then

$$\int\!\liminf_nf_n\,d\mu\leq\liminf_n\int\!f_n\,d\mu.$$

__Proof__: Let $g_n=\inf_{m\geq n}f_m$. Then $0\leq g_1\leq g_2\leq\cdots$, so MCT gives

$$\begin{aligned}
\int\!\liminf_nf_n\,d\mu&=\int\!\lim_ng_n\,d\mu\\
&=\lim_n\int\!g_n\,d\mu\\
&\leq\liminf_n\int\!f_n\,d\mu,
\end{aligned}$$

since $\int\\!g_n\,d\mu\leq\int\\!f_n\,d\mu$ for every $n$. $\qed$

Note that strict inequality may occur. For instance, take $\Omega=\bb N$, $\mu$ the counting measure on $\bb N$, and $f_n=\chi_{\\{n\\}}$. Then

$$\begin{aligned}
\int\!\liminf_nf_n\,d\mu&=\int\!0\,d\mu=0,\\
\liminf_n\int\!f_n\,d\mu&=\liminf_n1=1.
\end{aligned}$$


## Lebesgue dominated convergence theorem

__Lebesgue dominated convergence theorem__: Let $(f_n)$ be a sequence of measurable functions that converge to $f$. Suppose that there is an integrable function $g$ such that $\lvert f_n\rvert\leq g$ for all $n$. Then

$$\lim_{n\to\infty}\int\!f_n\,d\mu=\int\!f\,d\mu.$$

__Proof__: Since $g\pm f_n\geq0$, we have by Fatou's lemma that

$$\begin{aligned}
\int\!g\,d\mu-\limsup_n\int\!f_n\,d\mu&=\liminf_n\int\!(g-f_n)\,d\mu\\
&\geq\int\!\liminf_n(g-f_n)\,d\mu\\
&=\int\!g\,d\mu-\int\!f\,d\mu,\\
\int\!g\,d\mu+\liminf_n\int\!f_n\,d\mu&=\liminf_n\int\!(g+f_n)\,d\mu\\
&\geq\int\!\liminf_n(g+f_n)\,d\mu\\
&=\int\!g\,d\mu+\int\!f\,d\mu.
\end{aligned}$$

Hence

$$\limsup_n\int\!f_n\,d\mu\leq\int\!f\,d\mu\leq\liminf_n\int\!f_n\,d\mu,$$

so all three expressions are equal and we are done. $\qed$

We also have the $\mu$-a.e. version:

__Corollary__: Let $(f_n)$ be a sequence of measurable functions that converge to $f$ __$\mu$-a.e.__ Suppose that there is an integrable function $g$ such that $\lvert f_n\rvert\leq g$ __$\mu$-a.e.__ for all $n$. Then

$$\lim_{n\to\infty}\int\!f_n\,d\mu=\int\!f\,d\mu.$$

__Corollary__ (Bounded convergence theorem): Let $(\Omega,\Sigma,\mu)$ be a __finite__ measure space (ie. $\mu(\Omega)<\infty$). Let $(f_n)$ be a sequence of measurable functions such that for some $M>0$, we have $\lvert f_n(\omega)\rvert\leq M$ for all $n$ and $\omega\in\Omega$. If there is a measurable function $f$ such that $\lim_nf_n=f$ $\mu$-a.e., then

$$\lim_{n\to\infty}\int\!f_n\,d\mu=\int\!f\,d\mu.$$

__Proof__: Apply LDCT to the function $g(\omega)=M$, which is integrable since $\int\\!\lvert g\rvert\,d\mu=M\mu(\Omega)<\infty$. $\qed$

<!-- A less obvious application of LDCT is the following:

__Proposition__: Let $f:\bb R^2\to\bb R$ be a function such that $\frac{\del f}{\del y}$ exists on all of $\bb R^2$. Suppose that for fixed $y$, the functions $f(x,y)$ and $\frac{\del f}{\del y}$ are Lebesgue integrable in $x$. Also suppose that there is a Lebesgue integrable function $g:\bb R\to\bb R$ such that

$$\left|\frac{\del f}{\del y}(x,y)\right|\leq g(x)$$

for all $x,y$. Then

$$\frac\del{\del y}\int_{\bb R}\!f(x,y)\,d\lambda(x)=\int_{\bb R}\!\frac{\del f}{\del y}(x,y)\,d\lambda(x).$$ -->

## Convergence in measure

Let $(f_n)$ be a sequence of measurable functions. We say that $(f_n)$ __converges in measure__ to a measurable function $f$ if for any $\eps>0$, we have

$$\lim_{n\to\infty}\mu\{|f_n-f|\geq\eps\}=0.$$

For example, take $\Omega=\bb N$ and $\mu$ to be the counting measure. Then $(\chi_{\\{n\\}})$ is a sequence of measurable functions converging pointwise to zero, but not converging in measure to any function $f$. To see this, note that:
- If $\lvert f(m)\rvert\geq\eps$ for some $m\in\bb N$ and $\eps>0$, then $\mu\\{\lvert\chi_{\\{n\\}}-f\rvert\geq\eps\\}\geq1$ for $n>m$;
- Otherwise, we have $f\equiv0$, so $\mu\\{\lvert\chi_{\\{n\\}}-f\rvert\geq1\\}\geq1$ for all $n$.

<!-- Examples -->

__Proposition__: Let $f$ and $g$ be measurable functions. Suppose that $(f_n)$ is a sequence of measurable functions converging in measure to $f$. Then $(f_n)$ also converges in measure to $g$ if and only if $f=g$ $\mu$-a.e.

__Proof__: ($\Rightarrow$) Note that $\lvert f-g\rvert\leq\lvert f_n-f\rvert+\lvert f_n-g\rvert$. Hence

$$\{|f-g|\geq\eps\}\subseteq\{|f_n-f|\geq\frac\eps2\}\cup\{|f_n-g|\geq\frac\eps2\}.$$

Since the measure of both sets on RHS tend to $0$ as $n\to\infty$, LHS must have measure $0$, ie. $f=g$ $\mu$-a.e.

($\Leftarrow$) By an analogous argument to the above, we have

$$\{|f_n-g|\geq\eps\}\subseteq\{|f_n-f|\geq\eps\}\cup\{f\neq g\}.$$

Now note that the measure of the first set on RHS goes to $0$ as $n\to\infty$, and the measure of the second set is $0$. Hence the measure of LHS also goes to $0$ as $n\to\infty$, ie. $(f_n)$ converge in measure to $g$. $\qed$

__Proposition__: Let $(f_n)$ be a sequence of measurable functions converging in measure to a measurable function $f$. Then there is a subsequence $(f_{n_k})$ that converges pointwise to $f$ $\mu$-a.e.

__Proof__: For each $k$, choose $n_k$ such that

$$\mu\{|f_{n_k}-f|>\frac1{2^k}\}<\frac1{2^k}.$$

Let $S_k$ denote the set above, and consider the limsup

$$S=\bigcap_{m\geq1}\bigcup_{k\geq m}S_k.$$

Note that

$$\begin{aligned}
\mu\left\{\bigcup_{k\geq m}S_k\right\}&\leq\sum_{k\geq m}\mu(S_k)\\
&\leq\sum_{k\geq m}\frac1{2^k}=\frac1{2^{m-1}},
\end{aligned}$$

so $\mu(S)=0$. Also, for all $\omega\in\Omega\backslash S$, there exists $N\geq1$ such that

$$\omega\not\in S_k\quad\text{for all}\quad k\geq N.$$

Hence $\lvert f_{n_k}(\omega)-f(\omega)\rvert\leq\frac1{2^k}$ for all $k\geq N$, so $\lim_kf_{n_k}(\omega)=f(\omega)$ for all $\omega\not\in S$. Thus $(f_{n_k})\to f$ $\mu$-a.e. $\qed$

We can now prove the following extension of the LDCT, replacing pointwise convergence with convergence in measure:

__Theorem__: Let $(f_n)$ be a sequence of measurable functions converging in measure to a measurable function $f$. Suppose that $g$ is an integrable function such that $\lvert f_n\rvert\leq g$ for all $n$. Then

$$\lim_{n\to\infty}\int\!f_n\,d\mu=\int\!f\,d\mu.$$

__Proof__: We recall a result from real analysis: a sequence of real numbers $(a_n)$ converges to $L$ if and only if every subsequence $(a_{n_k})$ has a subsubsequence $(a_{n_{k_l}})$ converging to $L$.

As such, we consider any subsequence $(f_{n_k})$; note that this subsequence also converges in measure to $f$. By the previous proposition, there is a subsubsequence $(f_{n_{k_l}})$ converging to $f$ $\mu$-a.e., so by LDCT we have

$$\lim_{l\to\infty}\int\!f_{n_{k_l}}\,d\mu=\int\!f\,d\mu.$$

Hence the sequence $(\int\\!f_n\,d\mu)$ converges to $\int\\!f\,d\mu$, as desired. $\qed$

<!-- () -->