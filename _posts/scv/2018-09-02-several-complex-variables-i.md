---
title: 'Several Complex Variables (I): $z$ and $\overline z$'
layout: post
tag: [several complex variables]
date: 2018-09-02 09:33:12 +0800
---

This series of posts are adapted from the notes for the topics course MA4291, offered in AY18/19 Sem 1 by Prof Chin Chee Whye.

In this post, we recast some of one-variable complex analysis in terms of the differentials $dz$ and $d\overline z$, and the differential operators $\frac\del{\del z}$ and $\frac\del{\del\overline z}$.

<!--more-->

## Preliminaries

Let $U$ be an open subset of $\bb C$. Note that every $z\in U$ can be written as $z=x+iy$ with $x,y\in\bb R$, and every function $f:U\to\bb C$ can be written as

$$f(z)=u(x,y)+v(x,y)$$

with $u,v:U\subseteq\bb C\cong\bb R^2\to\bb R$.

Now for any $p\in U$, the $\bb R$-tangent space $T_pU$ has real dimension 2, with basis $\\{\frac\del{\del x},\frac\del{\del y}\\}$. We can consider its __complexification__ $T_pU\otimes_{\bb R}\bb C$, which we get by formally replacing the coefficient field $\bb R$ by $\bb C$. This has _complex_ dimension 2, with the same basis.

Similarly, we can consider the complexification of the cotangent space (aka the space of 1-forms):

$$(T_pU)^\vee\otimes_{\bb R}\bb C=(T_pU\otimes_{\bb R}\bb C)^\vee,$$

with dual basis $\\{dx,dy\\}$.

Now the usual exterior derivative

$$d:\Omega^0_{\bb R}(U)\to\Omega^1_{\bb R}(U),\qquad
\begin{aligned}
\Omega^0_{\bb R}(U)=C^\infty_{\bb R}(U)\\
\Omega^1_{\bb R}(U)=(T_pU)^\vee
\end{aligned}$$

is an $\bb R$-linear map from the space of 0-forms to the space of 1-forms. This has a natural $\bb C$-linear extension to the complexifications:

$$d:\Omega^0_{\bb C}(U)\to\Omega^1_{\bb C}(U),\qquad
\begin{aligned}
\Omega^0_{\bb C}(U)&=C^\infty_{\bb C}(U)\\
\Omega^1_{\bb C}(U)&=(T_pU\otimes_{\bb R}\bb C)^\vee,
\end{aligned}$$

by defining $df=du+i\,dv$.

In particular, with the functions $z=x+iy$, $\overline z=x-iy$, we have

$$\boxed{dz=dx+i\,dy,\qquad d\overline z=dx-i\,dy.}$$

Note that $\\{dz,d\overline z\\}$ form a basis for $(T_pU\otimes_{\bb R}\bb C)^\vee$, satisfying

$$\begin{aligned}
dz(\frac\del{\del x})&=1,&d\overline z(\frac\del{\del x})&=1,\\
dz(\frac\del{\del y})&=i,&d\overline z(\frac\del{\del y})&=-i.
\end{aligned}$$

We can thus solve for the dual basis $\\{\frac\del{\del z},\frac\del{\del\overline z}\\}$ in $T_pU\otimes_{\bb R}\bb C$:

$$\begin{aligned}
\begin{pmatrix}\frac\del{\del x}\\\frac\del{\del y}\end{pmatrix}
&=\begin{pmatrix}1&1\\i&-i\end{pmatrix}
\begin{pmatrix}\frac\del{\del z}\\\frac\del{\del\overline z}\end{pmatrix}\\
\begin{pmatrix}\frac\del{\del z}\\\frac\del{\del\overline z}\end{pmatrix}
&=\begin{pmatrix}1&1\\i&-i\end{pmatrix}^{-1}
\begin{pmatrix}\frac\del{\del x}\\\frac\del{\del y}\end{pmatrix}\\
&=\frac12\begin{pmatrix}1&-i\\1&i\end{pmatrix}
\begin{pmatrix}\frac\del{\del x}\\\frac\del{\del y}\end{pmatrix},
\end{aligned}$$

or

$$\boxed{\frac\del{\del z}=\frac12\left(\frac\del{\del x}-i\frac\del{\del y}\right),\qquad
\frac\del{\del\overline z}=\frac12\left(\frac\del{\del x}+i\frac\del{\del y}\right).}$$

## The Cauchy-Riemann equations

Recall that $f:U\to\bb C$ is __complex differentiable__ if the limit

$$\lim_{w\to0}\frac{f(z+w)-f(z)}w$$

exists for all $z\in U$. In particular, taking $w=t$ and $w=it$ for $t\to0$ real gives respectively

$$\begin{aligned}
\lim_{t\to0}\frac{u(x+t,y)+iv(x+t,y)-u(x,y)-iv(x,y)}t&=\frac{\del u}{\del x}+i\frac{\del v}{\del x}\\
\lim_{t\to0}\frac{u(x,y+t)+iv(x,y+t)-u(x,y)-iv(x,y)}{it}&=\frac{\del v}{\del y}-i\frac{\del u}{\del y}.
\end{aligned}$$

Extracting the real and imaginary parts gives the __Cauchy-Riemann equations__

