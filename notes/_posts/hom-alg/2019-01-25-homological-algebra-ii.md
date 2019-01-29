---
title: 'Homological Algebra (II): Chain Complexes'
layout: post
date: 2019-01-25 08:07:58 +0800
tag: [homological algebra, commutative algebra]
macros: >-
  "\\im":"\\operatorname{im}",
  "\\coker":"\\operatorname{coker}"
---

In this post, we look at the central objects of homological algebra, namely _chain complexes_ and their _homology_.

<!--more-->

As before, we will work in an abelian category, such as the category of $A$-modules with $A$ a commutative ring.

## Chain complexes

A __chain complex__, or simply a __complex__, is a sequence of objects and maps

$$\cdots\to K_n\xrightarrow{d_n}K_{n-1}\xrightarrow{d_{n-1}}K_{n-2}\to\cdots,$$

such that $d_{n-1}\circ d_n=0$ for every $n$. We denote this complex by $K_\bullet$. The maps $d_n$ are called the __differentials__ of the complex $K_\bullet$, and we often omit the indices to write simply $d$.

The __homology__ of the complex $K_\bullet$ is the collection of objects given by

$$H_n(K_\bullet)=\ker d_n /\im d_{n+1}.$$

__Proposition__: $K_\bullet$ is exact if and only if $H_n(K_\bullet)=0$ for all $n$. $\qed$

We can also consider the dual notion of a __cochain complex__ $K^\bullet$ with arrows reversed,

$$\cdots\to K^n\xrightarrow{d_n}K^{n+1}\to\cdots,$$

satisfying $d_{n+1}\circ d_n=0$, with __cohomology__

$$H^n(K^\bullet)=\ker(d_n)/\im(d_{n-1}).$$

We see that the difference between homology and cohomology is not in the essential content, but only an index convention. Historically, the study of chain complexes came first in algebraic topology, but today it is more convenient in many contexts to work with cochain complexes and cohomology.

Usually, the objects $K_n$ (or $K^n$) can be thought of as the collection of "function-like objects" satisfying certain properties, and the differential $d$ is a local operation. In this case, to check whether an element is in $\ker d_n$, we only need to check _locally_ everywhere; but to check whether it is in $\im d_{n+1}$, we need to find a _globally_ defined preimage. In these contexts, the (co)homology can be interpreted as an important measure of the failure of a _local-to-global property_.

For example, in the de Rham cohomology on a smooth manifold, $K^n$ represent differential forms, and the cohomology turns out to be a topological (not just smooth) invariant of the manifold.

## Morphisms of complexes

A __morphism of complexes__ $f:K_\bullet\to K'_ \bullet$ is a collection of maps $f_n:K_n\to K'_ n$, such that the diagram

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
\cdots&\ra{}&K_{n+1}&\ra{d_{n+1}}&K_n&\ra{d_n}&K_{n-1}&\ra{}&\cdots\\
&&\da{f_{n+1}}&&\da{f_n}&&\da{f_{n-1}}&&\\
\cdots&\ra{}&K'_ {n+1}&\ra{d'_ {n+1}}&K'_ n&\ra{d'_ n}&K'_ {n-1}&\ra{}&\cdots
\end{matrix}$$

commutes, ie. $d'\circ f_n=f_{n-1}\circ d$.

Now clearly $f_n(\ker d_n)\subseteq\ker d\'_ n$ and $f_n(\im d_{n+1})\subseteq\im d\'_ {n+1}$, so $f_n$ induces a map

