---
title: 'Measure Theory (XII): Product Measures'
layout: post
tag: [measure theory]
date: 2018-11-20 14:26:06 +0800
---

In this post, we describe the construction of a measure on the product of two measure spaces. We also relate integration in the product measure to the double integral over each measure space, in the form of Fubini's theorem and Tonelli's theorem.

<!--more-->

## Product measures

Let $(\Omega_1,\Sigma_1,\mu_1)$ and $(\Omega_2,\Sigma_2,\mu_2)$ be measure spaces. The family of __measurable rectangles__ on $\Omega_1\times\Omega_2$ is

$$\mc R\coloneqq\{A_1\times A_2\,:\,A_1\in\Sigma_1,\,A_2\in\Sigma_2\}.$$

We now apply the Carathéodory construction on the function $\mu_0:\mc R\to[0,\infty]$ given by

$$\mu_0(A_1\times A_2)=\mu_1(A_1)\mu_2(A_2),$$

obtaining first an outer measure $\mu^* :\mc P(\Omega_1\times\Omega_2)\to[0,\infty]$ by

$$\mu^* (A)=\inf\left\{\sum_{n=1}^\infty\mu_0(R_n)\,:\,R_n\in\mc R,\,A\subseteq\bigcup_{n=1}^\infty R_n\right\},$$

then a measure $\mu:\Sigma\to[0,\infty]$ by restricting $\mu^* $ to the $\mu^* $-measurable sets

$$\begin{aligned}
\Sigma=\{A\subseteq\Omega_1\times\Omega_2\,:\,&\mu^* (A\cap S)+\mu^* (A^c\cap S)\leq\mu^* (S)\\
&\text{for all }S\subseteq\Omega_1\times\Omega_2\}.
\end{aligned}$$

The measure space $(\Omega_1\times\Omega_2,\Sigma,\mu)$ is called the __product measure space__ of $(\Omega_1,\Sigma_1,\mu_1)$ and $(\Omega_2,\Sigma_2,\mu_2)$, and $\mu$ is called the __product measure__ of $\mu_1$ and $\mu_2$. This is sometimes written as $\mu=\mu_1\times\mu_2$.

Again, since the Carathéodory construction is rather indirect, some intuitive statements require some work to prove.

__Proposition__: $\mc R\subseteq\Sigma$, ie. every measurable rectangle is $\mu$-measurable. Moreover, $\mu(R)=\mu_0(R)$ for all $R\in\mc R$.

__Proof__: It suffices to show that

$$\mu^* (S)\geq\mu^* (S\cap R)+\mu^* (S\cap R^c)$$

for all $S\subseteq\Omega_1\times\Omega_2$. 

Consider any covering $(R_k)_{k=1}^\infty$ of $S$ by measurable rectangles. Now if we write $R=A\times B$ and $R_k=A_k\times B_k$, then we can write $R_k$ as a disjoint union as follows:

$$\begin{aligned}
R_k&=(R_k\cap R)\cup(R_k\cap R^c)\\
&=(R_k\cap R)\cup(A_k\times(B_k\backslash B))\cup((A_k\backslash A)\times(B_k\cap B))\\
&=R_k'\cup R_k''\cup R_k'''
\end{aligned}$$

(this is easiest to visualise with a picture). Hence $(R_k')$ and $(R_k'')\cup(R_k''')$ are coverings of $R\cap S$ and $R^c\cap S$ by measurable rectangles, respectively.

Also, it is routine to check that $\mu_0(R_k)=\mu_0(R_k')+\mu_0(R_k'')+\mu_0(R_k''')$. Hence

$$\begin{aligned}
\sum_{k=1}^\infty\mu_0(R_k)&=\sum_{k=1}^\infty\mu_0(R_k')+\sum_{k=1}^\infty(\mu_0(R_k'')+\mu_0(R_k'''))\\
&\geq\mu^* (R\cap S)+\mu^* (R^c\cap S).
\end{aligned}$$

Now taking infimum over all $(R_k)$ gives

$$\mu^* (S)\geq\mu^* (R\cap S)+\mu^* (R^c\cap S),$$

as desired. $\qed$

{% comment %}
<!-- Lebesgue measure on $\bb R^n$ -->
{% endcomment %}

## Iterated integrals

We expect that the Lebesgue integral of a function on a product measure space should have the same value as the "iterated integral" along the coordinates. In these two sections, we will show that this principle holds with very few conditions.

For the rest of this post, let $(\Omega_1,\Sigma_1,\mu_1)$ and $(\Omega_2,\Sigma_2,\mu_2)$ be __complete__ measure spaces (ie. subsets of null sets are null), and let $(\Omega_1\times\Omega_2,\Sigma,\mu)$ be their product measure space.

