---
title: 'Commutative Algebra (VII): Noetherian Rings'
layout: post
date: 2019-02-17 19:59:53 +0800
tag: [commutative algebra]
macros: >-
  "\\rad":"\\operatorname{rad}",
  "\\ann":"\\operatorname{ann}",
---

Even though the definitions of the [Noetherian and Artinian properties]({% post_url 2019-02-14-commutative-algebra-vi %}) are dual to each other, it turns out that the Noetherian condition is more important. For instance, we have already seen that every Artinian ring is Noetherian. In this post, we will prove more properties of Noetherian modules and rings.

<!--more-->

## Noetherian modules

We can characterise Noetherian modules by yet another finiteness property.

__Proposition__: An $A$-module $M$ is Noetherian if and only if every submodule of $M$ is finite (ie. finitely generated).

__Proof__: ($\Rightarrow$) For any submodule $M'\subseteq M$, let $S$ be the collection of all finite submodules of $M'$. Note that $S$ is nonempty since $\\{0\\}\in S$; hence $S$ has a maximal element $N$.

If there exists $x\in M'\backslash N$, then $N+Ax$ is a finite submodule of $M'$ that strictly contains $N$, contradicting maximality of $N$. Hence $N=M'$, so $M'$ is finite.

($\Leftarrow$) Let $N_1\subsetneq N_2\subsetneq\cdots$ be an ascending chain of submodules of $M$. Then $N\coloneqq\bigcup_kN_k$ is also a submodule of $M$, so $N$ is finite by assumption, say

$$N=An_1+An_2+\cdots+An_r.$$

Now each $n_i$ is contained in some $N_{k_i}$. Taking $K=\max_i(k_i)$, we see that $N_K$ contains all the $n_i$, so $N_K=N$, and the ascending chain must stop at that point. $\qed$

__Corollary__: A ring $A$ is Noetherian if and only if every ideal of $A$ is finitely generated. $\qed$

## Hilbert basis theorem

In this section, we show that if $A$ is a Noetherian ring, then so are $A[X]$ and $A⟦X⟧$, even though they are not finitely generated as $A$-modules.

__Hilbert Basis Theorem__: Let $A$ be a Noetherian ring. Then the polynomial ring $A[X]$ is also Noetherian.

__Proof__: We will show that any ideal $I\subseteq A[X]$ is finitely generated. Consider the set of all leading coefficients of polynomials in $I$; we check that these form an ideal $J\subseteq A$. Since $A$ is Noetherian, $J$ is finitely generated, say $J=Aa_1+\cdots+Aa_n$. For each $i$, choose $f_i\in A[X]$ with leading coefficient $a_i$, and let $r$ be the maximal degree among all $f_i$.

Write $I'=A[X]f_1+\cdots+A[X]f_n$. Now for any $f=aX^m+\cdots\in I$ with $m\geq r$, note that $a\in J$ implies that $a$ is an $A$-linear combination of the $a_i$. Hence by multiplying each $f_i$ by a suitable power of $X$, we see that there is a polynomial $aX^m+\cdots\in I'$. Thus we can repeatedly subtract $f$ by elements of $I'$ to obtain a polynomial of smaller degree, so we can write

$$f=g+h,\qquad\begin{gathered}\deg g< m,\\h\in I'.\end{gathered}$$

Writing $M=A+AX+\cdots+AX^{m-1}$, the above statement implies

$$I=(I\cap M)+I'.$$

But $M$ is a finitely generated, hence Noetherian, $A$-module; thus $I\cap M$ is a finitely generated $A$-module. Hence the union of $\\{f_1,\ldots,f_n\\}$ and a finite generating set for $I\cap M$ forms a finite generating set for $I$, and we are done. $\qed$

__Corollary__: If $A$ is a Noetherian ring, then so is $A[X_1,\ldots,X_n]$.

__Proof__: Induction on $n$ using $A[X_1,\ldots,X_n]\cong A[X_1,\ldots,X_{n-1}][X_n]$. $\qed$

__Corollary__: If $A$ is a Noetherian ring and $B\supseteq A$ is a finitely generated $A$-algebra, then $B$ is also Noetherian.

__Proof__: Note that $B$ is isomorphic to a quotient of some polynomial ring $A[X_1,\ldots,X_n]$. $\qed$

In particular, every finitely generated ring (ie. finitely generated $\bb Z$-algebra) is Noetherian; so is every finitely generated algebra over a field.

__Theorem__: Let $A$ be a Noetherian ring. Then the ring of formal power series $A⟦X⟧$ is also Noetherian.

__Proof__: The proof is analogous to that for the Hilbert basis theorem, but with "degree" replaced with "_minimal_ exponent of $X$ among terms with nonzero coefficient," and "leading coefficient" replaced by "coefficient of the term with _lowest_ degree." $\qed$

