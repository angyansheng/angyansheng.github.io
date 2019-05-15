---
title: 'Commutative Algebra (VI): Chain Conditions'
layout: post
date: 2019-02-14 16:30:00 +0800
tag: [commutative algebra]
macros: >-
  "\\rad":"\\operatorname{rad}",
---

We have previously considred finite generated and finite presented modules. In this post, we look at other finiteness properties of modules based on _chain conditions_.

<!--more-->

## Chain conditions

__Proposition__: Let $\Gamma$ be a partially ordered set. Then the following conditions are equivalent:
1. Any nonempty $S\subseteq\Gamma$ has a maximal element (ie. an element $x\in S$ such that $x\nless x'$ for all $x'\in S$);
2. Any ascending chain $x_1< x_2<\cdots$ of elements of $\Gamma$ must stop after finitely many steps (ie. there does not exist an infinite ascending chain);
3. Any nondecreasing chain $x_1\leq x_2\leq\cdots$ of elements in $\Gamma$ must be eventually constant (ie. there exists $N\geq1$ such that $x_n=x_N$ for all $n\geq N$).

__Proof__: ($1\Rightarrow2$) The contrapositive is clear: if $x_1< x_2<\cdots$ is an infinite ascending chain, then $S=\\{x_n\,:\,n\geq1\\}$ does not have a maximal element.

($2\Rightarrow3$) By removing repeated terms from a nondecreasing chain, we get an ascending chain, which only has finitely many terms by hypothesis; hence all terms after the first appearance of the largest term are equal to the largest term.

($3\Rightarrow1$) We prove the contrapositive. Take $S\subseteq\Gamma$ nonempty such that $S$ has no maximal element. By the axiom of choice, there exists a function $\varphi:S\to S$ such that $\varphi(x)>x$ for all $x\in S$. Pick any $x_1\in S$, and inductively define $x_{n+1}=\varphi(x_n)$. Then $x_1< x_2<\cdots$ is an infinite ascending chain, which in particular is not eventually constant. $\qed$

The equivalent conditions above are called the __ascending chain condition (a.c.c.)__ for a partially ordered set $\Gamma$. By reversing the order, we define the __descending chain condition (d.c.c.)__ analogously.

__Proposition__: If $\Gamma$ satisfies a.c.c. (resp. d.c.c.) and $\Gamma'\subseteq\Gamma$, then $\Gamma'$ also satisfies a.c.c. (resp. d.c.c.).

__Proof__: Every nonempty $S\subseteq\Gamma$ has a maximal (resp. minimal) element; in particular, so does every nonempty $S\subseteq\Gamma'$. $\qed$

## Noetherian and Artinian modules

Let $A$ be a (commutative unital) ring, and $M$ an $A$-module. Note that the set of submodules of $M$ form a partially ordered set under inclusion. We say that $M$ is a __Noetherian module__ (resp. __Artinian module__) if its set of submodules satisfies a.c.c. (resp. d.c.c.).

For instance, consider $\bb Z$ as a $\bb Z$-module. Its submodules are $\\{0\\}$ and $n\bb Z$ for integers $n\geq1$. Hence ascending chains of (nonzero) submodules correspond to decreasing sequences of positive integers, which must terminate in finitely many steps by the well-ordering property of $\bb Z_{>0}$. Thus $\bb Z$ is Noetherian. However, we have the infinite descending sequence

$$\bb Z\supsetneq2\bb Z\supsetneq2^2\bb Z\supsetneq\cdots,$$

so $\bb Z$ is not Artinian.

For another example, let $W$ be the abelian group of _dyadic rationals_,

$$W=\left\{\frac a{2^k}\,:\,a\in\bb Z,\,k\geq0\right\}.$$

Now consider the $\bb Z$-module $M=W/\bb Z$. For any submodule $N\subseteq M$, note that if $\frac a{2^k}\in N$ and $a$ is odd, then $a$ is invertible mod $2^k$ implies that $\frac1{2^k}\in N$. Hence we must have one of the following:

$$\begin{aligned}
N&=0\\
\text{or }N&=\frac1{2^k}\bb Z\qquad\text{for some }k\geq0\\
\text{or }N&=\bigcup_{k\geq0}\frac1{2^k}\bb Z=M.
\end{aligned}$$

Hence descending chains of submodules of $M$ correspond to decreasing sequences of $k$, which must terminate after finitely many steps. Thus $M$ is Artinian. However, we have the infinite ascending sequence

$$\{0\}\subsetneq\frac12\bb Z\subsetneq\frac1{2^2}\bb Z\subsetneq\cdots,$$

so $M$ is not Noetherian.

The Noetherian and Artinian properties carry over to submodules and quotient modules:

__Proposition__: Let $M$ be a Noetherian (resp. Artinian) $A$-module, and let $N\subseteq M$ be a submodule. Then $N$ and $M/N$ are also Noetherian (resp. Artinian).

