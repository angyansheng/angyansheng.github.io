---
title: 'Several Complex Variables (II): Holomorphic functions'
layout: post
tag: [several complex variables]
date: 2018-09-04 10:03:37 +0800
---

In this post, we look at holomorphic, analytic, and complex differentiable functions in several complex variables. As in the one variable case, we show that many of these notions are equivalent.

<!--more-->

## Recap: one variable

Let $f:U\to\bb C$, where $U\subseteq\bb C$ is open and connected. Recall the following definitions:

1. $f$ satisfies the __Cauchy-Riemann equations__ if $\frac{\del f}{\del\overline z}=0$ holds in $U$.
2. $f$ has __'Cauchy integral representation'__ (non-standard term) if for any disc $\Delta=\Delta(z_0,r)$ with $\overline\Delta\subseteq U$, $f$ can be written as

   $$f(z)=\frac1{2\pi i}\int_{\del\Delta}\!\frac{f(\zeta)}{\zeta-z}d\zeta$$

   for all $z\in\Delta$.
   <!-- for some continuous function $\phi:\del\overline\Delta\to\bb C$. -->
3. $f$ is __analytic__ if for any $z_0\in U$, $f$ has a power series expansion

   $$f(z)=c_0+c_1(z-z_0)+c_2(z-z_0)^2+\cdots,$$

   with $c_k\in\bb C$, which converges for all $z$ in some nonempty open disc $\Delta(z_0,r)$.
4. $f$ is __holomorphic__, or __complex differentiable__,  if the limit

   $$f'(z_0)\coloneqq\lim_{z\to z_0}\frac{f(z)-f(z_0)}{z-z_0}$$

   exists for all $z_0\in U$.

{% comment %}
<!-- __Theorem__: Let $f:U\to\bb C$, where $U\subseteq\bb C$ is open and connected. Then the following are equivalent:

1. $f$ is holomorphic in $U$;
2. $f\in C^1(U)$, and for any region $D$ with piecewise-$C^1$ boundary and closure contained in $U$, we have

   $$\int_{\del D}\!f(z)\,dz=0;$$
2. $f$ has Cauchy integral representation in $U$, in fact with $\phi=f$;
3. $f$ is analytic in $U$;
4. $f$ is complex differentiable in $U$.
 -->
{% endcomment %}

It is a fundamental result in classical complex analysis that these four definitions are equivalent. Here we give an outline of the proof.

$(1)\Rightarrow(2)$: For $z\in\Delta$, check that $g(\zeta)=\frac{f(\zeta)-f(z)}{\zeta-z}$ satisfies $\frac{\del g}{\del\overline\zeta}=0$. By Green's formula (or the generalised Cauchy integral formula) on the region $\Delta\backslash\overline\Delta(z,\eps)$, we get

$$\int_{\del\Delta}\!g(\zeta)\,d\zeta=\int_{\del\Delta(z,\eps)}g(\zeta)\,d\zeta.$$

As $\eps\to0^+$, the RHS is the integral of a bounded function over a curve of length $\to0$, so it goes to 0. Hence

$$\int_{\del\Delta}\!\frac{f(\zeta)}{\zeta-z}d\zeta=\int_{\del\Delta}\!\frac{f(z)}{\zeta-z}d\zeta=2\pi if(z).$$

$(2)\Rightarrow(3)$: For $z\in\Delta=\Delta(z_0,r)$, we have

$$\begin{aligned}
f(z)&=\frac1{2\pi i}\int_{\del\Delta}\!\frac{f(\zeta)}{\zeta-z}d\zeta\\
&=\frac1{2\pi i}\int_{\del\Delta}\!\frac{f(\zeta)}{\zeta-z_0}\frac1{1-\frac{z-z_0}{\zeta-z_0}}d\zeta\\
&=\frac1{2\pi i}\sum_{n=0}^\infty\left(\int_{\del\Delta}\!\frac{f(\zeta)}{(\zeta-z_0)^{n+1}}d\zeta\right)(z-z_0)^n,
\end{aligned}$$

where the geometric series converges <!--  absolutely since $\lvert\frac{z-z_0}{\zeta-z_0}\rvert<1$, and hence  -->normally (ie. uniformly on compact subsets), justifying the exchange of sum and integral in the last line. Hence we may take

$$c_n=\frac1{2\pi i}\int_{\del\Delta}\!\frac{f(\zeta)}{(\zeta-z_0)^{n+1}}d\zeta.$$

