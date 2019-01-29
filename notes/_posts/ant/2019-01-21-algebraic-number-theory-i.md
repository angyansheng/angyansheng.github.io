---
title: 'Algebraic Number Theory (I): First Examples'
layout: post
date: 2019-01-21 23:21:35 +0800
tag: [algebraic number theory]
---

In this post, we look at two specific examples of number rings, and investigate how their ring theoretic properties translate into number theory.

## Gaussian integers

The ring of __Gaussian integers__ is given by

$$\bb Z[i]=\{a+bi\,:\,a,b\in\bb Z\}.$$

In analogy to $\bb Z$, we can ask about factorisation in $\bb Z[i]$:
- Is $\bb Z[i]$ a PID? a UFD?
- Can we characterise irreducible elements of $\bb Z[i]$?
- In particular, if $p$ is a __rational prime__ (ie. a prime in $\bb Z$), when is it an irreducible element of $\bb Z[i]$?

Define a __norm function__ $N:\bb Z[i]\to\bb Z_{\geq0}$ by $N(a+bi)=a^2+b^2$. Then we can easily check the following:

__Proposition__: $N(\alpha)=\alpha\overline\alpha=\lvert\alpha\rvert^2$. $\qed$

It is good practice to keep track of where the equalities are supposed to hold over. The first equality above holds in $\bb Z[i]$, and the second holds in $\bb C$.

__Corollary__: $N(\alpha\beta)=N(\alpha)N(\beta)$. $\qed$

In other words, the norm function is multiplicative.

__Corollary__: If $\alpha\mid\beta$ in $\bb Z[i]$, then $N(\alpha)\mid N(\beta)$ in $\bb Z$. $\qed$

__Proposition__: $u\in\bb Z[i]$ is a unit if and only if $N(u)=1$.

__Proof__: ($\Rightarrow$) Note that $N(u)N(u^{-1})=N(1)=1$ implies $N(u)=1$.

($\Leftarrow$) $N(u)=u\overline u=1$, so $u$ is a unit. $\qed$

__Corollary__: The units of $\bb Z[i]$ are $\pm1$ and $\pm i$. $\qed$

The norm function gives us a criterion for detecting irreducible elements of $\bb Z[i]$:

__Proposition__: Let $\alpha\in\bb Z[i]$.
1. If $N(\alpha)=p$ for some rational prime $p$, then $\alpha$ is irreducible.
2. If $N(\alpha)=p^2$ for some rational prime $p\equiv3\pmod4$, then $\alpha$ is irreducible.

__Proof__: (1) If $\alpha=\beta\gamma$, then $N(\alpha)=N(\beta)N(\gamma)=p$ implies either $N(\beta)=1$ or $N(\gamma)=1$, so either $\beta$ or $\gamma$ is a unit.

(2) If $\alpha=\beta\gamma$, then $N(\alpha)=N(\beta)N(\gamma)=p^2$. Now $N(\beta)$ is a sum of two squares, and thus cannot be $\equiv3\pmod4$; in particular, $N(\beta)\neq p$. Finish as in the previous case. $\qed$

{% comment %}
<!-- __Proposition__: Every nonzero, non-unit $\alpha\in\bb Z[i]$ can be factorised as a product of irreducible elements.

__Proof__: We induct on $N(\alpha)$. If $N(\alpha)=1$ then $\alpha$ is a unit, and the statement is vacuous. 

Suppose the statement holds for all Gaussian integers with norm less than $N(\alpha)$. If $\alpha$ is irreducible then there is nothing to prove. Otherwise, write $\alpha=\beta\gamma$, where $\beta,\gamma$ are non-units. Then $N(\beta),N(\gamma)\neq1$ implies $N(\beta),N(\gamma)<N(\alpha)$, so $\beta,\gamma$ are both products of irreducible elements by induction hypothesis; hence so is $\alpha$. $\qed$ -->
{% endcomment %}

__Theorem__: $\bb Z[i]$ is a PID.

__Proof__: For any nonzero ideal $I\subseteq\bb Z[i]$, take a nonzero element $\alpha\in I$ with minimal norm; this is possible since $\bb Z_{\geq0}$ is well-ordered.