We say that a function $f:\Omega_1\times\Omega_2\to[-\infty,\infty]$ __has property $(F)$__, and write $f\in(F)$, if the following hold:
- $f$ is $\mu$-integrable;
- the function $f(\omega_1,-)$ is $\mu_2$-integrable for $\mu_1$-a.e. $\omega_1\in\Omega_1$; and
{% comment %}
<!-- - the function $f(-,\omega_2)$ is $\mu_1$-integrable for $\mu_2$-a.e. $\omega_2\in\Omega_2$; -->
{% endcomment %}
- the function $f^{(1)}:\Omega_1\to(-\infty,\infty)$ defined by

  $$f^{(1)}(\omega_1)=\begin{cases}\int_{\Omega_2}\!f(\omega_1,\omega_2)\,d\mu_2,&\text{if the integral exists}\\0,&\text{otherwise}\end{cases}$$

  is $\mu_1$-integrable, and 

  $$\int_{\Omega_1\times\Omega_2}\!f\,d\mu=\int_{\Omega_1}\!f^{(1)}\,d\mu_1.$$

The last equation is usually written as

$$\int_{\Omega_1\times\Omega_2}\!f\,d\mu=\int_{\Omega_1}\!\int_{\Omega_2}\!f(\omega_1,\omega_2)\,d\mu_2\,d\mu_1.$$

Our goal will be to prove that every $\mu$-integrable function has property $(F)$. As such, we will build up functions with property $(F)$ step-by-step.

__Lemma__: Let $R\in\mc R$ be a measurable rectangle with $\mu(R)<\infty$. Then $\chi_R\in(F)$.

__Proof__: Clearly $\chi_R$ is $\mu$-integrable. If $R=A\times B$ with $A\in\Sigma_1$ and $B\in\Sigma_2$, then

$$\chi_R^{(1)}(\omega_1)=\int_{\Omega_2}\!f(\omega_1,\omega_2)\,d\mu_2=\begin{cases}\mu_2(B),&\omega_1\in A\\0,&\text{else}.\end{cases}$$

Hence

$$\int_{\Omega_1\times\Omega_2}\chi_R\,d\mu=\mu(R)=\mu_1(A)\mu_2(B)=\int_{\Omega_1}\chi_R^{(1)}\,d\mu_1,$$

so $\chi_R$ satisfies $(F)$. $\qed$

__Lemma__: If $f,g\in(F)$ and $c\in\bb R$, then $cf,\,f+g\in(F)$.

__Proof__: Clearly $cf$, $f+g$ are $\mu$-integrable. Note that $(cf)^{(1)}=cf^{(1)}$ holds on all of $\Omega_1$, and $(f+g)^{(1)}=f^{(1)}+g^{(1)}$ holds $\mu_1$-a.e. $\qed$

__Lemma__: Let $0\leq f_1\leq f_2\leq\cdots$ be a sequence of $\mu$-measurable functions, converging pointwise to $f$. If $f_n\in(F)$ for all $n$ and $\sup_n\int\\!f_n\,d\mu<\infty$, then $f\in(F)$.

__Proof__: By MCT, $f_n$ are $\mu$-integrable imply that $f$ is $\mu$-integrable.

Note that for fixed $n$, $f_n(\omega_1,-)$ is $\mu_2$-measurable for all $\omega_1$ outside some $\mu_1$-null set $S_n$. Hence $f(\omega_1,-)$ is $\mu_2$-measurable for all $\omega_1$ outside $\bigcup_nS_n$, ie. for $\mu_1$-a.e. $\omega_1$.

For these $\omega_1\not\in\bigcup_nS_n$, we have by MCT that

$$\begin{aligned}
f^{(1)}(\omega_1)&=\int_{\Omega_2}\!f(\omega_1,\omega_2)\,d\mu_2\\
&=\lim_{n\to\infty}\int_{\Omega_2}\!f_n(\omega_1,\omega_2)\,d\mu_2\\
&=\lim_{n\to\infty}f_n^{(1)}(\omega_1).
\end{aligned}$$

Since this holds $\mu_1$-a.e., we can integrate both sides and apply MCT again to get

$$\begin{aligned}
\int_{\Omega_1}\!f^{(1)}\,d\mu_1&=\int_{\Omega_1}\lim_{n\to\infty}\!f_n^{(1)}\,d\mu_1\\
&=\lim_{n\to\infty}\int_{\Omega_1}\!f_n^{(1)}\,d\mu_1\\
&=\lim_{n\to\infty}\int_{\Omega_1\times\Omega_2}f_n\,d\mu\\
&=\int_{\Omega_1\times\Omega_2}f\,d\mu,
\end{aligned}$$

as desired. $\qed$

__Lemma__: Let $f_1\geq f_2\geq\cdots\geq0$ be a sequence of $\mu$-measurable functions, converging pointwise to $f$. If $f_n\in(F)$ for all $n$, then $f\in(F)$.

