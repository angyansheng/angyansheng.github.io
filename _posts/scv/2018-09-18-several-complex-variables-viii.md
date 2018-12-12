---
title: 'Several Complex Variables (VIII): Varieties in $\bb C^n$'
layout: post
tag: [several complex variables]
date: 2018-09-18 12:03:24 +0800
---

In this post, we introduce the notion of a _variety_, which is (locally) the common zero set of some holomorphic functions. This geometrical object will be the focus of much of our subsequent study.

<!--more-->

Let $U\subseteq\bb C^n$ be a open set. If $S$ is a set of holomorphic functions on $U$, define $V(S)$ to be their common zero set, ie.

$$V(S)=\{z\in U\,:\,f(z)=0\text{ for all }f\in S\}.$$

A __holomorphic subvariety of $U$__ is a closed subset $V\subseteq U$ which is _locally_ equal to some $V(S)$. In other words, for each $\lambda\in U$ there is a neighbourhood $W_\lambda$ of $\lambda$ and a set $S$ of holomorphic functions on $W_\lambda$ such that

$$V\cap W_\lambda=V(S).$$

We can say that $V$ is "cut out" by the functions in $S$ near $\lambda$.

Note that we may replace $\lambda\in U$ in the definition by $\lambda\in V$, since if $\lambda\not\in V$ then some neighbourhood of $\lambda$ does not intersect $V$, so $V$ is cut out near $\lambda$ by the set of functions $\\{1\\}$.

__Proposition__: A finite union (resp. finite intersection) of holomorphic subvarieties of $U$ is also a holomorphic subvariety of $U$.

__Proof__: It suffices to prove that for two subvarieties $V,\tilde V$, we have $V\cup\tilde V,V\cap\tilde V$ are also subvarieties. The general case then follows by induction.

For $\lambda\in U$, take $W_\lambda,\tilde W_\lambda$ and $S,\tilde S$ as in the definition of a subvariety. Then on $W=W_\lambda\cap\tilde W_\lambda$, we have

$$\begin{aligned}
(V\cap\tilde V)\cap W&=V(S)\cap V(\tilde S)\\
&=V(S\cap\tilde S),
\end{aligned}$$

so $V\cap\tilde V$ is a subvariety. Similarly,

$$\begin{aligned}
(V\cup\tilde V)\cap W&=(V(S)\cup V(\tilde S))\cap W\\
&=V(\{f|_W\tilde f|_W\,:\,f\in S,\,\tilde f\in\tilde S\}),
\end{aligned}$$

so $V\cup\tilde V$ is a subvariety. $\qed$

Why do we want to define subvarieties locally, instead of as the common zero set of some _globally defined_ holomorphic functions? We are anticipating the extension of this definition to complex structures other than $\bb C^n$. For example, every subvariety on $\bb C$ should also be a subvariety on the Riemann sphere $\widehat\bb C$. However, all global holomorphic functions on $\widehat\bb C$ are constant, so the only "global subvarieties" are $\emptyset$ and $\widehat\bb C$ itself!

## Germs of varieties

Another reason to define subvarieties locally is to the notion of the _germ_ of a subvariety, like we did with [the germs of holomorphic functions]({% post_url 2018-09-13-several-complex-variables-vii %}), which we can then study algebraically. Two subvarieties $V,\tilde V$ are __equivalent__ at $\lambda\in V\cap\tilde V$ if for some neighbourhood $U_\lambda$ of $\lambda$, we have $V\cap U_\lambda=W\cap U_\lambda$. The __germ of a subvariety $V$ at $\lambda\in V$__ is the equivalence class containing $V$. Now we say that $\bf V$ is the __germ of a holomorphic variety at $\lambda\in\bb C^n$__ if $\bf V$ is the germ of a subvariety $V$ of some neighbourhood of $\lambda$, where $\lambda\in V$.