__Proof__: Note that the set of submodules of $N$ is a subset of the set of submodules of $M$. Also, by the lattice isomorphism theorem, the set of submodules of $M/N$ is order-isomorphic to a subset of the set of submodules of $M$ (namely, those which contain $N$). The result now follows from the previous proposition. $\qed$.

In the other direction, we have the following result:

__Proposition__: Let $M$ be an $A$-module, and let $N\subseteq M$ be a submodule. If $N$ and $M/N$ are both Noetherian (resp. Artinian), then $M$ is also Noetherian (resp. Artinian).

__Proof__: We prove the statement for Noetherian modules; the proof for Artinian modules is analogous.

Let $M_1\subseteq M_2\subseteq\cdots$ be a nondecreasing chain of submodules of $M$. By hypothesis, the nondecreasing chains

$$\begin{aligned}
M_1\cap N&\subseteq M_2\cap N\subseteq\cdots,\\
\frac{M_1+N}N&\subseteq\frac{M_2+N}N\subseteq\cdots
\end{aligned}$$

are both eventually constant. Hence there exists $n_0$ such that for all $n\geq n_0$, we have

$$\begin{aligned}
M_n\cap N&=M_{n_0}\cap N,\\
\frac{M_n}{M_n\cap N}\cong\frac{M_n+N}N&=\frac{M_{n_0}+N}N\cong\frac{M_{n_0}}{M_{n_0}\cap N}.
\end{aligned}$$

But $M_{n_0}\subseteq M_n$, so $M_n=M_{n_0}$ for all $n\geq n_0$.

Hence the nondecreasing chain $M_1\subseteq M_2\subseteq\cdots$ is eventually constant, so $M$ is Noetherian. $\qed$

Recall that a __composition series__ of $M$ is a chain of submodules

$$M=M_0\supseteq M_1\supseteq\cdots\supseteq M_r=0,$$

such that each $M_i/M_{i+1}$ is simple. We have proven in the [previous post]({% post_url 2019-01-29-commutative-algebra-v %}) that any two composition series of $M$ have the same length, known as the __(composition) length__ $\ell(M)$.

__Proposition__: Let $M$ be an $A$-module. Then $M$ has a composition series if and only if it is both Noetherian and Artinian.

__Proof__: ($\Rightarrow$) We proved that for any submodules $M_1\subsetneq M_2$ of $M$, we have $\ell(M_1)<\ell(M_2)$. Hence any ascending or descending chain of submodules of $M$ has at most $\ell(M)+1$ elements, so $M$ is Noetherian and Artinian.

($\Leftarrow$) Let $M_0=\\{0\\}$, and inductively define $M_{k+1}$ to be a minimal submodule strictly containing $M_k$. Since $M$ is Artinian, this always exists unless $M_k=M$. Note that by minimality, $M_{k+1}/M_k$ has no proper submodules except $0$, ie. $M_{k+1}/M_k$ is simple.

Now we have an ascending chain $M_0\subsetneq M_1\subsetneq\cdots$ of submodules of $M$. Since $M$ is Noetherian, this chain must stop after finitely many steps, so $M_n=M$ for some $n\geq0$. Then

$$0=M_0\subseteq M_1\subseteq\cdots\subseteq M_n=M$$

is a composition series for $M$. $\qed$

Hence being both Noetherian and Artinian is equivalent to the finiteness of composition length.

## Noetherian and Artinian rings

We say that $A$ is a __Noetherian ring__ (resp. __Artinian ring__) if it is Noetherian (resp. Artinian) as an $A$-module; equivalently, if its set of ideals satisfies a.c.c. (resp. d.c.c.). The above results for Noetherian and Artinian modules yield the following:

__Proposition__: Let $A$ be a Noetherian (resp. Artinian) ring, and let $I\subseteq A$ be an ideal. Then $A/I$ is also Noetherian (resp. Artinian).

__Proof__: We proved that $A/I$ is a Noetherian (resp. Artinian) $A$-module. Now note that the $A$-submodules of $A/I$ are precisely the $A/I$-submodules, namely the ideals of $A/I$. $\qed$

Hence the Noetherian and Artinian properties carry over to quotient rings, but _not_ subrings in general (since subrings of $A$ are _not_ $A$-modules).

__Proposition__: Let $A$ be a Noetherian (resp. Artinian) ring. Then any finite $A$-module is also Noetherian (resp. Artinian).

__Proof__: First we induct on $n$ to show that the free module $A^n$ is Noetherian (resp. Artinian). This is given for $n=1$. If this is true for $n$, then the $A$-modules $A^n$ and $A^{n+1}/A^n\cong A$ are Noetherian (resp. Artinian), hence by the previous result, so is $A^{n+1}$.

Now any finite $A$-module is a quotient of some free module $A^n$, and hence is also Noetherian (resp. Artinian). $\qed$

__Corollary__: If $A$ is a Noetherian (resp. Artinian) ring and $B\supseteq A$ is a ring which is finitely generated as an $A$-module, then $B$ is also a Noetherian (resp. Artinian) ring.