We claim that $I=(a)$. To see this, take any $\beta\in I$, and let $z=\frac\beta\alpha\in\bb C$. Now take $m,n\in\bb Z$ with $\lvert\Re z-m\rvert\leq\frac12$, $\lvert\Im z-n\rvert\leq\frac12$. Then

$$|z-(m+ni)|^2\leq\left(\frac12\right)^2+\left(\frac12\right)^2=\frac12<1,$$

so multiplying by $\lvert\alpha\rvert^2$ gives

$$N(\beta-(m+ni)\alpha)=|\beta-(m+ni)\alpha|^2<|\alpha|^2=N(\alpha).$$

But $\beta-(m+ni)\alpha\in I$, so by minimality of $\alpha$ we have $\beta=(m+ni)\alpha\in(\alpha)$, as desired. $\qed$

__Corollary__: $\bb Z[i]$ is a UFD.

__Proof__: This is a [basic result in ring theory]({% post_url 2018-12-31-a-refresher-in-commutative-rings %}). $\qed$

## The irreducible elements of $\bb Z[i]$

Using unique factorisation, we can now deduce the complete list of irreducibles in $\bb Z[i]$.

__Lemma__: Let $p$ be a rational prime. Then $\bb F_p^\times$, the multiplicative group of integers mod $p$, is cyclic. $\qed$

We note that the above fact holds in general for any finite field. 

{% comment %}
<!-- __Proof__: First, note that $\sum_{d\mid n}\varphi(d)=n$ for any $n\geq1$: among the $n$ fractions $\frac1n,\frac2n,\ldots,\frac nn$, after reducing to lowest terms, exactly $\varphi(d)$ of them have denominator $d$ for any $d\mid n$.

Now for any $d\mid p-1$, suppose that there is an element $a\in\bb F_p^\times$ of multiplicative order $d$. Then the polynomial $X^d-1$ in $\bb F_p$ has roots $1,a,a^2,\ldots,a^{d-1}$, of which $\varphi(d)$ of them have order $d$. Hence the number of elements in $\bb F_p^\times$ of order $d$ is either $0$ or $\varphi(d)$. But

$$\lvert\bb F_p^\times\rvert=p-1=\sum_{d\mid p-1}\varphi(d),$$

so for each $d\mid p-1$ there must be exactly $\varphi(d)$ elements of order $d$. In particular, there are $\varphi(p-1)>0$ elements of order $p-1$; any one of these elements generates $\bb F_p^\times$, so $\bb F_p^\times$ is cyclic. $\qed$ -->
{% endcomment %}

__Proposition__: Let $p\equiv1\pmod4$ be a rational prime. Then $p=\alpha\overline\alpha$ for some irreducible $\alpha\in\bb Z[i]$.

__Proof__: Let $g$ be a generator of $\bb F_p^\times$. Then $g^{(p-1)/2}\neq1$ is an element of $\bb F_p^\times$ whose square is $1$, so $g^{(p-1)/2}=-1$. Hence for any integer $n\equiv g^{(p-1)/4}\pmod p$, we have $n^2\equiv-1\pmod p$. Hence

$$p\mid n^2+1=(n+i)(n-i).$$

But it is easy to check that $p$ divides a Gaussian integer if and only if $p$ divides both its real and imaginary parts, so $p\nmid n\pm i$. Hence $p$ is not prime in $\bb Z[i]$, thus not irreducible, so we can write $p=\alpha\beta$ for some non-units $\alpha,\beta\in\bb Z[i]$. Then

$$N(\alpha)N(\beta)=N(p)=p^2,$$

so $N(\alpha)=N(\beta)=p$. Thus $\alpha$ is irreducible, and $N(\alpha)=\alpha\overline\alpha=p$. $\qed$

__Theorem__: Up to associates, the list of all irreducible elements of $\bb Z[i]$ are:
1. $1+i$;
2. $a+bi$, where $a^2+b^2=p$ and $p\equiv1\pmod4$ is a rational prime; and
3. $p\equiv3\pmod4$ a rational prime.

__Proof__: Let $\alpha\in\bb Z[i]$ be irreducible, hence prime. Then $(\alpha)$ is a prime ideal in $\bb Z[i]$, so it is easy to check that $(\alpha)\cap\bb Z$ is a prime ideal in $\bb Z$. Thus $p\in(\alpha)$ for some rational prime $p$. Hence $\alpha\beta=p$ for some $\beta\in\bb Z[i]$. Taking norms on both sides, we get $N(\alpha)=p$ or $p^2$ (since $\alpha$ is not a unit).