Operations and relations on subvarieties carry over to germs as usual; we only elaborate on one example. Given germs of varieties $\bf V,\bf{\tilde V}$ at $\lambda$, choose a common ("actual") neighbourhood $U$ of $\lambda$ where they have representatives $V,\tilde V$; we then define the intersection $\bf V\cap\bf{\tilde V}$ as the germ of the intersection $V\cap\tilde V$. Similarly, we may define finite intersections, finite unions, and the inclusion relation between subvarieties.

There is also a natural relation between holomorphic functions $f$ and holomorphic subvarieties $V$, namely that $f$ can vanish on $V$ on a neighbourhood of $\lambda$. This notion passes to germs: we say that a germ $\bf f$ of a holomorphic function at $\lambda$ __vanishes on__ the germ $\bf V$ of a variety at $\lambda$ if there is an ("actual") neighbourhood $U$ of $\lambda$, and representatives $f,V$ in $U$, such that $f$ vanishes on $V$.

As usual, it is routine to check that the above definitions do not depend on the choice of representatives or neighbourhood.

## Ideal and locus

The interplay between germs of holomorphic functions and germs of varieties suggests natural algebraic constructions, as follows.

If $\bf V$ is the germ of a holomorphic variety at 0, define the __ideal of $\bf V$__, denoted $\operatorname{id}\bf V$, as the set of germs in ${}_n\mc H_0$ which vanish on $\bf V$. It is easily checked that this set is in fact an ideal of ${}_n\mc H_0$. Moreover, by definition, any other ideal of ${}_n\mc H_0$ whose elements all vanish on $\bf V$ must be a subset of $\operatorname{id}\bf V$.

Naively, we expect that the analogous definition works when we switch the roles of functions and varieties: if $\mc I$ is an ideal of ${}_ n\mc H_0$, we want to define the _locus_ of $\mc I$ as "the germ of a variety on which all functions of $\mc I$ vanish," or just "the intersection of the germs of all $V(\\{f\\})$ for $f\in\mc I$." The problem is that there are functions in $\mc I$ defined on _arbitrarily small_ neighbourhoods of 0, so there is no neighbourhood on which _every_ function in $\mc I$ has a representative!

The solution is to use the nontrivial result that [${}_n\mc H_0$ is a Noetherian ring]({% post_url 2018-09-13-several-complex-variables-vii %}), so any ideal $\mc I$ is generated by a finite set, say $\\{\bf g_1,\ldots,\bf g_r\\}$. Then we can pick a common neighbourhood $U$ on which these have representatives $S=\\{g_1,\ldots,g_r\\}$, and we define the __locus of $\mc I$__, denoted $\operatorname{loc}\mc I$, as the germ of $V(\\{g_1,\ldots,g_r\\})$.

__Proposition__: $\operatorname{loc}\mc I$ is indeed a germ of a variety on which every element of $\mc I$ vanishes, and it contains every germ of a variety with this property.

This last statement implies that $\operatorname{loc}\mc I$ is well-defined, independent of the choice of neighbourhood and generating set.

__Proof__: If $\bf g\in\mc I$, then it can be written as

$$\bf g=\bf f_1\bf g_1+\cdots+\bf f_r\bf g_r.$$

On some neighbourhood of 0, all the above functions have holomorphic representatives

$$g=f_1g_1+\cdots+f_rg_r.$$

By shrinking the neighbourhood, we may take a representative subvariety $V$ of $\operatorname{loc}\mc I$ such that every $g_k$ vanishes on $V$; then $g$ vanishes on $V$ also.

If $\bf W$ is a germ of a variety on which every element of $\mc I$ vanishes, it has a representative subvariety $W$ on some neighbourhood of 0. By shrinking the neighbourhood, we may take representatives $g_1,\ldots,g_r$ of the generating set of $\mc I$, which vanish on $W$. By shrinking further, we may take a representative subvariety $V$ of $\operatorname{loc}\mc I$ which is precisely the intersection of the zero sets of $g_1,\ldots,g_r$ in the neighbourhood; hence $W\subseteq V$ in this neighbourhood, so $\bf W\subseteq\operatorname{loc}\mc I$. $\qed$