$(3)\Rightarrow(4)$: We expect that the derivative $f'$ is given by termwise differentiation. This is a theorem from real analysis about power series, whose proof carries over to the complex case.

{% comment %}
<!-- Without loss of generality, assume $z_0=0$.

We expect that the derivative of $f(z)=\sum_{n=0}^\infty c_nz^n$ is given by termwise differentiation, so set $g(z)=\sum_{n=1}^\infty nc_nz^{n-1}$ and $f_N(z)=\sum_{n=0}^Nc_nz^n$. Then for all $\lvert z\rvert< r$, $\lvert\zeta\rvert< r$,

$$\begin{aligned}
&g(z)-\frac{f(\zeta)-f(z)}{\zeta-z}\\
&=g(z)-f_N'(z)+\left(f_N'(z)-\frac{f_N(\zeta)-f_N(z)}{\zeta-z}\right)+\frac{(f_N-f)(\zeta)-(f_N-f)(z)}{\zeta-z}\\
&=\sum_{n=N+1}^\infty nc_nz^{n-1}+\left(f_N'(z)-\frac{f_N(\zeta)-f_N(z)}{\zeta-z}\right)-\sum_{n=N+1}^\infty c_n\frac{\zeta^n-z^n}{\zeta-z}.
\end{aligned}$$

Now $f$ and $g$ have the same radius of convergence, so the first term goes to 0 for $N\to\infty$. The same is true for the last term, since

$$\left|\frac{\zeta^n-z^n}{\zeta-z}\right|=\left|\zeta^{n-1}+\zeta^{n-2}z+\cdots+z^{n-1}\right|\leq n\max(|z|,|\zeta|)^{n-1}.$$

Also, for fixed large $N$, the middle term goes to 0 as $\zeta\to z$. Hence

$$\lim_{\zeta\to z}\left(g(z)-\frac{f(\zeta)-f(z)}{\zeta-z}\right)=0,$$

ie. $g(z)=f'(z)$. -->
{% endcomment %}

$(4)\Rightarrow(1)$: We proved this in the [previous post]({% post_url 2018-09-02-several-complex-variables-i %}). In summary, taking the limit for the derivative in two different directions gives the usual formulation of the Cauchy-Riemann equations

$$\frac{\del u}{\del x}=\frac{\del v}{\del y},\qquad\frac{\del v}{\del x}=-\frac{\del u}{\del y},$$

which can be verified to be equivalent to $\frac{\del f}{\del\overline z}=0$ by explicit computation.

## Several variables

We want to extend the above results to the case of several complex variables, which we write as $z=(z_1,z_2,\ldots,z_n)\in\bb C^n$. Analogously to the one variable setting, we can define $z_j=x_j+iy_j$,

$$\begin{aligned}
dz_j&=dx_j+i\,dy_j\\
d\overline{z_j}&=dx_j-i\,dy_j
\end{aligned}\qquad
\begin{aligned}
\frac\del{\del z_j}&=\frac12\left(\frac\del{\del x_j}-i\frac\del{\del y_j}\right)\\
\frac\del{\del\overline z_j}&=\frac12\left(\frac\del{\del x_j}+i\frac\del{\del y_j}\right).
\end{aligned}$$

Let $f:U\to\bb C$, where $U\subseteq\bb C^n$ is open and connected. We make the following definitions:

1. $f$ satisfies the __Cauchy-Riemann equations__ if $\frac{\del f}{\del\overline z_j}=0$ holds in $U$ for all $1\leq j\leq n$.
2. $f$ has __'Cauchy integral representation'__ if for any polydisc $\Delta=\Delta(a,r)$ with $\overline\Delta\subseteq U$, $f$ can be written as

   $$f(z)=\frac1{(2\pi i)^n}\int_{\del\Delta(a_n,r_n)}\!\!\!\!\cdots\int_{\del\Delta(a_1,r_1)}\!\frac{f(\zeta_1,\ldots,\zeta_n)\,d\zeta_1\cdots d\zeta_n}{(\zeta_1-z_1)\cdots(\zeta_n-z_n)}$$

   for all $z\in\Delta$.
3. $f$ is __analytic__ if for any $a\in U$, $f$ has a power series expansion

   $$f(z)=\sum_{k_1,\ldots,k_n\geq0}c_{k_1,\ldots,k_n}(z_1-a_1)^{k_1}\cdots(z_n-a_n)^{k_n},$$

   with $c_{k_1,\ldots,k_n}\in\bb C$, which converges for all $z$ in some nonempty open disc $\Delta(a,r)$.
4. $f$ is __holomorphic__, or __complex differentiable__, if for each $a\in U$ there exists a linear functional $Df(a):\bb C^n\to\bb C$ such that
  
   $$\lim_{z\to a}\frac{|f(z)-f(a)-Df(a)(z-a)|}{|z-a|}=0.$$

We can also consider functions that are analytic separately in each variable:

<ol start="0">
   <li> $f$ is <b>separately analytic</b> if for any $a\in U$, the functions

   $$f_j:\Delta(0,\eps)\subseteq\bb C\to\bb C,\qquad w\mapsto f(a+we_j)$$

   are analytic at $w=0$ for each $1\leq j\leq n$. Here $\{e_1,\ldots,e_n\}$ is the basis of $\bb C^n$ dual to coordinates $\{z_1,\ldots,z_n\}$.
   </li>
</ol>

Note that this definition depends on the choice of coordinates.

Now we can investigate the relationship between these notions.

$(0)\Leftrightarrow(1)$: Clear.

$(0)\Rightarrow(2)$: This follows directly from $n$ applications of the Cauchy integral formula.

$(2)\Rightarrow(3)$: This is known as __Osgood's Lemma__, when we add an assumption that $f$ is bounded on compact subsets of $U$. In particular, this holds when $f$ is continuous.

We proceed as in the one variable case:

$$\begin{aligned}
f(z)&=\frac1{(2\pi i)^n}\int\!\!\cdots\!\!\int\!\frac{f(\zeta_1,\ldots,\zeta_n)\,d\zeta_1\cdots d\zeta_n}{(\zeta_1-z_1)\cdots(\zeta_n-z_n)}\\
&=\frac1{(2\pi i)^n}\int\!\!\cdots\!\!\int\!\frac{f(\zeta_1,\ldots,\zeta_n)\,d\zeta_1\cdots d\zeta_n}{(\zeta_1-a_1)\cdots(\zeta_n-a_n)}\frac1{1-\frac{z_1-a_1}{\zeta_1-a_1}}\cdots\frac1{1-\frac{z_n-a_n}{\zeta_n-a_n}}\\
&=\sum_{k_1,\ldots,k_n\geq0}c_{k_1,\ldots,k_n}(z_1-a_1)^{k_1}\cdots(z_n-a_n)^{k_n},
\end{aligned}$$

where

$$c_{k_1,\ldots,k_n}=\frac1{(2\pi i)^n}\int\!\!\cdots\!\!\int\!\frac{f(\zeta_1,\ldots,\zeta_n)\,d\zeta_1\cdots d\zeta_n}{(\zeta_1-a_1)^{k_1+1}\cdots(\zeta_n-a_n)^{k_n+1}}.$$

We can exchange sum and integral in the last line since the infinite sum converges normally by the boundedness assumption.

> In general, $(2)\Rightarrow(3)$ still holds without the boundedness assumption; this is known as __Hartogs's theorem__. We omit the proof because it requires a number of technical results. In practice, it is usually easy to show the continuity of $f$, so Osgood's lemma is sufficient to deduce analyticity from separate analyticity.

$(3)\Rightarrow(4)$: Again, we expect that the derivative is given by termwise differentiation.

From the one variable case, we know that as a power series in $z_1$, $f$ can be differentiated termwise to give

$$\begin{aligned}
\frac\del{\del z_1}f(z)&=\sum_{k_1\geq1}C_{k_1}(z_1-a_1)^{k_1-1},\\
\text{where }C_{k_1}&=k_1\sum_{\mathclap{k_2,\ldots,k_n\geq0}}c_{k_1,\ldots,k_n}(z_2-a_2)^{k_2}\cdots(z_n-a_n)^{k_n},
\end{aligned}$$

which is a convergent power series in $\Delta=\Delta(a,r)$; in particular, $\frac{\del f}{\del z_1}$ is continuous in $\Delta$.

Similarly, all partial derivatives of $f$ are continuous in $\Delta$; hence the total derivative $Df$ exists.

$(4)\Rightarrow(0)$: Taking $z=a+we_j$ gives

$$\begin{aligned}
\lim_{w\to0}\frac{|f(a+we_j)-f(a)-wDf(a)(e_j)|}{|w|}&=0\\
\implies\lim_{w\to0}\frac{f(a+we_j)-f(a)}w&=Df(a)(e_j).
\end{aligned}$$

In particular, $f$ is holomorphic (hence analytic) separately in each $z_j$.

{% comment %}
()* &
{% endcomment %}