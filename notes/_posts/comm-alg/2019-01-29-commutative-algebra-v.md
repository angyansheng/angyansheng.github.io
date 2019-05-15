---
title: 'Commutative Algebra (V): Composition Series'
layout: post
date: 2019-01-29 17:57:01 +0800
tag: [commutative algebra]
macros: >-
  "\\ann":"\\operatorname{ann}",
---

Besides finite generation and finite presentation, there are other measures of the "size" of an $A$-module $M$. For instance, we can look at the lengths of certain chains of submodules of $M$, known as _composition series_. We will see in this post that this length is well-defined, and well-behaved under natural operations on modules.

<!--more-->

## Simple modules

A nonzero $A$-module $M$ is __simple__ if the only submodules of $M$ are $0$ and $M$.

__Proposition__: Let $M$ be a nonzero $A$-module. Then the following are equivalent:
1. $M$ is a simple module;
2. Every nonzero element $\omega\in M$ generates $M$;
3. $M\cong A/\mf m$ as $A$-modules for some maximal ideal $\mf m\subseteq A$.

__Proof__: ($1\Rightarrow2$) For any $\omega\neq0$ in $M$, the submodule $\omega M$ is nonzero, and thus is equal to $M$.

($2\Rightarrow3$) Fix $\omega\neq0$ in $M$. Then the $A$-module map $\varphi:A\to M$ defined by $\varphi(a)=a\omega$ is surjective, so

$$M\cong A/\ker\varphi=A/\ann(\omega).$$

Since the only submodules of $M$ are $0$ and $M$, by the lattice isomorphism theorem, the only ideals of $A$ containing $\ann(\omega)$ are $A$ and $\ann(\omega)$. Hence $\ann(\omega)$ is a maximal ideal of $A$.

($3\Rightarrow1$) Since the only ideals of $A$ containing $\mf m$ are $A$ and $\mf m$, by the lattice isomorphism theorem, the only submodules of $A/\mf m$ are $A/A=0$ and $A/\mf m$. Hence $A/\mf m$ is a simple module. $\qed$

## Composition series

Let $M$ be an $A$-module. A __composition series__ of $M$ is a chain of submodules

$$M=M_0\supseteq M_1\supseteq\cdots\supseteq M_r=0,$$

such that each $M_i/M_{i+1}$ is simple. In this case, $r$ is called the __composition length__, or simply __length__, of the composition series.

Note that if $M_i/M_{i+1}$ is simple, then for any submodule $M_{i+1}\subseteq M'\subseteq M_i$, we have

$$\begin{aligned}
M'/M_{i+1}&\in\{0,M_i/M_{i+1}\}\\
\implies M'&\in\{M_{i+1},M_i\},
\end{aligned}$$

so if we insert more submodules into a composition series of $M$, we can only extend it trivially. Hence composition series can be seen as maximal chains of submodules of $M$.

We define the __composition length__ or __length__ of $M$, written $\ell(M)$, as the minimal length of a composition series of $M$, or $\infty$ if $M$ does not have a composition series.

We will now show that _any_ composition series of $M$ has length $\ell(M)$.

__Proposition__: Let $M$ be an $A$-module, and let $N\subseteq M$ be a submodule. Then $\ell(N)\leq\ell(M)$, with equality if and only if $N=M$.

__Proof__: Write $l=\ell(M)$, and take a composition series

$$M=M_0\supseteq M_1\supseteq\cdots\supseteq M_l=0$$

of length $l$. Then

$$N=N\cap M_0\supseteq N\cap M_1\supseteq\cdots\supseteq N\cap M_r=0.\tag{$* $}$$

By the second isomorphism theorem, for all $i$ we have

$$\frac{N\cap M_i}{N\cap M_{i+1}}=\frac{N\cap M_i}{(N\cap M_i)\cap M_{i+1}}\cong\frac{(N\cap M_i)+M_{i+1}}{M_{i+1}},$$

which is a submodule of the simple module $M_i/M_{i+1}$. Hence $\frac{N\cap M_i}{N\cap M_{i+1}}$ is either zero or simple for all $i$.

Now by removing repetitions from the chain $(* )$, we get a composition series for $N$ with length at most $l$. Thus $\ell(N)\leq l$.

If equality occurs, then there are no repetitions in $(* )$, so for all $i$ we have