Now we list some elementary properties of $\operatorname{id}$ and $\operatorname{loc}$.

__Proposition__:
1. $\bf V_1\subseteq\bf V_2\implies\operatorname{id}\bf V_1\supseteq\operatorname{id}\bf V_2$;
2. $\mc I_1\subseteq\mc I_2\implies\operatorname{loc}\mc I_1\supseteq\operatorname{loc}\mc I_2$;
3. $\bf V=\operatorname{loc}\operatorname{id}\bf V$;
4. $\mc I\subseteq\operatorname{id}\operatorname{loc}\mc I$;
5. $\operatorname{id}(\bf V_1\cup\bf V_2)=(\operatorname{id}\bf V_1)\cap(\operatorname{id}\bf V_2)\supseteq(\operatorname{id}\bf V_1)\cdot(\operatorname{id}\bf V_2)$;
6. $\operatorname{id}(\bf V_1\cap\bf V_2)\supseteq(\operatorname{id}\bf V_1)+(\operatorname{id}\bf V_2)$;
7. $\operatorname{loc}(\mc I_1\cdot\mc I_2)=\operatorname{loc}(\mc I_1\cap\mc I_2)=\operatorname{loc}(\mc I_1)\cup\operatorname{loc}(\mc I_2)$;
8. $\operatorname{loc}(\mc I_1+\mc I_2)=\operatorname{loc}(\mc I_1)\cap\operatorname{loc}(\mc I_2)$.

__Proof__: Once we choose neighbourhoods and representatives, many of these statements follow from definition and some set theory. We sketch the proofs of the more substantial statements.

(3): ($\supseteq$) Pick a representative subvariety $V$ in a neighbourhood $U$ of 0, so $V$ is the common zero set of some set of holomorphic functions on $U$. But the germs of these functions lie in $\operatorname{id}\bf V$, so $\bf V\supseteq\operatorname{loc}\operatorname{id}\bf V$ by (1).

(7): $\operatorname{loc}(\mc I_1)\cup\operatorname{loc}(\mc I_2)\subseteq\operatorname{loc}(\mc I_1\cap\mc I_2)$ is clear, and $\operatorname{loc}(\mc I_1\cap\mc I_2)\subseteq\operatorname{loc}(\mc I_1\cdot\mc I_2)$ follows from (2).

Pick finite sets of holomorphic functions $S_1,S_2$ on some neighbourhood of 0, whose germs generate $\mc I_1,\mc I_2$ respectively. Then

$$S_1\cdot S_2=\{fg\,:\,f\in S_1,\,g\in S_2\}$$

is a set of holomorphic functions whose germs generate $\mc I_1\cdot\mc I_2$. Now $V(S_1\cdot S_2)=V(S_1)\cup V(S_2)$, so $\operatorname{loc}(\mc I_1\cdot I_2)=\operatorname{loc}(\mc I_1)\cup\operatorname{loc}(\mc I_2)$.

(8): ($\supseteq$) Similar to the above, but with $V(S_1+S_2)=V(S_1)\cap V(S_2)$. $\qed$

