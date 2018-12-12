---
title: 'Measure Theory (IV): Lebesgue Integration (I)'
layout: post
tag: [measure theory]
date: 2018-10-20 20:27:57 +0800
---

Given a measure space $(\Omega,\Sigma,\mu)$, we define a new method of integration, known as __Lebesgue integration__, by extending the relation

$$\int_A\!1\,d\mu\coloneqq\int\!\chi_A\,d\mu=\mu(A)$$

for all measurable sets $A\in\Sigma$.

<!--more-->

Now the monotonicity and countable additivity of $\mu$ should correspond to monotonicity and limit properties of the Lebesgue integral, respectively. Accordingly, we should expect to be able to define the Lebesgue integral for all functions which are pointwise limits of step functions; by the final proposition in the previous post, this is precisely the class of $\Sigma$-measurable functions.

<!-- comparison with Riemann integral -->

## Nonnegative step functions

For any measure space $(\Omega,\Sigma,\mu)$, we can consider the collection of its (measurable) step functions $S(\Omega,\Sigma,\mu)$, and in particular the nonnegative step functions $S_+(\Omega,\Sigma,\mu)$. We start by defining the Lebesgue integral over $S_+(\Omega,\Sigma,\mu)$.

Let $\varphi\in S_+(\Omega,\Sigma,\mu)$. Then $\varphi(\Omega)$ is a finite set of nonnegative reals, say $\\{a_1,\ldots,a_m\\}$. We define

$$I(\varphi)=\sum_{k=1}^ma_k\mu(\varphi^{-1}(a_k)).$$

This is just a linear extension of what we want the Lebesgue integral to be for characteristic functions. $I$ will turn out to have the same value as the Lebesgue integral for general measurable functions; however, it is just an auxiliary construction en route to defining the Lebesgue integral at this point.

__Proposition__: Let $\varphi=\sum_{k=1}^nb_k\chi_{B_k}$ with $b_k\geq0$ and $B_k\in\Sigma$ pairwise disjoint. Then $\varphi\in S_+(\Omega,\Sigma,\mu)$, and

$$I(\varphi)=\sum_{k=1}^nb_k\mu(B_k).$$

__Proof__: Note that if $b_j=b_k$ for some $j\neq k$ then we can combine the two terms:

$$\begin{aligned}
b_j\chi_{B_j}+b_k\chi_{B_k}&=b_j\chi_{B_j\cup B_k},\\
b_j\mu(B_j)+b_k\mu(B_k)&=b_j\mu(B_j\cup B_k).
\end{aligned}$$

Hence by combining all such terms we may assume that $b_k$ are pairwise distinct; then $B_k=\varphi^{-1}(b_k)$, and the result follows by definition. $\qed$

__Proposition__: $I$ satisfies the following properties on $S_+(\Omega,\Sigma,\mu)$:

1. Linearity: For all $c\geq0$, we have

   $$I(c\varphi)=cI(\varphi),\qquad I(\varphi+\psi)=I(\varphi)+I(\psi).$$
2. Monotonicity: If $\varphi\geq\psi$, then $I(\varphi)\geq I(\psi)$.
3. If $\varphi=\psi$ $\mu$-a.e., then $I(\varphi)=I(\psi)$.

__Proof__: These follow from the previous proposition, plus the following observations:

(1): If $\varphi=\sum a_k\chi_{A_k}$ then $c\varphi=\sum ca_k\chi_{A_k}$.

If $\varphi=\sum_ka_k\chi_{A_k}$, $\psi=\sum_jb_j\chi_{B_j}$, set $C_{k,j}=A_k\cap B_j$. Then

$$\begin{aligned}
I(\varphi)&=\sum_{k,j}a_k\chi_{C_{k,j}},\\
I(\psi)&=\sum_{k,j}b_j\chi_{C_{k,j}},\\
I(\varphi+\psi)&=\sum_{k,j}(a_k+b_j)\chi_{C_{k,j}}.
\end{aligned}$$