$$\frac{(N\cap M_i)+M_{i+1}}{M_{i+1}}=\frac{M_i}{M_{i+1}},$$

so $(N\cap M_i)+M_{i+1}=M_i$.

Now we prove by induction that $N\cap M_i=M_i$ for all $i$. This is clear for $i=l$; if the claim holds for $M_{i+1}$, then

$$\begin{aligned}
N\cap M_i&=(N\cap M_i)+(N\cap M_{i+1})\\
&=(N\cap M_i)+M_{i+1}=M_i,
\end{aligned}$$

so the claim also holds for $M_i$. Now taking $i=0$ gives

$$M=M_0=N\cap M_0=N\cap M=N,$$

as desired. $\qed$

__Corollary__: For any strictly descending chain of submodules

$$M\supsetneq N_1\supsetneq\cdots\supsetneq N_s,$$

we have $s\leq\ell(M)$.

__Proof__: Note that

$$\ell(M)>\ell(N_1)>\cdots>\ell(N_s)\geq0,$$

so

$$\ell(M)\geq\ell(N_1)+1\geq\cdots\geq\ell(N_s)+s\geq s.\ \qed$$

__Corollary__: Any two composition series of $M$ has length $\ell(M)$.

__Proof__: By the above corollary, for any composition series

$$M=M_0\supseteq M_1\supseteq\cdots\supseteq M_r=0,$$

we have $r\leq\ell(M)$. Hence by minimality of $\ell(M)$, we have $r=\ell(M)$. $\qed$

## Jordan-Hölder theorem

The above result is only one part of the Jordan-Hölder theorem for modules. We will not need the full theorem in this course, but we give the proof here for completeness.

The __composition factors__ of a composition series

$$M=M_0\supseteq M_1\supseteq\cdots\supseteq M_r=0$$

are the quotients $M_i/M_{i+1}$.

__Jordan-Hölder Theorem__: Any two composition series of an $A$-module $M$ have the same composition factors, up to permutation and isomorphism.

__Proof__: We proceed by induction on $\ell(M)$. If $\ell(M)=0$ then $M=0$, and there is nothing to prove.

Suppose that the statement holds for all $A$-modules with length less than $r$, and let $M$ be an $A$-module with two composition series

$$\begin{aligned}
M&=M_0\supseteq M_1\supseteq\cdots\supseteq M_r=0,\\
M&=N_0\supseteq N_1\supseteq\cdots\supseteq N_r=0.
\end{aligned}$$

If $M_1=N_1$, then by induction hypothesis, the lists of composition factors for 

$$\begin{aligned}
M_1&\supseteq M_2\supseteq\cdots\supseteq M_r=0,\\
N_1&\supseteq N_2\supseteq\cdots\supseteq N_r=0.
\end{aligned}$$

are the same up to permutation and isomorphism. Now $M_0/M_1=N_0/N_1$, so the the lists of composition factors for the original composition series are the same up to permutation and isomorphism.

If $M_1\neq N_1$, then $M_1$ is a maximal proper submodule of $M$, so $M_1+N_1=M$. Write $K=M_1\cap N_1$; then by the second isomorphism theorem, we have

$$\begin{aligned}
N_1/K&\cong(M_1+N_1)/M_1=M/M_1,\\
M_1/K&\cong(M_1+N_1)/N_1=M/N_1.
\end{aligned}\tag{$** $}$$

In particular, both of these modules are simple.

Now pick any composition series for $K$, say

$$K=K_0\supseteq K_1\supseteq\cdots\supseteq K_s=0.$$

Then by induction hypothesis, the lists of composition factors for

$$\begin{aligned}
M_1&\supseteq K\supseteq K_1\supseteq\cdots\supseteq K_s=0,\\
M_1&\supseteq M_2\supseteq\cdots\supseteq M_r=0
\end{aligned}$$

are the same up to permutation and isomorphism, so this is still true when we add $M$ at the start of both composition series. We have an analogous argument with $M_i$ replaced by $N_i$; hence it remains to show that the lists of composition factors for

$$\begin{aligned}
M&\supseteq M_1\supseteq K\supseteq K_1\supseteq\cdots\supseteq K_s=0,\\
M&\supseteq N_1\supseteq K\supseteq K_1\supseteq\cdots\supseteq K_s=0,\\
\end{aligned}$$