_Case 1_: $N(\alpha)=p$. For $p=2$ we get $\alpha=\pm1\pm i$, all of which are conjugate to $1+i$, so it is of type (1). For $p\equiv1\pmod4$, we get $\alpha$ is of type (2). For $p\equiv3\pmod4$, this case does not occur.

_Case 2_: $N(\alpha)=p^2$. Then $\beta$ is a unit in $\bb Z[i]$. For $p\equiv3\pmod4$ this is irreducible in $\bb Z[i]$, so $\alpha$ is of type (3). Now for $p=2$ we have $2=-i(1+i)^2$, and for $p\equiv1\pmod4$ we have $p=\gamma\overline\gamma$ for some $\gamma\in\bb Z[i]$ of norm $p$. So $p$ (and hence $\alpha$) is not irreducible in $\bb Z[i]$, contradiction. $\qed$

## Applications

We now list some number theoretic consequences of the theory of factorisation in the ring of Gaussian integers. Note that both of these problems can be stated and solved in terms of elementary number theory over $\bb Z$, but they admit much cleaner proofs when we use unique factorisation over $\bb Z[i]$.

__Proposition__: Any rational prime $p\equiv1\pmod4$ is the sum of two squares.

__Proof__: Take any irreducible $a+bi\in\bb Z[i]$ of norm $p$; then $p=N(a+bi)=a^2+b^2$. $\qed$

Next, we derive a parametrisation for the primitive Pythagorean triplets.

__Proposition__: Suppose that $x,y,z\geq1$ are integers with no common factors, and

$$x^2+y^2=z^2.$$

Then there exists coprime integers $m,n\geq1$ such that

$$\{x,y\}=\{\pm(m^2-n^2),\pm2mn\},\quad z=\pm(m^2+n^2).$$

__Proof__: First note that if $x\equiv y\pmod2$ then $x,y$ are both odd, so $z^2\equiv2\pmod4$, contradiction. Hence exactly one of $x,y$ is odd, so $z$ is also odd.

Now the equation can be factored in $\bb Z[i]$ as

$$(x+yi)(x-yi)=z^2.$$

Suppose that some irreducible $\pi\in\bb Z[i]$ divides both $x+yi$ and $x-yi$. Then $\pi$ divides their sum $2x$ and their product $z^2$. But $x$ and $z$ are coprime in $\bb Z$ (otherwise $p\mid x$, $p\mid z$ implies $p\mid y$, contradiction), hence so are $2x$ and $z^2$ (since $z$ is odd). Hence there exists integers $a,b$ with $2ax+bz^2=1$, so $\pi\mid1$, contradiction. Hence $x+yi$ and $x-yi$ have no common irreducible factors in $\bb Z[i]$.

Now for each irreducible $\pi\in\bb Z[i]$ that divides $x+yi$, say $e$ times (ie. $\pi^e\mid x+yi$ and $\pi^{e+1}\nmid x+yi$), $\pi$ does not divide $x-yi$, so $\pi$ also divides $z^2$ $e$ times. Hence $e$ is twice the number of times that $\pi$ divides $z$, so $e$ is even. Thus every irreducible factor in the prime factorisation of $x+yi$ appears with even exponent, so $x+yi=u\alpha^2$ for some unit $u\in\\{\pm1,\pm i\\}$ and some $\alpha\in\bb Z[i]$.

Finally, write $\alpha=m+ni$, so $\alpha^2=(m^2-n^2)+2mni$. Comparing this with $x+yi=u\alpha^2$ gives the desired form for $x,y$, and

$$z^2=N(x+yi)=N(m+ni)^2=(m^2+n^2)^2$$

gives the desired form for $z$. Any common factor of $m$ and $n$ also divides $x$, $y$ and $z$, so $m$ and $n$ are coprime. $\qed$

## Eisenstein integers

We can make an analogous construction with the cube root of unity $\omega=e^{2\pi i/3}$, to obtain the ring of __Eisenstein integers__, given by

$$\bb Z[\omega]=\\{a+b\omega\,:\,a,b\in\bb Z\\}.$$

Note that $\omega^3=1$ implies $\omega^2+\omega+1=0$. We also have $\overline\omega=\omega^2$.