__Proof__: By the previous proposition, $B$ is a Noetherian (resp. Artinian) $A$-module. Since every $B$-submodule of $B$ is also an $A$-submodule, $B$ is also a Noetherian (resp. Artinian) $B$-module. $\qed$

A warning to the reader: note that, for instance, $A[X]$ is _not_ finitely generated _as an $A$-module_, even though it is finitely generated _as an $A$-algebra_ (by $X$). For Noetherian rings, the extension of the above result to finitely generated algebras uses the Hilbert basis theorem, which we will cover in the [next post]({% post_url 2019-02-17-commutative-algebra-vii %}).

## Artinian rings

We have seen that the Noetherian and Artinian conditions for modules are independent. However, for rings we have the following surprising result:

__Akizuki-Hopkins-Levitzki Theorem__: Any Artinian ring is Noetherian.

We proceed in several steps.

__Proposition__: Let $A$ be an Artinian ring. Then $A$ has finitely many maximal ideals.

__Proof__: Suppose otherwise; then let $\mf m_1,\mf m_2,\ldots$ be pairwise distinct maximal ideals. For any $k\geq2$, pick $x_i\in\mf m_i\backslash\mf m_k$ for $1\leq i\leq k-1$. Since $\mf m_k$ is prime, we have

$$x_1\cdots x_{k-1}\in\mf m_1\cdots\mf m_{k-1}\backslash\mf m_k.$$

Then we have the infinite descending chain of ideals

$$\mf m_1\supsetneq\mf m_1\mf m_2\supsetneq\mf m_1\mf m_2\mf m_3\supsetneq\cdots,$$

which is the desired contradiction. $\qed$

__Proposition__: Let $A$ be an Artinian ring. Then the Jacobson radical $\rad(A)$ is nilpotent.

__Proof__: Write $I=\rad(A)$, and consider the nonincreasing chain

$$I\supseteq I^2\supseteq\cdots,$$

which must be eventually constant; hence there exists $s\geq1$ with $I^s=I^{s+1}$.

Assume for sake of contradiction that $I^s\neq(0)$. Consider the family of ideals $J\subseteq A$ such that $JI^s\neq(0)$; since $II^s=I^{s+1}=I^s\neq(0)$, this family is nonempty, so it has a minimal element $J$.

Now there exists $x\in J$ such that $I^sx\neq0$, so $I^s(Ax)\neq(0)$ and $Ax\subseteq J$ implies $J=Ax$ by minimality of $J$; in particular, $J$ is finitely generated as an $A$-module.

Also, note that

$$(JI^s)I^s=JI^{2s}=JI^s\neq(0),$$

so $JI^s\subseteq J$ implies $JI^s=J$ by minimality of $J$. By Nakayama's lemma, we have $J=(0)$, so $JI^s=(0)$, which is the desired contradiction. $\qed$

__Corollary__: Let $A$ be an Artinian ring. Then every prime ideal of $A$ is maximal.

__Proof__: Let the maximal ideals of $A$ be $\mf m_1,\ldots,\mf m_r$, and let $\mf p$ be any prime ideal of $A$. Since the Jacobson radical $\rad(A)=\mf m_1\mf m_2\cdots\mf m_r$ is nilpotent, we have

$$(\mf m_1\cdots\mf m_r)^s=(0)\subseteq\mf p$$

for some $s\geq1$. Hence we must have $\mf m_k\subseteq\mf p$ for some $k$, so $\mf p=\mf m_k$. $\qed$

__Proof of Akizuki-Hopkins-Levitzki Theorem__: Let $A$ be an Artinian ring, with maximal ideals $\mf m_1,\ldots,\mf m_r$, and Jacobson radical $I=\rad(A)=\mf m_1\mf m_2\cdots\mf m_r$ satisfying $I^s=(0)$. Consider the chain of ideals

$$\begin{aligned}
A&\supseteq\mf m_1\supseteq\mf m_1\mf m_2\supseteq\cdots\supseteq I\\
&\supseteq I\mf m_1\supseteq I\mf m_1\mf m_2\supseteq\cdots\supseteq I^2\\
&\supseteq\cdots\\
&\supseteq I^s=(0).
\end{aligned}$$

For any two consecutive terms in this sequence, say $M$ and $M\mc m_i$, note that $M/M\mf m_i$ is a $(A/\mf m_i)$-vector space, whose $(A/\mf m_i)$-vector subspaces are precisely its $A$-submodules. Hence

$$\begin{aligned}
A&\text{ is an Artinian }A\text{-module}\\
\implies M&\text{ is an Artinian }A\text{-module}\\
\implies M/M\mf m_i&\text{ is an Artinian }A\text{-module}\\
\implies M/M\mf m_i&\text{ is an Artinian }(A/\mf m_i)\text{-vector space},
\end{aligned}$$

so $M/M\mf m_i$ is finite-dimensional over $A/\mf m_i$. Thus $\ell(M/M\mf m_i)<\infty$. By additivity of composition length, we get $\ell(A)<\infty$, so $A$ has a composition series implies $A$ is a Noetherian ring. $\qed$