__Proof__: Note that $(f_1-f_n)$ is an increasing sequence of nonnegative $\mu$-integrable functions converging to $f_1-f$, with

$$\sup_n\int_{\Omega_1\times\Omega_2}\!(f_1-f_n)\,d\mu\leq\int_{\Omega_1\times\Omega_2}\!f_1\,d\mu<\infty.$$

Hence by the previous Lemma, we have $f_1-f\in(F)$, so $f\in(F)$. $\qed$

__Lemma__: Let $(R_n)$ be a sequence of measurable rectangles, and let $F=\bigcup_nR_n$. If $\mu(F)<\infty$, then $\chi_F\in(F)$.

__Proof__: Note that every finite union of measurable rectangles can be written as a finite disjoint union of measurable rectangles. Hence if $F_N=\bigcup_{n=1}^NR_n$, then $\chi_{F_N}\in(F)$. Now $(\chi_{F_n})$ is an increasing sequence of nonnegative $\mu$-measurable functions with limit $\chi_F$, so we are done by the Lemma above. $\qed$

__Lemma__: Let $E\in\Sigma$ be $\mu$-null. Then $\chi_E\in(F)$.

__Proof__: For each $n$, there is a set $F_n$ which is the union of countably many measurable rectangles, such that $E\subseteq F_n$ and $\mu(F_n)<\frac1n$. By replacing $F_n$ with $\bigcap_{k=1}^nF_k$, we may assume that $F_1\supseteq F_2\supseteq\cdots\supseteq E$.

Let $F=\bigcap_nF_n$. By the previous Lemma, we have $\chi_{F_n}\in(F)$, so $\chi_F\in(F)$. Hence for $\mu_1$-a.e. $\omega_1$, we have <!-- $\chi_F(\omega_1,-)$ is $\mu_2$-integrable, and -->

$$\int_{\Omega_1}\!\chi_F^{(1)}\,d\mu_1=\int_{\Omega_1\times\Omega_2}\!\chi_F\,d\mu=0$$

implies that

$$\chi_F^{(1)}(\omega_1)=\int_{\Omega_2}\!\chi_F(\omega_1,\omega_2)\,d\mu_2=0$$

for $\mu_1$-a.e. $\omega_1$. Now $0\leq\chi_E(\omega_1,-)\leq\chi_F(\omega_1,-)$, so completeness of $\mu_2$ yields

$$\chi_E^{(1)}(\omega_1)=\int_{\Omega_2}\!\chi_E(\omega_1,\omega_2)\,d\mu_2=0$$

on the same set of $\omega_1$. Hence

$$\int_{\Omega_1}\!\chi_E^{(1)}\,d\mu_1=0=\int_{\Omega_1\times\Omega_2}\!\chi_E\,d\mu,$$

as desired. $\qed$

__Lemma__: Let $E\in\Sigma$ satisfy $\mu(E)<\infty$. Then $\chi_E\in(F)$.

__Proof__: For each $n$, there is a set $F_n$ which is the union of countably many measurable rectangles, such that $E\subseteq F_n$ and $\mu(F_n)<\mu(E)+\frac1n$. By replacing $F_n$ with $\bigcap_{k=1}^nF_k$, we may assume that $F_1\supseteq F_2\supseteq\cdots\supseteq E$.

Let $F=\bigcap_nF_n$. By the Lemma from previously, we have $\chi_{F_n}\in(F)$, so $\chi_F\in(F)$. Also, the set $G=F\backslash E$ is $\mu$-null, so $\chi_G\in(F)$. Thus $\chi_E=\chi_F-\chi_G\in(F)$. $\qed$

## Fubini's and Tonelli's theorems

__Fubini's Theorem__: Let $f:\Omega_1\times\Omega_2\to[-\infty,\infty]$ be $\mu$-integrable. Then $f\in(F)$.

__Proof__: First note that it is sufficient to prove the statement for $f\geq0$; for the general case, note that $f=f^+-f^-$, so $f^+,f^-\in(F)$ imply $f\in(F)$.

Take a sequence of step functions $0\leq f_1\leq f_2\leq\cdots$ converging pointwise to $f$. Then $f_n\leq f$ implies that $f_n$ is $\mu$-integrable, so

$$f_n=\sum_{k=1}^{m_n}a_{n,k}\chi_{E_{n,k}}$$

for some $a_{n,k}>0$ and $E_{n,k}\in\Sigma$ with $\mu(E_{n,k})<\infty$. By the previous Lemma, we have $f_n\in(F)$, so $f\in(F)$, and we are done. $\qed$

Of course, by swapping the roles of $\Omega_1$ and $\Omega_2$, we also get