(2): Write $\varphi,\psi$ as above; if $C_{k,j}\neq\emptyset$, then $\varphi\geq\psi$ on $C_{k,j}$ implies $a_k\geq b_j$.

(3): Let $\varphi(\Omega)\cup\psi(\Omega)=\\{a_1,\ldots,a_m\\}$. For each $k$, write $A_k=\varphi^{-1}(a_k)$ and $B_k=\psi^{-1}(a_k)$. Then

$$A_k\backslash(A_k\cap B_k)\subseteq\{\varphi\neq\psi\},$$

which has measure zero, so $\mu(A_k)=\mu(A_k\cap B_k)$. Similarly $\mu(B_k)=\mu(A_k\cap B_k)$, so $\mu(A_k)=\mu(B_k)$. Finish by noting

$$\begin{aligned}
I(\varphi)&=\sum_ka_k\mu(A_k)\\
&=\sum_kb_k\mu(B_k)=I(\psi).\qed
\end{aligned}$$

Using $I$, we can define new measures by "integrating against step functions," as follows:

__Proposition__: Given $\Phi\in S_+(\Omega,\Sigma,\mu)$, define

$$\nu(S)=I(\Phi\chi_S)$$

for all $S\in\Sigma$. Then $\nu$ is a measure on $(\Omega,\Sigma)$.

__Proof__: $\nu(\emptyset)=0$ is clear, and monotonicity of $\nu$ follows from monotonicity of $I$.

To prove countable additivity, write $\Phi=\sum_{k=1}^ma_k\chi_{A_k}$, and let $S_1,S_2,\ldots\in\Sigma$ be pairwise disjoint. Then

$$\begin{aligned}
\sum_{n=1}^\infty\nu(S_n)&=\sum_{n=1}^\infty I\left(\sum_{k=1}^ma_k\chi_{A_k}\chi_{S_n}\right)\\
&=\sum_{n=1}^\infty\sum_{k=1}^ma_k\mu(A_k\cap S_n)\\
&=\sum_{k=1}^m\sum_{n=1}^\infty a_k\mu(A_k\cap S_n)\\
&=\sum_{k=1}^ma_k\mu\left(\bigcup_{n=1}^\infty A_k\cap S_n\right)\\
&=\sum_{k=1}^ma_k\mu\left(A_k\cap\bigcup_{n=1}^\infty S_n\right)\\
&=\nu\left(\bigcup_{n=1}^\infty S_n\right).\ \qed
\end{aligned}$$

Now we can prove that $I$ has the following limit property:

__Lemma__: Let $\Phi\in S_+(\Omega,\Sigma,\mu)$, and let $\varphi_1\leq\varphi_2\leq\cdots$ be a sequence in $S_+(\Omega,\Sigma,\mu)$. If $\lim_{n\to\infty}\varphi_n(\omega)\geq\Phi(\omega)$ for all $\omega\in\Omega$, Then $\lim_{n\to\infty}I(\varphi_n)\geq I(\Phi)$.

<!-- If $I(h)=0$ then there is nothing to prove.

Otherwise, the set $h(\Omega)\backslash\\{0\\}$ is finite and nonempty, and hence has a minimum and maximum $0< m\leq M<\infty$. -->

__Proof__: Choose $0< c<1$. For any $\omega\in\Omega$, if $\Phi(\omega)>0$ then $\lim_n\varphi_n(\omega)\geq \Phi(\omega)>c\Phi(\omega)$ implies $\varphi_n(\omega)\geq c\Phi(\omega)$ for all sufficiently large $n$. Otherwise, $\Phi(\omega)=0$ implies $\varphi_n(\omega)\geq0=c\Phi(\omega)$ for all $n$. Hence the sets

$$S_n=\{\omega\in\Omega\,:\,\varphi_n(\omega)\geq c\Phi(\omega)\}$$