## Eakin-Nagata theorem

In this section, we look at when the existence of a sufficiently "nice" module implies that the base ring is Noetherian; in particular, when a subring of a Noetherian ring is Noetherian. 

We know that a finite module over a Noetherian ring is a Noetherian module. The following result is a partial converse: a ring with a faithful Noetherian module is a Noetherian ring.

__Proposition__: Let $A$ be a ring, and let $M$ be a Noetherian $A$-module. Then $A/\ann(M)$ is a Noetherian ring.

__Proof__: Write $\overline A=A/\ann(M)$. Then the $A$-submodules of $M$ are exactly the $\overline A$-submodules of $M$, so $M$ is also a Noetherian $\overline A$-module.

In particular, $M$ is a finite $\overline A$-module, say $M=\overline A\omega_1+\cdots+\overline A\omega_n$. Now the map

$$a\mapsto(a\omega_1,\ldots,a\omega_n)$$

is a $\overline A$-module map from $\overline A$ to $M^n$, which is injective since $\ann_{\overline A}(M)=0$; hence $\overline A$ is isomorphic to an $\overline A$-submodule of $M^n$. But $M$ is a Noetherian $\overline A$-module, hence so is $M^n$, thus so is $\overline A$. $\qed$

__Theorem__: (Formanek) Let $A$ be a ring, and let $B$ be a finite $A$-module which is faithful (ie. $\ann(B)=0$). Suppose that the collection of submodules of $B$ given by

$$\{IB\,:\,I\subseteq A\text{ ideal}\}$$

satisfies the a.c.c.; then $A$ is a Noetherian ring.

__Proof__: By the previous result, it suffices to show that $B$ is a Noetherian $A$-module.

Assume otherwise for sake of contradiction; consider the collection

$$\left\{IB\,:\,\begin{gathered}I\subseteq A\text{ ideal},\\B/IB\text{ not Noetherian as }A\text{-module}\end{gathered}\right\}.$$

This collection is nonempty (since it contains $\\{0\\}$), so it has some maximal element $I_0B$. Replacing $B\to B/I_0B$ and $A\to A/\ann(B/I_0B)$, we may assume that $B$ is not Noetherian as an $A$-module, but $B/IB$ is Noetherian for any nonzero ideal $I\subseteq A$.

Next, consider the family

$$\Gamma=\{N\subseteq B\text{ submodule}\,:\,B/N\text{ faithful }A\text{-module}\}.$$

Assume for sake of contradiction that for some chain $(N_i)_ {i\in I}$ in $\Gamma$, the union $N=\bigcup_{i\in I}N_i$ is not in $\Gamma$. Now $B$ is a finite $A$-module, say $B=Ab_1+\cdots+Ab_n$. Then $N\not\in\Gamma$ implies

$$\exists a\in A\backslash\{0\}\,\forall1\leq k\leq n\,[ab_k\in N].$$

But then $ab_k\in N_{i_k}$ for some $i_k\in I$; hence if $i=\max_ki_k$, then $ab_k\in N_i$ for all $k$, so $N_i\not\in\Gamma$, contradiction.

Thus every chain in $\Gamma$ has an upper bound in $\Gamma$, namely its union. Hence by Zorn's lemma, $\Gamma$ has a maximal element $N_0$. Now $B/N_0$ is a finite faithful $A$-module, so if it is also Noetherian then $A$ is a Noetherian ring, so $B$ is a Noetherian $A$-module, contradiction. Thus by replacing $B\to B/N_0$, we get a module $B$ with the following properties:
1. $B$ is not Noetherian as an $A$-module;
2. For any nonzero ideal $I\subseteq A$, we have $B/IB$ is Noetherian as an $A$-module; and
3. For any nonzero submodule $N\subseteq B$, we have $B/N$ is not faithful as an $A$-module.

Now take any nonzero submodule $N\subseteq B$. By (3), there is a nonzero element $a\in A$ with $a(B/N)=0$, ie. $aB\subseteq N$. By (2), $B/aB$ is a Noetherian $A$-module, so $N/aB$ is finitely generated. But $B$ is finitely generated, hence so is $aB$; thus $N$ is finitely generated. Hence $B$ is a Noetherian $A$-module, which is our desired contradiction. $\qed$

__Eakin-Nagata Theorem__: Let $B$ be a Noetherian ring, and let $A\subseteq B$ be a subring such that $B$ is finite over $A$. Then $A$ is also a Noetherian ring.

__Proof__: If $a\in\ann(B)$ then $a1_B=0$ implies $a=0$. Hence $B$ is a finite faithful $A$-module, and $B$ Noetherian implies that the $A$-submodules

$$\{IB\,:\,I\subseteq A\text{ ideal}\}$$

satisfies the a.c.c.. Hence $A$ is a Noetherian ring by the previous theorem. $\qed$