---
title: 'Measure Theory (V): Lebesgue Integration (II)'
layout: post
tag: [measure theory]
date: 2018-10-23 11:57:57 +0800
---

In this post, we extend the Lebesgue integral from nonnegative measurable functions to all measurable functions.

<!--more-->

## Measurable functions

Recall that the __positive part__ and __negative part__ of $f$ are defined by $f^+=\max(f,0)$, $f^-=-\min(f,0)$, with the following properties:
- $f^+,f^-\geq0$;
- $f^+-f^-=f$; and
- $f^++f^-=\lvert f\rvert$.

Then we can just define the __Lebesgue integral__ of $f$ by

$$\int\!f\,d\mu=\int\!f^+\,d\mu-\int\!f^-\,d\mu,$$

whenever RHS is defined (ie. when the two integrals are not both $\infty$). We say that $f$ is __$\mu$-integrable__, or __integrable__, if both integrals on RHS are finite.

Note that this definition agrees with the previous definition on nonnegative measurable functions, since for any $f\geq0$ we have $f^+=f$ and $f^-=0$.

For convenience, we write

$$\int_A\!f\,d\mu=\int\!f\chi_A\,d\mu$$

for any measurable set $A\in\Sigma$.

__Proposition__: The Lebesgue integral satisfies the following properties on all measurable functions:

1. Linearity: For all $c\in\bb R$, we have

   $$\int\!cf\,d\mu=c\int\!f\,d\mu,\qquad\int\!(f+g)\,d\mu=\int\!f\,d\mu+\int\!g\,d\mu.$$
2. Monotonicity: If $f\geq g$, then $\int\\!f\,d\mu\geq\int\\!g\,d\mu$.
3. $\int\\!\lvert f\rvert\,d\mu=0$ if and only if $f=0$ $\mu$-a.e.
4. If $f=g$ $\mu$-a.e., then $\int\\!f\,d\mu=\int\\!g\,d\mu$.
5. $f$ is integrable if and only if $\lvert f\rvert$ is integrable.

Note that it is possible for the Lebesgue integral to be undefined; thus, whenever we say that two integrals are equal, we mean the following: if one of the integrals is defined, then both are defined and are equal to each other.

__Proof__: (1): We have

$$\begin{aligned}
\int\!cf\,d\mu&=\int\!(cf)^+\,d\mu-\int\!(cf)^-\,d\mu\\
&=\begin{cases}\int\!cf^+\,d\mu-\int\!cf^-\,d\mu&c\geq0\\\int\!(-cf^-)\,d\mu-\int\!(-cf^+)\,d\mu&c\leq0\end{cases}\\
&=c\left(\int\!f^+\,d\mu-\int\!f^-\,d\mu\right)\\
&=c\int\!f\,d\mu.
\end{aligned}$$

To prove additivity, we essentially analyse each combination of the signs of the functions. Given measurable functions $f,g$, define

$$\begin{aligned}
S_{++}&=\{f\geq0\}\cap\{g\geq0\},\\
S_{+-}^+&=\{f\geq0\}\cap\{g<0\}\cap\{f+g\geq0\},\\
S_{+-}^-&=\{f\geq0\}\cap\{g<0\}\cap\{f+g<0\},
\end{aligned}$$

and similarly $S_{-+}^+,S_{-+}^-,S_{- -}$: the subscripts indicate the signs of $f,g$, and the superscripts indicate the sign of $f+g$. Then

$$\begin{aligned}
\int\!(f+g)\,d\mu&=\int\!(f+g)^+\,d\mu-\int\!(f+g)^-\,d\mu\\
&=\int_{S_{++}\cup S_{+-}^+\cup S_{-+}^+}\hspace{-4em}(f+g)\,d\mu-\int_{S_{--}\cup S_{+-}^-\cup S_{-+}^-}\hspace{-4em}{-(f+g)}\,d\mu.
\end{aligned}$$

Now note that

