---
title: 'Commutative Algebra (VIII): Spectrum of a Ring'
layout: post
date: 2019-03-08 08:08:17 +0800
tag: [commutative algebra]
macros: >-
  "\\maxSpec":"\\operatorname{maxSpec}",
  "\\Spec":"\\operatorname{Spec}",
  "\\rad":"\\operatorname{rad}",
---

We have arrived at one of the central objects of algebraic geometry, the spectrum of a ring.

<!--more-->

## Motivation: algebraic geometry

First, we cover some motivation for the definition of the spectrum from algebraic geometry. The reader may skip this introductory section and proceed straight to the <a href="#spectrum-of-a-ring">definition of the spectrum</a>.

We will get a lot of mileage out of the following philosophy:

To understand a space, study the functions on the space.
{: style="text-align: center;"}

For instance, in the context of algebraic geometry, suppose we want to study $\bb C^n$ and its algebraic subvarieties. (In this setting we usually write $\bb C^n$ as $\bb A^n$, the affine $n$-space.) Then the appropriate function space to look at is the polynomial ring $\bb C[X_1,\ldots,X_n]$. Every ideal $\mf a\subseteq\bb C[X_1,\ldots,X_n]$ defines an __affine algebraic variety__ in $\bb A^n$, which is its vanishing locus:

$$\bb V(\mf a)\coloneqq\{(x_1,\ldots,x_n)\in\bb A^n\,:\,f(x_1,\ldots,x_n)=0\text{ for all }f\in\mf a\}.$$

It can be shown that the collection of all algebraic varieties in $\bb A^n$ form the closed sets for a topology, known as the __Zariski topology__ on $\bb A^n$.

More generally, for any affine algebraic variety $V\subseteq\bb A^n$, the corresponding function space is the ring of polynomial functions on $V$, called its __coordinate ring__ and denoted $\bb C[V]$. Note that

$$\bb C[V]=\bb C[X_1,\ldots,X_n]/\bb I(V),$$

where $\bb I(V)$ is the ideal of polynomials vanishing on $V$. Again, it is possible to define the Zariski topology on $V$.

The geometry of affine algebraic varieties has a natural effect on the coordinate rings, as follows: any morphism of affine algebraic varieties $F:V\to W$ induces a __pullback map__ on the coordinate rings

$$\begin{aligned}
F^\#:\bb C[W]&\to\bb C[V],\\
g\quad&\mapsto g\circ F.
\end{aligned}$$

The most important link between $V$ and $\bb C[V]$ is given by Hilbert's Nullstellensatz, which implies that the points of $V$ correspond to maximal ideals of $\bb C[V]$, ie. elements of the __maximal spectrum__

$$\maxSpec(\bb C[V])\coloneqq\{\mf m\subseteq\bb C[V]\,:\,\mf m\text{ maximal ideal}\}.$$

Moreover, we can define the Zariski topology on $\maxSpec(\bb C[V])$ such that the correspondence is in fact a homeomorphism $V\to\maxSpec(\bb C[V])$.

The point of the above construction is this: we have recovered the _geometric_ object $V$ from _algebraic_ data in $\bb C[V]$.

The above discussion works for rings of the form $\bb C[V]$, or perhaps $k[V]$ for algebraically closed fields $k$. What if we try to extend the construction to arbitrary (commutative unital) rings? Here the philosophy is that _every ring $A$ is the "function ring" of some geometrical object_, called the __spectrum__ $\Spec(A)$.

From the discussion above, we want $\Spec(A)$ to have the following nice properties:
1. $\Spec(A)$ has a topology, defined using purely algebraic constructions from $A$;
2. Every ring homomorphism $A\to B$ induces a continuous map $\Spec(B)\to\Spec(A)$;
3. In fact, we want this to be functorial, ie. $\Spec$ is a contravariant functor from the category of (commutative unital) rings to the category of topological spaces.

We note that $\maxSpec$ actually does not work, because it fails to be functorial: this is essentially because the inverse image of a maximal ideal under a ring homomorphism might not be maximal. However, by replacing "maximal" with "prime" we circumvent this problem, and this turns out to be the right generalisation.

## Spectrum of a ring

__Note__: Since the definition of the spectrum is motivated by the specific case of coordinate rings in algebraic geometry, it will be very helpful to keep the examples $A=\bb C[X_1,\ldots,X_n]$ or $A=\bb C[V]$ in mind from this point on.

Let $A$ be a (commutative unital) ring. The __(prime) spectrum of $A$__, denoted $\Spec(A)$, is the set of all prime ideals of $A$.