Again, define a norm function $N:\bb Z[\omega]\to\bb Z_{\geq0}$ by $N(a+b\omega)=a^2-ab+b^2$. Then we have

$$\begin{aligned}
(a+b\omega)\overline{(a+b\omega)}&=a^2+2ab\Re(\omega)+b^2|\omega|^2\\
&=a^2-ab+b^2=N(a+b\omega),
\end{aligned}$$

so we have the following results as before:

__Proposition__: $N(\alpha)=\alpha\overline\alpha=\lvert\alpha\rvert^2$. $\qed$

__Corollary__: $N(\alpha\beta)=N(\alpha)N(\beta)$. $\qed$

__Corollary__: If $\alpha\mid\beta$ in $\bb Z[\omega]$, then $N(\alpha)\mid N(\beta)$ in $\bb Z$. $\qed$

__Proposition__: $u\in\bb Z[\omega]$ is a unit if and only if $N(u)=1$. $\qed$

__Corollary__: The units of $\bb Z[\omega]$ are $\pm1$, $\pm\omega$, and $\pm\omega^2$.

__Proof__: If $a+b\omega$ is a unit in $\bb Z[\omega]$, then

$$4=4N(a+b\omega)=3(a-b)^2+(a+b)^2.$$

Hence $(a-b,a+b)\in\\{(\pm1,\pm1),(0,\pm2)\\}$. Each of these six cases gives one of the six possibilities in the claim, by noting that $1+\omega=-\omega^2.$ $\qed$

__Theorem__: $\bb Z[\omega]$ is a PID.

__Proof__: This is completely analogous to the previous proof in $\bb Z[i]$. The relevant computation is as follows: if $z=x+y\omega\in\bb C$, take $m,n\in\bb Z$ with $\lvert x-m\rvert\leq\frac12$, $\lvert y-n\rvert\leq\frac12$. Then

$$\begin{aligned}
|z-(m+n\omega)|^2&=(x-m)^2-(x-m)(y-n)+(y-n)^2\\
&=\frac{3((x-m)-(y-n))^2+((x-m)+(y-n))^2}4\\
&\leq1,
\end{aligned}$$

with equality possible only if $\lvert(x-m)-(y-n)\rvert=\lvert(x-m)+(y-n)\rvert=1$. It is easy to check that this never occurs. $\qed$

__Corollary__: $\bb Z[\omega]$ is a UFD. $\qed$

## The irreducible elements of $\bb Z[\omega]$

By methods analogous to the case of Gaussian integers, we can determine the form of all irreducible Eisenstein integers. We will only sketch the proofs.

__Proposition__: Let $\alpha\in\bb Z[i]$.
1. If $N(\alpha)=p$ for some rational prime $p$, then $\alpha$ is irreducible.
2. If $N(\alpha)=p^2$ for some rational prime $p\equiv2\pmod3$, then $\alpha$ is irreducible.

__Proof__: Analogous to the case of Gaussian integers. The relevant computation for (2) is the following: for $\alpha=a+b\omega$, we have

$$4N(\alpha)=3(a-b)^2+(a+b)^2\not\equiv2\pmod3.\ \qed$$

__Proposition__: Let $p\equiv1\pmod3$ be a rational prime. Then $p=\alpha\overline\alpha$ for some irreducible $\alpha\in\bb Z[\omega]$.

__Proof__: Let $g$ be a generator of $\bb F_p^\times$. Then for any integer $n\equiv g^{(p-1)/3}\not\equiv1\pmod p$, we have $n^3\equiv1\pmod p$, so

$$p\mid n^2-n+1=(n+\omega)(\overline{n+\omega}).$$

But it is easy to check that $p$ does not divide either factor in $\bb Z[\omega]$. Hence $p=\alpha\beta$ for some non-units $\alpha,\beta\in\bb Z[\omega]$, and we finish as before. $\qed$

__Theorem__: Up to associates, the list of all irreducible elements of $\bb Z[i]$ are:
1. $1-2\omega$;
2. $a+b\omega$, where $a^2-ab+b^2=p$ and $p\equiv1\pmod3$ is a rational prime; and
3. $p\equiv2\pmod3$ a rational prime.

__Proof__: Analogous to the case for $\bb Z[i]$. $\qed$