$$\int_{\Omega_1\times\Omega_2}\!f\,d\mu=\int_{\Omega_1}\!\int_{\Omega_2}\!f(\omega_1,\omega_2)\,d\mu_2\,d\mu_1=\int_{\Omega_2}\!\int_{\Omega_1}\!f(\omega_1,\omega_2)\,d\mu_1\,d\mu_2.$$

The main problem when trying to apply Fubini's theorem is that the function needs to be known to be integrable on the _product measure_ beforehand. We show that this hypothesis can be replaced with nonnegativity of the function and __$\sigma$-finiteness__ of the measure spaces.

__Tonelli's Theorem__: Let $(\Omega_1,\Sigma_1,\mu_1)$ and $(\Omega_2,\Sigma_2,\mu_2)$ be complete measure spaces which are __$\sigma$-finite__ (ie. countable unions of sets with finite measure), and let $(\Omega_1\times\Omega_2,\Sigma,\mu)$ be their product measure space. If $f\geq0$ is a $\mu$-measurable function, then:
- the function $f(\omega_1,-)$ is $\mu_2$-measurable for $\mu_1$-a.e. $\omega_1\in\Omega_1$; and
- the function $f^{(1)}:\Omega_1\to(-\infty,\infty)$ defined by

  $$f^{(1)}(\omega_1)=\begin{cases}\int_{\Omega_2}\!f(\omega_1,\omega_2)\,d\mu_2,&\text{if the integral exists}\\0,&\text{otherwise}\end{cases}$$

  is $\mu_1$-measurable, and 

  $$\int_{\Omega_1\times\Omega_2}\!f\,d\mu=\int_{\Omega_1}\!f^{(1)}\,d\mu_1.$$

__Proof__: Take $(A_n)$ in $\Sigma_1$ such that $\mu_1(A_n)<\infty$ and $\bigcup_nA_n=\Omega_1$, and take $(B_n)$ in $\Sigma_2$ similarly. Then $R_n=A_n\times B_n\in\mc R$ satisfy $\mu(R_n)<\infty$ and $\bigcup_nR_n=\Omega_1\times\Omega_2$.

Let $f_n=\min(f,n)\chi_{R_n}$. This is bounded above by $n\chi_{R_n}$, which is $\mu$-integrable, so $f_n\in(F)$ by Fubini's theorem. In particular, the two given conditions in the theorem hold with $f$ replaced by $f_n$.

Now $0\leq f_1\leq f_2\leq\cdots$, with $(f_n)\to f$ pointwise. If $f_n(\omega_1,-)$ is $\mu_2$-measurable for all $\omega_1$ outside of a $\mu_1$-null set $S_n$, then $f(\omega_1,-)$ is $\mu_2$-measurable for all $\omega_1$ outside of the $\mu_1$-null set $\bigcup_nS_n$.

Hence $f^{(1)}=\lim_{n\to\infty}f_n^{(1)}$ $\mu_1$-a.e., so $f^{(1)}$ is $\mu_1$-measurable, and MCT gives

$$\begin{aligned}
\int_{\Omega_1}\!f^{(1)}\,d\mu_1&=\lim_{n\to\infty}\int_{\Omega_1}\!f_n^{(1)}\,d\mu_1\\
&=\lim_{n\to\infty}\int_{\Omega_1\times\Omega_2}\!f_n\,d\mu\\
&=\int_{\Omega_1\times\Omega_2}\!f\,d\mu,
\end{aligned}$$

as desired. $\qed$

For arbitrary measurable functions $f$, we may apply Tonelli's theorem to $\lvert f\rvert$ to get $\mu$-integrability, then apply Fubini's theorem. This gives the following version:

__Fubini--Tonelli Theorem__: Let $(\Omega_1,\Sigma_1,\mu_1)$ and $(\Omega_2,\Sigma_2,\mu_2)$ be complete $\sigma$-finite measure spaces, and let $(\Omega_1\times\Omega_2,\Sigma,\mu)$ be their product measure space. If $f$ is a $\mu$-measurable function such that any of the integrals

$$\int_{\Omega_1\times\Omega_2}|f|\,d\mu,\quad\int_{\Omega_1}\!\int_{\Omega_2}|f(\omega_1,\omega_2)|\,d\mu_2\,d\mu_1,\quad\int_{\Omega_2}\!\int_{\Omega_1}|f(\omega_1,\omega_2)|\,d\mu_1\,d\mu_2$$

is finite, then

$$\int_{\Omega_1\times\Omega_2}f\,d\mu=\int_{\Omega_1}\!\int_{\Omega_2}f(\omega_1,\omega_2)\,d\mu_2\,d\mu_1=\int_{\Omega_2}\!\int_{\Omega_1}f(\omega_1,\omega_2)\,d\mu_1\,d\mu_2.\ \qed$$