The first order of business is to define a topology on $\Spec(A)$, which is well-behaved with respect to the ring structure. For each subset $E\subseteq A$, let $V(E)$ denote the set of all prime ideals which contain $E$:

$$V(E)=\{\mf p\in\Spec(A)\,:\,E\subseteq\mf p\}.$$

We record some easy consequences of the definition:
1. $V(0)=\Spec(A)$ and $V(A)=\emptyset$;
2. $V$ is inclusion-reversing: if $E_1\subseteq E_2$, then $V(E_1)\supseteq V(E_2)$;
3. If $\mf a=AE$ is the ideal generated by $E$, then $V(E)=V(\mf a)$.

Here are more properties of $V$.

__Proposition__: Let $\mf a\subseteq A$ be an ideal. Then $V(\mf a)=V(\rad(\mf a))$.

__Proof__: ($\supseteq$) Clear since $\mf a\subseteq\rad(\mf a)$.

($\subseteq$) If $\mf p\in V(\mf a)$, then $\mf a\subseteq\mf p$, so $\rad(\mf a)\subseteq\rad(\mf p)=\mf p$, ie. $\mf p\in V(\rad(\mf a))$. $\qed$

__Proposition__: Let $(E_i)_ {i\in I}$ be a family of subsets of $A$. Then

$$V\left(\bigcup_{i\in I}E_i\right)=\bigcap_{i\in I}V(E_i).$$

__Proof__: Note that

$$\begin{aligned}
\mf p\in V\left(\bigcup_{i\in I}E_i\right)&\iff E_i\subseteq\mf p\text{ for all }i\\
&\iff\mf p\in V(E_i)\text{ for all }i\\
&\iff\mf p\in\bigcap_{i\in I}V(E_i).\ \qed
\end{aligned}$$

__Proposition__: Let $\mf a,\mf b\subseteq A$ be ideals. Then

$$V(\mf a\cap\mf b)=V(\mf a\mf b)=V(\mf a)\cup V(\mf b).$$

__Proof__: $V(\mf a\cap\mf b)=V(\mf a\mf b)$: Note that $\subseteq$ is clear, since $\mf a\cap\mf b\supseteq\mf a\mf b$.

In the other direction, suppose that $\mf p\not\in V(\mf a\cap\mf b)$. Then $\mf a\cap\mf b\not\subseteq\mf p$, so there exists $x\in\mf a\cap\mf b$ with $x\not\in\mf p$. But then $x^2\in\mf a\mf b$ and $x^2\not\in\mf p$. Hence $\mf a\mf b\not\subseteq\mf p$, so $\mf p\not\in V(\mf a\mf b)$.

$V(\mf a\mf b)=V(\mf a)\cup V(\mf b)$: Note that $\supseteq$ is clear, since $\mf a\mf b\subseteq\mf a$ and $\mf a\mf b\subseteq\mf b$.

In the other direction, suppose that $\mf p\in V(\mf a\mf b)$, so $\mf a\mf b\subseteq\mf p$. By definition of a prime ideal, this implies either $\mf a\subseteq\mf p$ or $\mf b\subseteq\mf p$, so $\mf p\in V(\mf a)\cup V(\mf b)$. $\qed$

Hence we have shown that the family of sets

$$\{V(E)\,:\,E\subseteq A\}\subseteq\mc P(\Spec(A))$$

contains $\emptyset$ and $\Spec A$, and is closed under arbitrary intersection and finite union. Thus this family of sets are the closed sets for a topology on $\Spec(A)$, known as the __Zariski topology__.

__Proposition__: Let $\mf a\subseteq A$ be an ideal. Then $\Spec(A/\mf a)$ is homeomorphic to $V(\mf a)$ (as a subspace of $\Spec(A)$).

__Proof__: Note that closed sets in $V(\mf a)$ are exactly those of the form $V(\mf a)\cap V(E)=V(\mf a\cup E)=V(A(\mf a\cup E))$, ie. exactly those of the form $V(\mf b)$ for ideals $J$ with $\mf a\subseteq\mf b\subseteq A$.

Now the lattice isomorphism theorem gives a correspondence

$$\begin{aligned}
\{\text{ideals of }A/\mf a\}&\leftrightarrow\{\text{ideals of }A\text{ containing }\mf a\}\\
\underline{\mf c}\qquad&\mapsto\quad q^{-1}(\underline{\mf c})\\
q(\mf b)\quad&\gets\qquad\mf b,
\end{aligned}$$

