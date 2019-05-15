---
title: 'Algebraic Number Theory (V): Cyclotomic Fields'
layout: post
date: 2019-04-24 16:02:07 +0800
tag: [algebraic number theory]
series-order: 5
macros: >-
  "\\disc":"\\operatorname{disc}",
---

While developing any theory, it is always helpful to have explicit examples at hand. We have previously encountered the family of quadratic fields, for which it is possible to work out many of their properties (eg. generators of the number ring). In this post, we introduce the __cyclotomic fields__, which form another such family of fields where explicit computations are viable.

<!--more-->

## Cyclotomic fields

For an integer $m\geq1$, let $\omega=e^{2\pi i/m}\in\bb C$ be a primitive $m$-th root of unity. Then $\bb Q[\omega]$ is called the __$m$-th cyclotomic field__.

We have already encountered some examples of cyclotomic fields. For instance, the $m$-th cyclotomic field is $\bb Q$ for $m=1,2$, $\bb Q\left[\frac{1+\sqrt{-3}}2\right]$ for $m=3,6$, and $\bb Q[i]$ for $m=4$.

__Proposition__: Let $m\geq1$ be odd. Then the $m$-th cyclotomic field is equal to the $2m$-th cyclotomic field, ie. $\bb Q[e^{2\pi i/m}]=\bb Q[e^{2\pi i/2m}]$.

__Proof__: $\subseteq$ follows from $e^{2\pi i/m}=\left(e^{2\pi i/2m}\right)^2$, and $\supseteq$ follows from $e^{2\pi i/2m}=-\left(e^{2\pi i/m}\right)^{(m+1)/2}$. $\qed$

The above result essentially follows from the fact that $-1\in\bb Q$ is a primitive square root of unity.

Our first task is to determine the degree of the extension $[\bb Q[\omega]:\bb Q]$, which is equal to the number of conjugates of $\omega$ in $\bb C$, or the degree of the minimal polynomial of $\omega$ over $\bb Q$. Note that this minimal polynomial divides $X^m-1$, but does not divide $X^n-1$ for any $1\leq n< m$ (since $\omega^m=1$ but $\omega^n\neq1$). Hence the only possible conjugates of $\omega$ are $\omega^k$ for $k$ coprime to $m$. (Note that this immediately implies that $\bb Q[\omega]$ is Galois over $\bb Q$.) We prove the converse statement below.

__Proposition__: For any $k$ with $\gcd(k,m)=1$, we have $\omega^k$ is conjugate to $\omega$.

__Proof__: We will prove the following statement: for any $\theta=\omega^l$ with $\gcd(l,m)=1$, and any prime $p$ not dividing $m$, we have $\theta^p$ is conjugate to $\theta$. Then since conjugacy is transitive, by induction we have $\omega$ is conjugate to $\omega^k$ for any $k$ which is a product of primes not dividing $m$, ie. for any $k\geq1$ coprime to $m$, and we are done.