satisfy $S_1\subseteq S_2\subseteq\cdots$ and $\bigcup_nS_n=\Omega$.

Now let $\nu(S)=I(\Phi\chi_S)$ for $S\in\Sigma$. By monotonicity of $I$, we have

$$I(\varphi_n)\geq I(\varphi_n\chi_{S_n})\geq cI(\Phi\chi_{S_n})=c\nu(S_n).$$

Since $\nu$ is a measure,
taking supremum of the above gives

$$\lim_nI(\varphi_n)\geq c\sup_n\nu(S_n)=c\nu(\Omega)=cI(\Phi),$$

and we are done by taking $c\to1^-$. $\qed$

## Nonnegative measurable functions

Now for $f$ a nonnegative measurable function, define its __Lebesgue integral__ by

$$\int\!f=\int\!f\,d\mu=\int_\Omega\!f\,d\mu\coloneqq\sup I(\varphi),$$

where the supremum is taken over all $\varphi\in S_+(\Omega,\Sigma,\mu)$ with $\varphi\leq f$.

The limit property for $I$ now gives a useful limit property for $\int$:

__Lemma__: Let $f$ be a nonnegative measurable function, and $0\leq\varphi_1\leq\varphi_2\leq\cdots$ be a sequence of step functions converging to $f$. Then

$$\int\!f\,d\mu=\lim_{n\to\infty}I(\varphi_n).$$

__Proof__: On one hand, $\int\\!f\,d\mu\geq I(\varphi_n)$ for all $n$ implies $\int\\!f\,d\mu\geq\lim_{n\to\infty}I(\varphi_n)$. On the other hand, for all $\varphi\in S_+(\Omega,\Sigma,\mu)$ with $\varphi\leq f=\lim_{n\to\infty}\varphi_n$, we have by the previous lemma that

$$I(\varphi)\leq\lim_{n\to\infty}I(\varphi_n).$$

Taking supremum over all $\varphi$ gives $\int\\!f\,d\mu\leq\lim_{n\to\infty}I(\varphi_n)$, and we are done. $\qed$

Now it is easy to prove the following:

__Proposition__: The Lebesgue integral satisfies the following properties on _nonnegative_ measurable functions:

1. Linearity: For all $c\geq0$, we have

   $$\int\!cf\,d\mu=c\int\!f\,d\mu,\qquad\int\!(f+g)\,d\mu=\int\!f\,d\mu+\int\!g\,d\mu.$$
2. Monotonicity: If $f\geq g$, then $\int\\!f\,d\mu\geq\int\\!g\,d\mu$.
3. $\int\\!f\,d\mu\geq0$, with equality if and only if $f=0$ $\mu$-a.e.
4. If $f=g$ $\mu$-a.e., then $\int\\!f\,d\mu=\int\\!g\,d\mu$.
5. If $\varphi\in S_+(\Omega,\Sigma,\mu)$, then $\int\\!\varphi\,d\mu=I(\varphi)$.

__Proof__: (1): Let $(\varphi_n)$, $(\psi_n)$ be nondecreasing sequences of nonnegative step functions converging to $f,g$ respectively. Then $(c\varphi_n)$, $(\varphi_n+\psi_n)$ are nondecreasing sequences of nonnegative step functions converging to $cf,f+g$ respectively. The statement now follows from the previous lemma.

(2): Let $(\varphi_n)$, $(\psi_n)$ be as above. Then $\lim_{n\to\infty}\varphi_n=f\geq g\geq\psi_m$ for all $m$, so

$$\int\!f\,d\mu=\lim_{n\to\infty}I(\varphi_n)\geq I(\psi_m).$$

We are now done by taking $m\to\infty$.

{% comment %}
<!-- (1): The first statement follows from $\varphi\leq f\iff c\varphi\leq cf$, and $I(c\varphi)=cI(\varphi)$.