are the same up to permutation and isomorphism. But clearly the composition factors after $K$ are the same, and by $(** )$ the two composition factors before $K$ are simply swapped. Thus the lists of composition factors for the original composition series are the same up to permutation and isomorphism, and induction is complete. $\qed$

## Properties of composition length

We first note that composition length is additive with respect to short exact sequences:

__Proposition__: If $M$ is an $A$-module and $N\subseteq M$ is a submodule, then

$$\ell(M)=\ell(N)+\ell(M/N).$$

__Proof__: By the lattice isomorphism theorem, any composition series of $M/N$ must be of the form

$$M/N\supseteq M_1/N\supseteq\cdots\supseteq M_t/N=0,$$

for submodules $N\subseteq M_i\subseteq M$. Also, by the third isomorphism theorem we have

$$M_i/M_{i+1}\cong(M_i/N)/(M_{i+1}/N),$$

which is a simple module. Hence for any composition series of $N$, say

$$N=N_0\supseteq N_1\supseteq\cdots\supseteq N_s=0,$$

the following is a composition series of $M$:

$$\begin{aligned}
M&\supseteq M_1\supseteq\cdots\supseteq M_t\\
&\supseteq N_1\supseteq\cdots\supseteq N_s=0.
\end{aligned}$$

Hence $\ell(M)=s+t=\ell(N)+\ell(M/N)$. $\qed$

__Corollary__: If $M_i$ are $A$-modules of finite length, such that the sequence

$$0\to M_1\to M_2\to\cdots\to M_n\to 0$$

is exact, then

$$\sum_{i=1}^n(-1)^i\ell(M_i)=0.$$

__Proof__: Every long exact sequence splits into short exact sequences

$$\begin{aligned}
0\to M_1&\to M_2\to K_2\to0,\\
0\to K_2&\to M_3\to K_3\to0,\\
&\quad\vdots\\
0\to K_{n-2}&\to M_{n-1}\to M_n\to0.
\end{aligned}$$

Then by the previous proposition, we have

$$\begin{aligned}
-\ell(M_1)+\ell(M_2)-\ell(K_2)&=0,\\
\ell(K_2)-\ell(M_3)+\ell(K_3)&=0,\\
\vdots\qquad&\\
(-1)^n\left[\ell(K_{n-2})-\ell(M_{n-1})+\ell(M_n)\right]&=0.
\end{aligned}$$

Summing all of the above identities gives the desired claim. $\qed$

__Proposition__: Let $\mf m$ be a finitely generated maximal ideal of $A$. Then for any $\nu\geq1$, we have $\ell(A/\mf m^\nu)<\infty$.

__Proof__: Firstly, note that if $\mf m$ is generated by $\\{a_1,\ldots,a_j\\}$ (as an ideal of $A$, ie. as an $A$-module), then $\mf m^i$ is generated by

$$\left\{a_{k_1}a_{k_2}\cdots a_{k_i}\,:\,1\leq k_1,\ldots,k_i\leq j\right\},$$

which is a finite set. Hence $\mf m^i$ is also finitely generated for all $i\geq1$.

Since $A/\mf m^i\cong(A/\mf m^{i-1})/(\mf m^{i-1}/\mf m^i)$ as $A$-modules, by induction we have

$$\ell(A/\mf m^\nu)=\ell(A/\mf m)+\ell(\mf m/\mf m^2)+\cdots+\ell(\mf m^{\nu-1}/\mf m^\nu).$$

Let $k=A/\mf m$, which is a field. Since each $\mf m^i$ is a finite $A$-module, each $\mf m^i/\mf m^{i+1}$ is a finite $A/\mf m$-module, ie. a finite-dimensional $k$-vector space. Moreover, in $\mf m^i/\mf m^{i+1}$, the $A$-submodules are exactly the $A/\mf m$-submodules, ie. the $k$-vector subspaces; hence

$$\ell(\mf m^i/\mf m^{i+1})=\dim_k(\mf m^i/\mf m^{i+1})<\infty,$$

so $\ell(A/\mf m^\nu)<\infty$. $\qed$

We will see later that $\ell(A/\mf m^\nu)$, as a function of $\nu$, is closely related to the ring structure of $A$.