Let $f$ be the minimal polynomial of $\theta$ over $\bb Q$, so $X^m-1=f(X)g(X)$ for some monic $g\in\bb Q$. By [Gauss's lemma]({% post_url 2019-02-08-algebraic-number-theory-iii %}), we have $f,g\in\bb Z[X]$.

Assume for sake of contradiction that $\theta^p$ is not conjugate to $\theta$. Then $f(\theta^p)\neq0$, so $g(\theta^p)=0$. Thus $\theta$ is a root of $g(X^p)$, so $f(X)\mid g(X^p)$ in $\bb Q[X]$, and by Gauss's lemma again we have $f(X)\mid g(X^p)$ in $\bb Z[X]$.

Therefore, under the mod $p$ homomorphism $\overline\cdot:\bb Z[X]\to\bb F_p[X]$, we have $\overline f(X)\mid\overline g(X^p)=\overline g(X)^p$ in $\bb F_p[X]$. Now $\bb F_p[X]$ is a UFD, so $\overline f$ and $\overline g$ have a nontrivial common factor, say $h$.

Thus $h^2\mid\overline{fg}=X^m-1$, so $h$ divides the derivative $mX^{m-1}$. By unique factorisation, we have $h$ is a multiple of some $X^b$, $b\geq1$, but this contradicts $h\mid X^m-1$, and we are done. $\qed$

Recall that the __Euler totient function__ $\varphi:\bb Z_{>0}\to\bb Z_{>0}$ is defined by $\varphi(n)=\lvert(\bb Z/n\bb Z)^\times\rvert$; equivalently, $\varphi(n)$ is the number of integers in $\\{1,2,\ldots,n\\}$ which are coprime to $n$.

__Corollary__: $[\bb Q[\omega]:\bb Q]=\varphi(m)$.

__Proof__: By the above result, the conjugates of $\omega$ are precisely

$$\{\omega^k\,:\,1\leq k\leq m,\,\gcd(k,m)=1\},$$

which is a set with $\varphi(m)$ many elements. Hence the minimal polynomial of $\omega$ has degree $\varphi(m)$. $\qed$

__Corollary__: The Galois group of $\bb Q[\omega]$ over $\bb Q$ is isomorphic to $(\bb Z/m\bb Z)^\times$. More precisely, each $k\in(\bb Z/m\bb Z)^\times$ is mapped to the automorphism sending $\omega\mapsto\omega^k$.

__Proof__: It suffices to check that the composition law for automorphisms corresponds to multiplication mod $m$: performing $\omega\mapsto\omega^k$ then $\omega\mapsto\omega^l$ yields

$$\omega\mapsto\omega^k\mapsto(\omega^l)^k=\omega^{kl},$$

and we are done. $\qed$

<!-- By the fundamental theorem of Galois theory, the subfields of $\bb Q[\omega]$ correspond to subgroups of $(\bb Z/m\bb Z)^\times$. In particular,  -->

__Corollary__: The only roots of unity in $\bb Q[\omega]$ are the $m$-th roots of unity for $m$ even, and the $2m$-th roots of unity for $m$ odd.

__Proof__: Since the $m$-th and $2m$-th cyclotomic fields are equal for $m$ odd, it suffices to prove the claim for $m$ even. Suppose that $\bb Q[\omega]$ contains a primitive $k$-th root of unity $\theta=e^{2\pi ih/k}$, with $\gcd(h,k)=1$. Let $\gcd(k,m)=d$, so that $\gcd(k,hm)=d$. Hence there exists $a,b\in\bb Z$ with $ak+bhm=d$. Then $\bb Q[\omega]$ contains

$$\omega^a\theta^b=e^{2\pi id/km},$$

which is a primitive $cm$-th root of unity (where $c=\frac kd$). Hence $\bb Q[\omega]$ contains the $cm$-th cyclotomic field, so $\varphi(m)\geq\varphi(cm)$. By well-known properties of the Euler totient function, this implies that $c=1$, so $d=k$ divides $m$; hence $\theta$ is an $m$-th root of unity, as desired. $\qed$

__Corollary__: The $m$-th cyclotomic fields, for even $m$, are pairwise non-isomorphic.

__Proof__: Since all such fields are Galois over $\bb Q$, and any such isomorphism is an embedding in $\bb C$, it suffices to show that these fields are pairwise distinct.

Now if $\bb Q[e^{2\pi i/m}]=\bb Q[e^{2\pi i/m'}]$, then the above result implies that $e^{2\pi i/m}$ is an $m'$-th root of unity, so $m'\mid m$; similarly, we have $m\mid m'$, so $m=m'$. $\qed$

## Discriminant of an element

We want to investigate the ring of algebraic integers in cyclotomic fields. However, we first need some properties of the discriminant of $n$-tuples with a special form.

For an algebraic number $\alpha$ of degree $n$ over $\bb Q$, we will write $\disc(\alpha)$ to denote $\disc(1,\alpha,\ldots,\alpha^{n-1})$.

__Lemma__: Let $K=\bb Q[\alpha]$, and let $\alpha_1,\ldots,\alpha_n$ be the conjugates of $\alpha$ over $\bb Q$. Then

$$\disc(\alpha)=\prod_{r< s}(\alpha_r-\alpha_s)^2=(-1)^{\frac{n(n-1)}2}N^K(f'(\alpha)),$$

where $f$ is the minimal (monic irreducible) polynomial of $\alpha$ over $\bb Q$.

__Proof__: Let $\sigma_1,\ldots,\sigma_n$ be the $n$ embeddings of $K$ into $\bb C$ such that $\sigma_k(\alpha)=\alpha_k$. Then

$$\det(\sigma_i(\alpha^{j-1}))_ {i,j}=\det(\alpha_i^{j-1})_ {i,j}=\prod_{r< s}(\alpha_r-\alpha_s),$$

from the formula for [Vandemonde determinants](https://en.wikipedia.org/wiki/Vandermonde_matrix). Squaring both sides gives the first equality.

Next, note that for each $r$, we have

$$f'(\alpha_r)=\lim_{x\to\alpha_r}\frac{\prod_s(x-\alpha_s)}{x-\alpha_r}=\prod_{s\neq r}(\alpha_r-\alpha_s).$$

Now $f'\in\bb Q[X]$ implies

$$\begin{aligned}
N^K(f'(\alpha))&=\prod_r\sigma_r(f'(\alpha))\\
&=\prod_rf'(\alpha_r)\\
&=\prod_{r\neq s}(\alpha_r-\alpha_s),
\end{aligned}$$

where the last product is over all $n(n-1)$ ordered pairs $(r,s)$ with $r\neq s$. Then note that

$$\prod_{r< s}(a_r-a_s)^2=(-1)^{n(n-1)/2}\prod_{r\neq s}(a_r-a_s),$$

which yields the second equality. $\qed$

## Algebraic integers in cyclotomic fields

We now consider the ring of algebraic integers $\bb A\cap\bb Q[\omega]$ in $\bb Q[\omega]$. (Recall that $\omega=e^{2\pi i/m}$ is a primitive $m$-th root of unity.) We first observe that $\omega$ is a root of $X^m-1$, and is hence an algebraic integer. This implies $\bb Z[\omega]\subseteq\bb A\cap\bb Q[\omega]$. In this section, we show that this is in fact an equality.

__Lemma__: $\disc(\omega)$ divides $m^{\varphi(m)}$.

__Proof__: Let $f$ be the minimal polynomial for $\omega$ over $\bb Q$. As before, we have $X^m-1=f(X)g(X)$ with $f,g\in\bb Z[X]$ monic. Differentiating both sides yields

$$mX^{m-1}=f'(X)g(X)+f(X)g'(X).$$

Now multiply both sides by $X$, and substitute $X=\omega$ to get

$$m=\omega f'(\omega)g(\omega).$$

Taking norms yields

$$m^{\varphi(m)}=\pm\disc(\omega)N(\omega g(\omega)),$$

and we finish by noting that $N(\omega g(\omega))\in\bb Z$ (since $\omega$ and $g(\omega)$ are algebraic integers). $\qed$

__Lemma__: Let $m\geq3$. Then $\bb Z[1-\omega]=\bb Z[\omega]$, and $\disc(1-\omega)=\disc(\omega)$.

__Proof__: The first statement is clear. For the second statement, note that if $\alpha_i$ are the conjugates of $\omega$, then $1-\alpha_i$ are the conjugates of $1-\alpha$. Hence

$$\begin{aligned}
\disc(\omega)&=\prod_{r< s}(\alpha_r-\alpha_s)^2\\
&=\prod_{r< s}((1-\alpha_r)-(1-\alpha_s))^2\\
&=\disc(1-\omega).\ \qed
\end{aligned}$$

We will first determine the ring of integers in the $m$-th cyclotomic field $\bb Q[\omega]$ in the case where $m$ is a power of a prime.

__Lemma__: Let $p$ be a prime, and let $m=p^r$. Then

$$\prod_{1\leq k\leq m,\,p\nmid k}(1-\omega^k)=p.$$

__Proof__: Let

$$f(x)=\frac{x^{p^r}-1}{x^{p^{r-1}}-1}=1+x^{p^{r-1}}+x^{2p^{r-1}}+\cdots+x^{(p-1)p^{r-1}}.$$

Then for all $p\nmid k$, we have $\omega^k$ is a root of $X^{p^r}-1$ but not $X^{p^{r-1}}-1$. Thus all the $\omega^k$ are roots of $f$. Furthermore, we have

$$\#\{1\leq k\leq m\,:\,p\nmid k\}=\varphi(m)=p^m-p^{m-1}=\deg f,$$

so the $\omega^k$ are all the roots of $f$. Thus

$$f(X)=\prod_{1\leq k\leq m,\,p\nmid k}(X-\omega^k),$$

and the result follows by substituting $X=1$. $\qed$

__Theorem__: Let $\omega=e^{2\pi i/m}$, where $m=p^r$ for some prime $p$. Then $\bb A\cap\bb Q[\omega]=\bb Z[\omega]$.

__Proof__: We write $K=\bb Q[\omega]$, $R=\bb A\cap K$, and $n=\varphi(p^r)=[K:\bb Q]$. Also, let $d\coloneqq\disc(1-\omega)=\disc(\omega)$. Note that $d\neq0$, since

$$\{1,\omega,\ldots,\omega^{n-1}\}$$

is a basis for $K$ over $\bb Q$. Hence

$$\{1,1-\omega,\ldots,(1-\omega)^{n-1}\}$$

is also a basis of $K$ over $\bb Q$. Thus by a theorem in the [previous post]({% post_url 2019-02-10-algebraic-number-theory-iv %}), every $\alpha\in R$ can be written as

$$\alpha=\frac1d\sum_{j=0}^{n-1}m_j(1-\omega)^j,$$

where $m_j\in\bb Z$. Also, by a previous lemma, we have $d\mid m^{\varphi(m)}$, so $d$ is a power of $p$.

Assume for the sake of contradiction that $R\neq\bb Z[\omega]=\bb Z[1-\omega]$. Then there exists $\alpha\in R$ such that not all $m_j$ above are divisible by $d$. By multiplying a suitable power of $p$ to all the $m_j$, we may assume that $\frac dp\mid m_j$; by subtracting some initial terms, we see that $R$ contains an element of the form

$$\beta=\frac1p\sum_{j=j_0}^{n-1}\mu_j(1-\omega)^j$$

for some $j_0\leq n-1$, where $\mu_j\in\bb Z$ and $p\nmid\mu_{j_0}$.

Now note that

$$\begin{aligned}
p&=\prod_{1\leq k\leq m,\,p\nmid k}(1-\omega^k)\\
&=(1-\omega)^n\prod_{1\leq k\leq m,\,p\nmid k}(1+\omega+\cdots+\omega^{k-1}),
\end{aligned}$$

so $\frac p{(1-\omega)^n}\in\bb Z[\omega]$. Thus

$$\sum_{j=j_0}^{n-1}\mu_j(1-\omega)^{j-j_0-1}=\frac{\beta p}{(1-\omega)^{j_0+1}}\in R.$$

Hence $\frac{\mu_{j_0}}{1-\omega}\in R$, so

$$p=N(1-\omega)\mid N(\mu_{j_0})=\mu_{j_0}^n,$$

which is our desired contradiction. $\qed$

For the case of general $m$, we need the following corollary of the last theorem in the [previous post]({% post_url 2019-02-10-algebraic-number-theory-iv %}):

__Corollary__: Let $K,L$ be number fields, and let $R,S,T$ be the number rings of $K,L,KL$ respectively. If $[KL:\bb Q]=[K:\bb Q][L:\bb Q]$ and $\gcd(\disc R,\disc S)=1$, then $T=RS$.

We can now prove the main theorem for this section.

__Theorem__: Let $\omega=e^{2\pi i/m}$. Then $\bb A\cap\bb Q[\omega]=\bb Z[\omega]$.

__Proof__: We proceed by strong induction on $m$. We have already solved the case when $m$ is a prime power. If $m$ is not a prime power, then we can write $m=m_1m_2$ for coprime integers $m_1,m_2>1$.

Let $K=\bb Q[\omega]$, $R=\bb A\cap K$. For $k=1,2$, write $\omega_k=e^{2\pi i/m_k}$, $K_k=\bb Q[\omega_k]$, and $R_k=\bb A\cap K_k=\bb Z[\omega_k]$ by inductive hypothesis.

Let $a,b\in\bb Z$ satisfy $am_1+bm_2=\gcd(m_1,m_2)=1$. Then $\omega=\omega_1^a\omega_2^b$ implies $K\subseteq K_1K_2$ and $\bb Z[\omega]\subseteq R_1R_2$. Note that the reverse inclusions are clear, so $K=K_1K_2$ and $\bb Z[\omega]=R_1R_2$.

Hence it suffices to show that $R=R_1R_2$, so we are left to check the conditions of the previous corollary. The degree condition follows from $\varphi(m)=\varphi(m_1)\varphi(m_2)$, since $m_1,m_2$ are coprime. The discriminant condition follows since $\disc R_1$ divides a power of $m_1$, and similarly for $\disc R_2$, so $m_1,m_2$ coprime implies $\disc R_1,\disc R_2$ coprime. $\qed$