$$\frac{\del u}{\del x}=\frac{\del v}{\del y},\qquad\frac{\del v}{\del x}=-\frac{\del u}{\del y}.$$

On the other hand, we can evaluate

$$\begin{aligned}
\frac{\del f}{\del\overline z}&=\frac12\left(\frac\del{\del x}+i\frac\del{\del y}\right)(u+iv)\\
&=\frac12\left(\frac{\del u}{\del x}+i\frac{\del u}{\del y}+i\frac{\del v}{\del x}-\frac{\del v}{\del y}\right).
\end{aligned}$$

This is equal to 0 precisely when the Cauchy-Riemann equations hold; hence the Cauchy-Riemann equations can be written succintly as

$$\boxed{\frac{\del f}{\del\overline z}=0.}$$

## The generalised Cauchy integral formula

The differentials $dz$ and $d\overline z$ also give a sleek way of proving a generalisation of the Cauchy integral formula. Firstly, note that by splitting into real and complex parts, we see that the theory of differential forms carry over almost verbatim to the complexification.

Let $U$ be an open subset of $\bb C$ bounded by a rectifiable Jordan curve $\gamma$. For any function $f$ which is $C^\infty$ in a neighbourhood of $\overline U$, and any $z\in U$, we have (as forms in $\zeta$)

$$\begin{aligned}
d\left(f(\zeta)\frac{d\zeta}{\zeta-z}\right)&=d\left(\frac{f(\zeta)}{\zeta-z}\right)d\zeta\\
&=\frac\del{\del\overline\zeta}\left(\frac{f(\zeta)}{\zeta-z}\right)d\overline\zeta\wedge d\zeta\\
&=\frac{\del f(\zeta)}{\del\overline\zeta}\frac{d\overline\zeta\wedge d\zeta}{\zeta-z}.
\end{aligned}$$

Take $r>0$ small enough such that the disc $\Delta(z,r)$ lies in $U$. Let $U_r=U\backslash\Delta(z,r)$ and $\gamma_r$ be the boundary of $\Delta(z,r)$. Then by Stokes's theorem,

$$\iint_{U_r}\!\frac{\del f(\zeta)}{\del\overline\zeta}\frac{d\overline\zeta\wedge d\zeta}{\zeta-z}
=\int_\gamma\!f(\zeta)\frac{d\zeta}{\zeta-z}-\int_{\gamma_r}\!f(\zeta)\frac{d\zeta}{\zeta-z}.$$

We want to take the limit $r\to0^+$. The idea is that we can replace $U_r$ by $U$ on the LHS because $\frac1{\zeta-z}$ is integrable over bounded regions of the plane, and the second term on the RHS goes to $2\pi if(z)$. We give a detailed argument below.

> For the LHS, note that
> 
> $$\begin{aligned}
d\overline\zeta\wedge d\zeta&=(dx-i\,dy)\wedge(dx+i\,dy)\\
&=2i\,dx\wedge dy.
\end{aligned}$$
> 
> Write $M_r=\sup_{\Delta(z,r)}\left\lvert\frac{\del f(\zeta)}{\del\overline\zeta}\right\rvert$, which is bounded since $f$ is $C^1$. Using polar coordinates about $z$, we have
> 
> $$\begin{aligned}
&\left|\left(\iint_U-\iint_{U_r}\right)\frac{\del f(\zeta)}{\del\overline\zeta}\frac{d\overline\zeta\wedge d\zeta}{\zeta-z}\right|\\
&=\left|\iint_{\Delta(z,r)}\!\frac{\del f(\zeta)}{\del\overline\zeta}\frac{d\overline\zeta\wedge d\zeta}{\zeta-z}\right|\\
&\leq2M_r\left|\iint_{\Delta(z,r)}\!\frac{dx\wedge dy}{\zeta-z}\right|\\
&=2M_r\left|\int_0^r\int_0^{2\pi}\!\frac{r\,dr\wedge d\theta}r\right|\\
&=4\pi rM_r\to0\qquad\text{as }r\to0^+.
\end{aligned}$$
> 
> For the RHS, write $D_r=\sup_{\gamma_r}\left\lvert\frac{f(\zeta)-f(z)}{\zeta-z}\right\rvert$, which is bounded since $f$ is $C^1$. Hence
> 
> $$\begin{aligned}
&\left|2\pi if(z)-\int_{\gamma_r}\!f(\zeta)\frac{d\zeta}{\zeta-z}\right|\\
&=\left|\int_{\gamma_r}\!\frac{f(\zeta)-f(z)}{\zeta-z}d\zeta\right|\\
&\leq2\pi rD_r\to0\qquad\text{as }r\to0^+.
\end{aligned}$$

This gives the generalised Cauchy integral formula:

$$\boxed{f(z)=\frac1{2\pi i}\int_\gamma\!f(\zeta)\frac{d\zeta}{\zeta-z}+\frac1{2\pi i}\iint_U\!\frac{\del f(\zeta)}{\del\overline\zeta}\frac{d\zeta\wedge d\overline\zeta}{\zeta-z}.}$$

Note that this holds for all smooth $f$. In particular, if $f$ is complex differentiable, then the last term above vanishes by the Cauchy-Riemann equations, and we recover the usual Cauchy integral formula.

{% comment %}
()* &
{% endcomment %}