For the second statement, note that if $\varphi,\psi\in S_+(\Omega,\Sigma,\mu)$ with $\varphi\leq f$, $\psi\leq g$, then $\varphi+\psi\in S_+(\Omega,\Sigma,\mu)$ satisfies $\varphi+\psi\leq f+g$. Hence

$$\int\!(f+g)\,d\mu\geq I(\varphi+\psi)=I(\varphi)+I(\psi).$$

Taking supremum over $\varphi,\psi$ gives $\int\!(f+g)\,d\mu\geq\int\!f\,d\mu+\int\!g\,d\mu$.

On the other hand, there are nondecreasing sequences $(\varphi_n)_n$, $(\psi_n)_n$ of nonnegative step functions converging to $f$ and $g$, respectively. Then for every $\varphi\in S_+(\Omega,\Sigma,\mu)$ with $\varphi\leq f+g$, we have

$$\lim_n(\varphi_n+\psi_n)(\omega)=f(\omega)+g(\omega)\geq\varphi(\omega)$$

for all $\omega\in\Omega$, so by Lemma we get

$$\int\!f\,d\mu+\int\!g\,d\mu\geq\lim_nI(\varphi_n+\psi_n)\geq I(\varphi).$$

Taking supremum over $\varphi$ gives $\int\!(f+g)\,d\mu\leq\int\!f\,d\mu+\int\!g\,d\mu$, and we are done.

(2): Since $f-g\geq0$, we have by linearity and (3):

$$\int\!f\,d\mu=\int\!g\,d\mu+\int\!(f-g)\,d\mu\geq\int\!g\,d\mu.$$

(5): $f\leq f$ implies $\int\!f\,d\mu\geq I(f)$. Conversely, for any $g\in S_+(\Omega,\Sigma,\mu)$ with $g\leq f$, we have $I(g)\leq I(f)$, so taking supremum over all such $g$ gives $\int\!f\,d\mu\leq I(f)$. Hence $\int\!f\,d\mu=I(f)$. $\qed$ -->
{% endcomment %}

(3): Since $0$ is a step function satisfying $0\leq f$, we have $\int\\!f\,d\mu\geq I(0)=0$.

If $f=0$ $\mu$-a.e., and $g\in S_+(\Omega,\Sigma,\mu)$ satisfies $g\leq f$, then $g=0$ on $f^{-1}(0)$, ie. $g=0$ $\mu$-a.e. Hence $I(g)=I(0)=0$ for all such $g$, so $\int\\!f\,d\mu=0$.

If $f$ is not $0$ $\mu$-a.e., consider $S_n=f^{-1}[\frac1n,\infty]$. Then $(S_n)$ is an increasing sequence whose union is $f^{-1}(0,\infty]$, which has nonzero measure; hence some $S_n$ has nonzero measure. Then $g=\frac1n\chi_{S_n}\in S_+(\Omega,\Sigma,\mu)$ satisfies $g\leq f$, so

$$\int\!f\,d\mu\geq I(g)=\frac{\mu(S_n)}n>0.$$

(4): Let $h=\min(f,g)$; then $\\{f\neq h\\}\subseteq\\{f\neq g\\}$ has measure zero, so $f-h$ is a nonnegative measurable function which is zero $\mu$-a.e. Thus $\int\\!(f-h)\,d\mu=0$, and similarly if we replace $f$ by $g$. Thus

$$\begin{aligned}
\int\!f\,d\mu&=\int\!h\,d\mu+\int\!(f-h)\,d\mu\\
&=\int\!h\,d\mu+\int\!(g-h)\,d\mu=\int\!g\,d\mu.
\end{aligned}$$

(5): Note that $(\varphi)$ is a nondecreasing sequence of nonnegative step functions converging to $\varphi$, so

$$\int\!\varphi\,d\mu=\lim_{n\to\infty}I(\varphi)=I(\varphi).\qed$$