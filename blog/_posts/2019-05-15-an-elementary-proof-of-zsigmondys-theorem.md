---
title: >-
  An Elementary Proof of Zsigmondy's Theorem
layout: post
date: 2019-05-15 23:45:50 +0800
tags: [elementary number theory, math olympiad]
---

Zsigmondy's theorem is a powerful result about the prime divisors of $a^n-b^n$, and can be used to solve a variety of math olympiad problems (see for instance [this blog post by KingSmasher3](https://artofproblemsolving.com/community/c1803h1043308_zsigmondys_theorem)). In this post, I will present an elementary proof of Zsigmondy's theorem.

<!--more-->

The core idea of the proof can be summarised as follows:

__Key Idea__: Apply the LTE lemma to the context of cyclotomic polynomials.
{: style="text-align: center;"}

All the technical results that we prove along the way will serve this single purpose.

The proof below is a cleaned-up version of [this Stack Exchange answer](https://math.stackexchange.com/a/662196). 

## Zsigmondy's theorem

__Zsigmondy's Theorem (1892)__: Let $a>b\geq1$ be coprime integers, and let $n\geq2$. Then there exists a prime divisor of $a^n-b^n$ that does not divide $a^k-b^k$ for all $1\leq k< n$, except when:
- $n=2$, and $a+b$ is a power of $2$; or
- $(a,b,n)=(2,1,6)$.

We call such a prime a __primitive prime divisor__ of $a^n-b^n$.

We shall first deal with the easy case $n=2$. If $a^2-b^2$ has no primitive prime divisors then any prime $p$ dividing $a+b$ must divide $a^2-b^2$, and thus must divide $a-b$. Then

$$\begin{aligned}
p&\mid(a+b)+(a-b)=2a,\\
p&\mid(a+b)-(a-b)=2b,
\end{aligned}$$

so $p=2$ (since $a,b$ are coprime). Hence $a+b$ is a power of $2$. Henceforth we shall assume that $n\geq3$.

## Lifting The Exponent lemma

For $p$ prime and $n\geq1$, let $v_p(n)$ denote the exponent of $p$ in the prime factorisation of $n$. The following is a well-known result within the math olympiad community, called the __Lifting The Exponent (LTE)__ lemma.

__LTE Lemma__: Let $p$ be a prime, $x,y\in\bb Z$, and $m\geq1$, such that $x\equiv y\not\equiv0\pmod p$.

1. If $p\geq3$, then

   $$v_p(x^m-y^m)=v_p(x-y)+v_p(m).$$

2. If $p=2$, then

   $$v_2(x^m-y^m)=\begin{cases}v_2(x^2-y^2)+v_2\left(\frac m2\right)&m\text{ even},\\v_2(x-y)&m\text{ odd}.\end{cases}\ \qed$$

The proof proceeds by expanding $\frac{x^m-y^m}{x-y}$, and studying the $v_p$ of each factor; you can refer to the [detailed argument here](https://cp4space.wordpress.com/2014/04/13/lifting-the-exponent/).

We want to study $v_p(a^n-b^n)$ as a function of $n$. This is zero for all $n$ if $p$ divides either $a$ or $b$ ($p$ cannot divide both since they are coprime). Otherwise, let $k\geq1$ be minimal such that $p\mid a^k-b^k$. Then $k$ is the order of $\frac ab$ in the multiplicative group $(\bb Z/p\bb Z)^\times$, so

$$p\mid a^n-b^n\iff\left(\frac ab\right)^n\equiv1\pmod p\iff k\mid n.$$

In this case, by the LTE lemma we have

$$v_p(a^n-b^n)=v_p(a^k-b^k)+v_p\left(\frac nk\right).$$

Hence the first time that $p$ divides $a^n-b^n$ (ie. when $n=k$), we have no control over what power of $p$ divides it; but after that LTE determines the exponent completely.

## Cyclotomic polynomials

For $n\geq1$, the __primitive $n$-th roots of unity__ are the $\omega\in\bb C$ such that $\omega^n=1$, and $\omega^k\neq1$ for $1\leq k< n$. More explicitly, these are given by

$$\{\exp(\frac{2\pi ik}n)\,:\,1\leq k\leq n,\,\gcd(k,n)=1\}.$$

Hence there are precisely $\varphi(n)$ many primitive $n$-th roots of unity, where $\varphi$ denotes the [Euler totient function](https://en.wikipedia.org/wiki/Euler%27s_totient_function).

The __$n$-th cyclotomic polynomial__ $\Phi_n$ is defined by

$$\Phi_n(X)\coloneqq\prod_j(X-\omega_j),$$

where the product is taken over all primitive $n$-th roots of unity $\omega_j$. Note that the $n$-th roots of unity are precisely the union of the primitive $d$-th root of unity for $d\mid n$, so

$$X^n-1=\prod_{d\mid n}\Phi_d(X).$$

__Theorem__: For $n\geq1$, $\Phi_n(X)$ has integer coefficients.

__Proof__: We proceed by induction; for $n=1$ we have $\Phi_1(X)=X-1\in\bb Z[X]$.

Suppose that $\Phi_k(X)\in\bb Z[X]$ for all $k< n$. Then

$$X^n-1=\Phi_n(X)g_n(X),$$

where $g_n(X)$ is the product of all $\Phi_d(X)$ with $d\mid n$ and $d\neq n$. Then $g_n\in\bb Z[X]$ by induction hypothesis. By performing the long division $\Phi_n(X)=\frac{X^n-1}{g_n(X)}$, we have $\Phi_n\in\bb Q[X]$. Hence by [Gauss's lemma]({% post_url 2019-02-08-algebraic-number-theory-iii %}), we have $\Phi_n\in\bb Z[X]$, as desired. $\qed$

__Proposition__: Let $p$ be a prime and $n\geq1$. Then

$$\Phi_{pn}(X)=\begin{cases}\Phi_n(X^p)&p\mid n\\\frac{\Phi_n(X^p)}{\Phi_n(X)}&p\nmid n.\end{cases}$$

__Proof__: If $p\mid n$, note that the $p$-th roots of the primitive $n$-th roots of unity are precisely the primitive $pn$-th roots of unity (eg. from the explicit formula for primitive roots of unity). Hence

$$\prod_j(X^p-\omega_j)=\prod_k(X-\rho_k),$$

where the product on LHS (resp. RHS) is over all primitive $n$-th (resp. $pn$-th) roots of unity. This gives the first statement.

If $p\nmid n$, note that the $p$-th roots of the primitive $n$-th roots of unity are precisely the union of the primitive $n$-th and $pn$-th roots of unity. A similar product to the above gives the second statement. $\qed$

__Proposition__: Let $n\geq3$ and $x\in(1,\infty)$. Then

$$(x-1)^{\varphi(n)}<\Phi_n(x)< (x+1)^{\varphi(n)}.$$

__Proof__: For any primitive $n$-th root of unity $\omega$, we have $\lvert\omega\rvert=1$, so triangle inequality gives

$$x-1\leq\lvert x-\omega\rvert\leq x+1,$$

where the left (resp. right) equality holds if and only if $\omega=1$ (resp. $\omega=-1$). Since $n\geq3$, neither equality can hold for all $\omega$. Hence taking products over all $\omega$ gives

$$(x-1)^{\varphi(n)}<\lvert\Phi_n(x)\rvert< (x+1)^{\varphi(n)}.$$

We finish by noting that $\Phi_n(x)>0$ for $x>1$ by induction on $n$, using $X^n-1=\prod_{d\mid n}\Phi_d(X)$. $\qed$

The expression $a^n-b^n$ is clearly related to the cyclotomic polynomials when $b=1$, since $a^n-1=\prod_{d\mid n}\Phi_n(a)$. For the case of general $b$, we can use the trick of _homogenisation_: define

$$\Phi_n(a,b)\coloneqq b^{\varphi(n)}\Phi_n\left(\frac ab\right).$$

Note that when expanding $\Phi_n\left(\frac ab\right)$, the denominators are powers of $b$ up to $b^{\varphi(n)}$; hence $\Phi_n(a,b)$ is an integer. Also,

$$\begin{aligned}
\prod_{d\mid n}\Phi_n(a,b)&=\prod_{d\mid n}b^{\varphi(d)}\Phi_d\left(\frac ab\right)\\
&=b^n\left[\left(\frac ab\right)^n-1\right]\\
&=a^n-b^n.
\end{aligned}$$

Furthermore, we can easily check the following analogous results:

__Proposition__: Let $p$ be a prime and $n\geq1$. Then

$$\Phi_{pn}(a,b)=\begin{cases}\Phi_n(a^p,b^p)&p\mid n\\\frac{\Phi_n(a^p,b^p)}{\Phi_n(a,b)}&p\nmid n.\end{cases}\ \qed$$

__Proposition__: Let $n\geq3$. Then

$$(a-b)^{\varphi(n)}<\Phi_n(a,b)< (a+b)^{\varphi(n)}.\ \qed$$

## LTE on cyclotomic polynomials

To execute the Key Idea, let's see what LTE says about $v_p(\Phi_n(a,b))$.

__Theorem__: Let $p\geq3$ be a prime such that $p\nmid a,b$. Let $n\geq1$, and let $k\geq1$ be minimal such that $p\mid a^k-b^k$. Then

$$v_p(\Phi_n(a,b))=\begin{cases}v_p(a^k-b^k)&n=k\\1&n=p^\beta k,\,\beta\geq1\\0&\text{else}.\end{cases}$$

__Proof__: Firstly, if $k\nmid n$ then $p\nmid a^n-b^n$ implies $p\nmid\Phi_n(a,b)$. Hence

$$\begin{aligned}
v_p(a^k-b^k)&=v_p(\Phi_k(a,b))+\sum_{d\mid k,\,d\neq k}v_p(\Phi_d(a,b))\\
&=v_p(\Phi_k(a,b)),
\end{aligned}$$

which proves the first statement. Now LTE gives

$$\begin{aligned}
v_p(a^k-b^k)+\beta&=v_p(a^{p^\beta k}-b^{p^\beta k})\\
&=\sum_{d\mid p^\beta k}v_p(\Phi_d(a,b))\\
&=\sum_{d\mid p^\beta k,\,d\mid k}v_p(\Phi_d(a,b))\\
&=v_p(a^k-b^k)+\sum_{j=1}^\beta v_p(\Phi_{p^jk}(a,b)).
\end{aligned}$$

Hence if $v_p(\Phi_{p^jk}(a,b))=1$ for all $1\leq j<\beta$ then $v_p(\Phi_{p^\beta k}(a,b))=1$ as well, and so the second statement follows by induction.

Finally, if $k\mid n$ then $n=p^\beta mk$ for some $p\nmid m$ (so $\beta=v_p(\frac nk)$). We have dealt with the case $m=1$. If $m>1$ then $\Phi_n(a,b)$ is a factor of

$$\frac{\prod_{d\mid n}\Phi_d(a,b)}{\prod_{d\mid p^\beta k}\Phi_d(a,b)}=\frac{a^n-b^n}{a^{p^\beta k}-b^{p^\beta k}}.$$

But LTE gives $v_p(a^n-b^n)=v_p(a^{p^\beta k}-b^{p^\beta k})$, so $p$ does not divide $\Phi_n(a,b)$, and we are done. $\qed$

For the case $p=2$, the slightly different form of LTE gives the following using exactly the same argument. (Note that in this case, we must have $k=1$ above.)

__Theorem__: Let $a,b$ be odd, and $n\geq1$. Then

$$v_2(\Phi_n(a,b))=\begin{cases}v_2(a-b)&n=1\\v_2(a+b)&n=2\\1&n=2^\beta,\,\beta\geq2\\0&\text{else}.\end{cases}\ \qed$$

## Proof of Zsigmondy's theorem

We are now ready to prove Zsigmondy's theorem for $a>b\geq1$ coprime integers and $n\geq3$. The plan is to use the previous results to severely restrict the possible values of $\Phi_n(a,b)$, which will almost always contradict the analytic bounds on $\Phi_n$.

Assume that $a^n-b^n$ has no primitive prime divisors. If $\Phi_n(a,b)$ has no prime factors then it is equal to $1$; otherwise let $p$ be any prime factor of $\Phi_n(a,b)$. Then $p\mid a^n-b^n$, so by assumption there exists a minimal $1\leq k< n$ such that $p\mid a^k-b^k$.

Now by the results of the previous section, $v_p(\Phi_n(a,b))\geq1$ implies $n=p^\beta k$ for some $\beta\geq1$, where $k$ is the order of $\frac ab$ in $(\bb Z/p\bb Z)^\times$. Hence $k\mid p-1$, so $k< p$. This implies that $p$ is in fact the largest prime factor of $n$ (if not, the largest prime factor of $n$ is larger than $p$ and divides $k$, contradiction).

If $p\geq3$, we immediately have $v_p(\Phi_n(a,b))=1$. Also, if $p=2$ then $n\geq3$ is a power of $2$, so $4\mid n$ implies

$$\Phi_n(a,b)=a^{n/2}+b^{n/2}\equiv2\pmod 4.$$

Thus $v_p(\Phi_n(a,b))=1$ also holds in this case. Therefore $\Phi_n(a,b)$ is either $1$ or $p$, the largest prime factor of $n$.

On the other hand, by our lower bound for $\Phi_n(a,b)$, we have

$$p\geq\Phi_n(a,b)\geq(a-b)^{\varphi(n)}\geq(a-b)^{p-1}.$$

If $a-b\geq2$, then equality can only hold if $p=2$ and $n=2$, contradicting $n\geq3$.

If $a-b=1$, write $n=p^\beta k$ as before. If $\beta\geq2$ then

$$\begin{aligned}
p\geq\Phi_n(a,b)&=\Phi_{pk}(a^{p^{\beta-1}},b^{p^{\beta-1}})\\
&\geq(a^{p^{\beta-1}}-b^{p^{\beta-1}})^{\varphi(pk)}\\
&\geq a^p-b^p\\
&=pb^{p-1}+\cdots+1,\quad(\because a=b+1)
\end{aligned}$$

contradiction. Hence $\beta=1$, so $n=pk$. Thus we have

$$\begin{aligned}
p\geq\Phi_n(a,b)&=\frac{\Phi_k(a^p,b^p)}{\Phi_k(a,b)}\\
&\geq\left(\frac{a^p-b^p}{a+b}\right)^{\varphi(k)}\\
&\geq\frac{\sum_{j=1}^b(j+1)^p-j^p}{a+b}\\
&\geq\frac{b(2^p-1)}{2b+1}\\
&\geq\frac{2^p-1}3.
\end{aligned}$$

Here, equality can only hold when $p=3$ and $b=1$ (so $a=2$). Also, since $k< p$, we have $k\in\\{1,2\\}$, so $n\in\\{3,6\\}$. It is now straightforward to check that $2^3-1^3$ has $7$ as a primitive divisor, but $2^6-1^6$ has no primitive divisors. This concludes the proof of Zsigmondy's theorem.