$$\begin{aligned}
\int_{S_{++}}\!(f+g)\,d\mu&=\int_{S_{++}}\!f^+\,d\mu+\int_{S_{++}}\!g^+\,d\mu,\\
\int_{S_{+-}^+}\!(f+g)\,d\mu&=\int_{S_{+-}^+}\!f^+\,d\mu-\int_{S_{+-}^+}\!g^-\,d\mu,\\
\int_{S_{+-}^-}\!-(f+g)\,d\mu&=-\int_{S_{+-}^-}\!f^+\,d\mu+\int_{S_{+-}^-}\!g^-\,d\mu,
\end{aligned}$$

and similarly for the other three cases. Plugging these six integrals into the previous expression and collecting terms gives

$$\begin{aligned}
\int\!(f+g)\,d\mu&=\cdots\\
&=\int_{S_{++}\cup S_{+-}^+\cup S_{+-}^-}\hspace{-4em}f^+\,d\mu+\int_{S_{++}\cup S_{+-}^+\cup S_{+-}^-}\hspace{-4em}g^+\,d\mu-\int_{S_{--}\cup S_{-+}^+\cup S_{-+}^-}\hspace{-4em}f^-\,d\mu-\int_{S_{--}\cup S_{-+}^+\cup S_{-+}^-}\hspace{-4em}g^-\,d\mu\\
&=\int\!f^+\,d\mu-\int\!f^-\,d\mu+\int\!g^+\,d\mu-\int\!g^-\,d\mu\\
&=\int\!f\,d\mu+\int\!g\,d\mu.
\end{aligned}$$

(2): This follows from the fact that $f\geq g$ implies $f^+\geq g^+$ and $f^-\leq g^-$.

(3): Note that both statements are equivalent to the condition that $\lvert f\rvert=0$ $\mu$-a.e.

(4): If $f=g$ $\mu$-a.e. then $f-g=0$ $\mu$-a.e., so

$$\int\!f\,d\mu-\int\!g\,d\mu=\int\!(f-g)\,d\mu=0,$$

ie. $\int\\!f\,d\mu=\int\\!g\,d\mu$.

(5): Note that

$$\int\!\lvert f\rvert\,d\mu=\int\!f^+\,d\mu+\int\!f^-\,d\mu,$$

and LHS is finite if and only if both terms in RHS are finite. $\qed$

## Example: Counting measure

Let us work out an explicit example, when $\mu$ is the counting measure on $\Omega$, and $\Sigma=\mc P(\Omega)$. In this case, every function $f:\Omega\to\bb R$ is measurable.

For $f\geq0$, note that $f\chi_F$ is a nonnegative step function for every finite subset $F\subseteq\Omega$. Hence

$$\int\!f\,d\mu\geq I(f\chi_F)=\sum_{\omega\in F}f(\omega).$$

On the other hand, for any nonnegative step function $0\leq\varphi\leq f$, let $A=\\{\varphi>0\\}$, and note that:
- If $A$ is finite, then $\varphi\leq f\chi_A$, so

  $$I(\varphi)\leq I(f\chi_A)=\sum_{\omega\in A}f(\omega);$$
- If $A$ is infinite, then $\varphi$ attains some nonzero value infinitely often (since the image of $A$ is finite), say $\lvert\varphi^{-1}(a)\rvert=\infty$. Then

  $$I(\varphi)\geq a\mu(\varphi^{-1}(a))=\infty,$$

  so $I(\varphi)=\infty$. On the other hand, for any finite subset $B\subseteq\varphi^{-1}(a)$, we have

  $$I(f\chi_B)=a|B|,$$

  which is unbounded as we increase $\lvert B\rvert$.

In either case, we deduce that

$$\int\!f\,d\mu=\sup_F\sum_{\omega\in F}f(\omega),$$

where the supremum is taken over all finite subsets $F\subseteq\Omega$.

<!-- more explanation -->

<!-- $$\begin{aligned}
\end{aligned}$$ -->