$$f_{* n}:H_n(K_\bullet)\to H_n(K'_ \bullet),$$

which we will usually write simply as $f$.

Now we can construct a new category, in which the objects are complexes and the maps are morphisms of complexes. Then we have the following interpretation of $H_n$:

__Proposition__: $H_n(-)$ is a functor (called the __$n$-th homology functor__) from the category of complexes to the original category, where for a morphism $f$, we define $H_n(f)=f_{* n}$.

__Proof__: It is clear that $H_n(1_ {K_\bullet})=1_ {H_n(K_\bullet)}$. Now for morphisms

$$K_\bullet\xrightarrow{f}K'_ \bullet\xrightarrow{g}K''_ \bullet,$$

and any $x\in K_n$, we have

$$\begin{aligned}
H_n(g)\circ H_n(f)(x+\im d_{n+1})&=H_n(g)(f(x)+\im d'_ {n+1})\\
&=g\circ f(x)+\im d''_ {n+1}\\
&=H_n(g\circ f)(x+\im d_{n+1}),
\end{aligned}$$

and we are done. $\qed$

## Homotopic maps

Note that there are nonzero morphisms which induce the zero map in homology:

__Proposition__: For any collection of maps $h_n:K_n\to K'_ {n+1}$, define

$$\varphi_n=d'\circ h_n+h_{n-1}\circ d.$$

Then $\varphi:K_\bullet\to K'_ \bullet$ is a morphism of complexes, which induces the zero map in homology (ie. $\varphi_{* n}=0$ for all $n$).

__Proof__: To see that $\varphi$ is a morphism of complexes, it suffices to note that

$$d'\circ\varphi_n=d'\circ h_{n-1}\circ d=\varphi_{n-1}\circ d.$$

Now for any $x\in\ker d_n$, we have

$$\varphi_n(x)=d'_ {n+1}\circ h_n(x)\in\im d'_ {n+1},$$

so $\varphi_{* n}$ maps every element $x+\ker d_n\in H_n(K_\bullet)$ to $0$ in $H_n(K'_ \bullet)$. Hence $\varphi_{* n}=0$. $\qed$

We say that two morphisms of complexes $f,g:K_\bullet\to K'_ \bullet$ are __chain homotopic__, or __homotopic__, written $f\sim g$, if there is a collection of maps $h_n:K_n\to K'_ {n+1}$ such that

$$f_n-g_n=d'\circ h_n+h_{n-1}\circ d.$$

As the name suggests, this concept first appeared in the context of algebraic topology. 

__Corollary__: If two morphisms of complexes are homotopic, then they induce the same map in homology (ie. $f\sim g$ implies $f_{* n}=g_{* n}$ for all $n$). $\qed$

Two complexes $K_\bullet$, $K'_ \bullet$ are __homotopy equivalent__ if there are morphisms

$$K_\bullet\xtofrom[f']{f}K'_ \bullet$$

such that $f'\circ f\sim1_ K$ and $f\circ f'\sim 1_{K'}$.

__Corollary__: Homotopy equivalent complexes have the same homology. $\qed$

## The homology long exact sequence

We say that a sequence of complexes

$$0\to K_\bullet\xrightarrow{f}K'_ \bullet\xrightarrow{g}K''_ \bullet\to0$$

is __exact__ if for every $n$, the sequence

$$0\to K_n\xrightarrow{f_n}K'_ n\xrightarrow{g_n}K''_ n\to0$$

is exact.

The following result could be viewed as the "fundamental theorem of homological algebra." This gives us a construction of a __homology long exact sequence__, which is very useful for computing homology in specific circumstances.

__Theorem__: Let

$$0\to K_\bullet\xrightarrow{f}K'_ \bullet\xrightarrow{g}K''_ \bullet\to0$$

be a (short) exact sequence of complexes. Then we have a (long) exact sequence given by

$$\cdots\to H_{n+1}(K''_ \bullet)\xrightarrow{\delta}H_n(K_\bullet)\xrightarrow{f}H_n(K'_ \bullet)\xrightarrow{g}H_n(K''_ \bullet)\xrightarrow{\delta}H_{n-1}(K_\bullet)\to\cdots$$

__Proof__: This will follow from two applications of the [snake lemma]({% post_url 2019-01-24-homological-algebra-i %}). First we consider the following commutative diagram:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
0&\ra{}&K_n&\ra{f_n}&K'_ n&\ra{g_n}&K''_ n&\ra{}&0\\
&&\da{d_n}&&\da{d'_ n}&&\da{d''_ n}&&\\
0&\ra{}&K_{n-1}&\ra{f_{n-1}}&K'_ {n-1}&\ra{g_{n-1}}&K''_ {n-1}&\ra{}&0
\end{matrix}$$

where the rows are exact. Hence by the snake lemma, we have the exact sequences

$$0\to\ker d_n\xrightarrow{\overline{f_n}}\ker d'_ n\xrightarrow{\overline{g_n}}\ker d''_ n$$

(since $f_n$ injective implies $\overline{f_n}$ injective), and

$$\coker d_n\xrightarrow{\underline{f_{n-1}}}\coker d'_ n\xrightarrow{\underline{g_{n-1}}}\coker d''_ n\to0$$

(since $g_{n-1}$ surjective implies $\underline{g_{n-1}}$ surjective).

Now consider the diagram

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&\coker d_{n+1}&\ra{\underline{f_n}}&\coker d'_ {n+1}&\ra{\underline{g_n}}&\coker d''_ {n+1}&\ra{}&0\\
&&\da{\tilde d_n}&&\da{\tilde d'_ n}&&\da{\tilde d''_ n}&&\\
0&\ra{}&\ker d_{n-1}&\ra{\overline{f_{n-1}}}&\ker d'_ {n-1}&\ra{\overline{g_{n-1}}}&\ker d''_ {n-1}
\end{matrix}$$

Here the map $\tilde d_n$ is induced from the map $d_n:K_n\to K_{n-1}$, by noting that $\im d_n\subseteq\ker d_{n-1}$ and $\im d_{n+1}\subseteq\ker d_n$. The maps $\tilde d\'_ {n+1}$ and $\tilde d\'\'_ {n+1}$ are defined similarly.

Again by the snake lemma, we get an exact sequence

$$\ker\tilde d_n\xrightarrow{\overline{(\underline{f_n})}}\ker\tilde d'_ n\xrightarrow{\overline{(\underline{g_n})}}\ker\tilde d''_ n\xrightarrow{\delta_n}\coker\tilde d_n\xrightarrow{\underline{(\overline{f_{n-1}})}}\coker\tilde d'_ n\xrightarrow{\underline{(\overline{g_{n-1}})}}\coker\tilde d''_ n$$

Now we have

$$\begin{aligned}
\ker\tilde d_n&=\ker d_n/\im d_{n+1}=H_n(K_\bullet),\\
\coker\tilde d_n&=\ker d_{n-1}/\im\tilde d_n\\
&=\ker d_{n-1}/\im d_n=H_{n-1}(K_\bullet),
\end{aligned}$$

and similarly for $\tilde d\'_ n$ and $\tilde d\'\'_ n$. Also, it is routine to check that 

$$\begin{aligned}
\overline{(\underline{f_n})}&=f_{* n},&\underline{(\overline{f_{n-1}})}&=f_{* n-1},\\
\overline{(\underline{g_n})}&=g_{* n},&\underline{(\overline{g_{n-1}})}&=g_{* n-1}.
\end{aligned}$$

Hence we get the long exact sequence in the claim. $\qed$