Part (4) of the above proposition can be refined into the following (compare with Hilbert's Nullstellensatz from algebraic geometry):

__Rückert's Nullstellensatz__: If $\mc I$ is an ideal in ${}_n\mc H_0$, then

$$\operatorname{id}\operatorname{loc}\mc I=\sqrt{\mc I}\coloneqq\{\bf f\in{}_n\mc H_0\,:\,\bf f^k\in\mc I\text{ for some }k\}.\qed$$

Despite its short statement, we will not be proving the above theorem in these notes, due to its technical nature.

## Irreducible varieties

We conclude with a short example of how the algebraic constructions of $\operatorname{id}$ and $\operatorname{loc}$ can give us geometric insight into varieties.

A subvariety $V$ of an open set $U$ is said to be __reducible__ if $V=V_1\cup V_2$, where $V_1,V_2\neq V$ are proper subvarieties of $V$. Similarly, a germ $\bf V$ of a variety at 0 is __reducible__ if $\bf V=\bf V_1\cup\bf V_2$, where $\bf V_1,\bf V_2\neq\bf V$ are germs of varieties at 0 which are properly contained in $\bf V$.

__Proposition__: A germ of a variety $\bf V$ is irreducible if and only if $\operatorname{id}\bf V$ is a prime ideal.

__Proof__: ($\Leftarrow$): If $\bf V$ is reducible, say $\bf V=\bf V_1\cup\bf V_2$ with $\bf V_1,\bf V_2\neq\bf V$, then (5) from the previous proposition gives $(\operatorname{id}\bf V_1)\cdot(\operatorname{id}\bf V_2)\subseteq\operatorname{id}\bf V$, while (1) and (3) imply that $\operatorname{id}\bf V_1,\operatorname{id}\bf V_2\neq\operatorname{id}\bf V$. Hence $\operatorname{id}\bf V$ is not a prime ideal.

($\Rightarrow$): If $\operatorname{id}\bf V$ is not a prime ideal, then it contains $\mc I_1\cdot\mc I_2$ for some ideals $\mc I_1,\mc I_2$ not contained in $\operatorname{id}\bf V$. By (2), (3) and (7), $\bf V$ is contained in $\operatorname{loc}(\mc I_1\cdot\mc I_2)=\operatorname{loc}\mc I_1\cup\operatorname{loc}\mc I_2$, but is contained in neither of $\operatorname{loc}\mc I_1$ or $\operatorname{loc}\mc I_2$. Now taking $\bf V_i=\bf V\cap\operatorname{loc}\mc I_i$, we have $\bf V_i\neq\bf V$ and $\bf V=\bf V_1\cup\bf V_2$; hence $\bf V$ is reducible. $\qed$

__Proposition__: Every germ of a variety can be uniquely (up to order) decomposed into the union of finitely many irreducible germs of varieties

$$\bf V=\bf V_1\cup\cdots\cup\bf V_k,$$

where $\bf V_i\not\subseteq\bf V_j$ if $i\neq j$.

__Proof__: Suppose that $\bf V$ does not have such a decomposition. In particular, $\bf V$ is not irreducible, so we can write it as $\bf V=\bf V_1\cup\bf V_1'$. At least one of these factors, say $\bf V_1$, does not have a decomposition, and is hence reducible, say $\bf V=\bf V_2\cup\bf V_2'$. Continuing in this way, we get an infinite descending chain of germs of varieties

$$\bf V\supsetneq\bf V_1\supsetneq\bf V_2\supsetneq\cdots$$

By (2) and (3), this gives an infinite increasing sequence of ideals

$$\operatorname{id}\bf V\subsetneq\operatorname{id}\bf V_1\subsetneq\operatorname{id}\bf V_2\subsetneq\cdots,$$

contradicting the fact that ${}_n\mc H_0$ is a Noetherian ring. This proves that $\bf V$ does have a decomposition as a finite union of irreducibles. Deleting redundant terms yields the other required condition.

If $\bf V$ has two such decompositions

$$\bf V=\bf V_1\cup\cdots\cup\bf V_k=\bf V_1'\cup\cdots\cup\bf V_m',$$

then $\bf V_i=(\bf V_i\cap\bf V_1')\cup\cdots\cup(\bf V_i\cap\bf V_m')$; since $\bf V_i$ is irreducible, this means that $\bf V_i$ is contained in some $\bf V_j'$. Similarly, this $\bf V_j'$ is contained in some $\bf V_k$. Now by the non-redundancy condition we have $i=k$, so $\bf V_i=\bf V_j'$. Repeating this for all $i$ shows that the $\bf V_j'$ are equal to the $\bf V_i$ up to reordering. $\qed$