which preserves inclusion. It is easy to check that the maps in both directions send prime ideals to prime ideals. Hence this map sends $V(\underline{\mf c})\mapsto V(q^{-1}(\underline{\mf c}))$ and $V(q(\mf b))\gets V(\mf b)$, so it is the desired homeomorphism. $\qed$

__Proposition__: Let $\mf p\in\Spec(A)$. Then $\overline{\\{\mf p\\}}=V(\mf p)$.

__Proof__: We have

$$\begin{aligned}
\overline{\{\mf p\}}&=\bigcap\{C\subseteq\Spec(A)\text{ closed}\,:\,\{\mf p\}\subseteq C\}\\
&=\bigcap\{V(E)\,:\,\mf p\in V(E)\}\\
&=V\left(\bigcup\{E\,:\,E\subseteq\mf p\}\right)\\
&=V(\mf p).\ \qed
\end{aligned}$$

__Corollary__: $\mf p$ is a closed point in $\Spec(A)$ (ie. $\\{\mf p\\}$ is closed) if and only if $\mf p$ is maximal. $\qed$


## Basic open sets

In this section, we further study the spectrum as a topological space under the Zariski topology. As such, we write $X=\Spec(A)$.

For each $f\in A$, let $X_f=X\backslash V(f)$. Note that this is a basis of open sets for the Zariski topology: any open set in $X$ is of the form $U=X\backslash V(\mf a)$ for some ideal $\mf a\subseteq A$, and

$$\begin{aligned}
\mf p\in V(\mf a)&\iff\mf a\subseteq\mf p\\
&\iff f\in\mf p\text{ for all }f\in\mf a\\
&\iff(f)\subseteq\mf p\text{ for all }f\in\mf a\\
&\iff\mf p\in\bigcap_{f\in\mf a}V(f),
\end{aligned}$$

so $U=\bigcup_{f\in\mf a}X_f$.

Here we collect some simple properties of the $X_f$:

__Proposition__: For all $f,g\in A$, we have:
1. $X_f\cap X_g=X_{fg}$;
2. $X_f=\emptyset\iff f$ is nilpotent;
3. $X_f=X\iff f$ is a unit;
4. $V(f)\subseteq V(g)\iff\rad(f)\supseteq\rad(g)$;
5. $X_f=X_g\iff\rad(f)=\rad(g)$.

__Proof__: (1) We have $fg\not\in\mf p$ if and only if $f\not\in\mf p$ and $g\not\in\mf p$.

(2) Both statements hold if and only if $f$ is in the intersection of all prime ideals of $A$, which is the nilradical of $A$.

(3) If $X_f=X$ then $f$ is not contained in any maximal ideal of $A$. Thus $(f)$ is not a proper ideal, ie. $(f)=A$, so $f$ is a unit.

Conversely, if $f$ is a unit then $(f)=A$, so $f$ is not contained in any proper ideal (hence any prime ideal) of $A$.

(4) Note that $V(f)=V(\rad(f))$ and $V(g)=V(\rad(g))$, so ($\Leftarrow$) is clear since $V$ is order-reversing, and ($\Rightarrow$) follows since $\rad(f)\in V(\rad(f))\subseteq V(\rad(g))$ implies $\rad(g)\subseteq\rad(f)$ by definition.

(5) This is clear from (4). $\qed$

Following the convention in algebraic geometry, we say that a topological space is __quasi-compact__ if every open cover has a finite subcover, and it is __compact__ if it is quasi-compact and Hausdorff.

__Proposition__: $X$ is quasi-compact.

__Proof__: Let $(U_i)_ {i\in I}$ be an open covering of $X$; without loss of generality, we may assume that the $U_i$ are basic open sets, so $U_i=X_{f_i}$ for some $f_i\in A$. Now if $\mf a$ is the ideal generated by all the $f_i$, then

$$V(\mf a)=\bigcap_{i\in I}V(f_i)=\emptyset,$$

so $\mf a$ is not contained in any maximal ideal, ie. $\mf a=A$. In particular, $1\in\mf a$ implies that there exists $i_1,\ldots,i_n\in I$ and $a_1,\ldots,a_n\in A$ such that

$$1=a_1f_{i_1}+\cdots+a_nf_{i_n},$$

so $A=Af_{i_1}+\cdots+Af_{i_n}$ implies $V(f_{i_1})\cap\cdots\cap V(f_{i_n})=\emptyset$. Hence $X_{f_1},\ldots,X_{f_n}$ form a finite subcover of $X$. $\qed$

__Corollary__: For any $f\in A$, the subspace $X_f\subseteq X$ is quasi-compact. $\qed$