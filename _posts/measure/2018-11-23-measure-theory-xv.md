---
title: 'Measure Theory (XV): The Fourier Transform on $\bb R$'
layout: post
tag: [measure theory]
date: 2018-11-23 11:38:33 +0800
---

The Fourier transform decomposes a function into components of different frequencies. Historically, Fourier series were developed to study periodic processes and the heat equation, but Fourier analysis has found applications in diverse areas such as number theory, combinatorics, and signal processing. 

The study of the Fourier transform has given rise to entire new areas of mathematics, such as harmonic analysis and functional analysis. In this post, we will only study a small part of the rigorous foundations for Fourier analysis, namely some conditions for the existence of the Fourier transform and its inverse.

<!--more-->

## The Fourier transform

Firstly, note that our definition for Lebesgue measurable and Lebesgue integrable functions extend naturally to $\bb C$-valued functions: if $f:\bb R\to\bb C$, write $f=u+iv$ with $u,v:\bb R\to\bb R$. Then we say that $f$ is Lebesgue measurable (resp. integrable) if both $u$ and $v$ are Lebesgue measurable (resp. integrable), and define

$$\int\!f\,d\lambda=\int\!u\,d\lambda+i\int\!v\,d\lambda.$$

__Lemma__: (Triangle inequality for integrals) Let $f:\bb R\to\bb C$ be such that $\lvert f\rvert\in L^1(\bb R)$. Then

$$\left|\int\!f\,d\lambda\right|\leq\int\!|f|\,d\lambda.$$

__Proof__: Choose $\alpha\in\bb C$ such that $\lvert\alpha\rvert=1$ and the first line holds:

$$\begin{aligned}
\left|\int\!f\,d\lambda\right|&=\alpha\int\!f\,d\lambda\\
&=\int\!\alpha f\,d\lambda\\
&=\int\!\Re(\alpha f)\,d\lambda\\
&\leq\int\!|\alpha f|\,d\lambda\\
&=\int\!|f|\,d\lambda.\ \qed
\end{aligned}$$

Now for $f\in L^1(\bb R)$, define the __Fourier transform__ of $f$ by

$$\widehat f(y)=\int\!f(x)e^{-ixy}\,d\lambda(x).$$

Note that the Fourier transform is $\bb R$-linear, hence $\bb C$-linear; as such, there is no loss in generality if we restrict ourselves to studying the Fourier transform only on $\bb R$-valued functions.

An important first example is the Gaussian function, whose Fourier transform is simply a multiple of itself.

__Proposition__: Let $g(x)=\frac1{\sqrt{2\pi}}e^{-\frac{x^2}2}$. Then $\widehat g(y)=e^{-\frac{y^2}2}$.

__Proof__: By differentiation under the integral sign, converting into a Riemann integral, and integration by parts, we have

$$\begin{aligned}
\widehat g(y)&=\frac1{\sqrt{2\pi}}\int\!e^{-\frac{x^2}2}e^{-ixy}\,d\lambda(x)\\
\widehat g'(y)&=\frac1{\sqrt{2\pi}}\int\!\frac\del{\del y}e^{-\frac{x^2}2}e^{-ixy}\,d\lambda(x)\\
&=\frac i{\sqrt{2\pi}}\int_{-\infty}^\infty\!-xe^{-\frac{x^2}2}e^{-ixy}\,dx\\
&=\frac i{\sqrt{2\pi}}\left(\left[e^{-\frac{x^2}2}e^{-ixy}\right]_ {-\infty}^\infty-\int_{-\infty}^\infty\!e^{-\frac{x^2}2}(-iy)e^{-ixy}\,dx\right)\\
&=-\frac y{\sqrt{2\pi}}\int_{-\infty}^\infty\!e^{-\frac{x^2}2}e^{-ixy}\,dx\\
&=-y\widehat g(y).
\end{aligned}$$

This differential equation has a unique solution

$$\widehat g(y)=\widehat g(0)e^{-\frac{y^2}2}=e^{-\frac{y^2}2},$$

where the computation $\widehat g(0)=\int\\!g\,d\lambda=1$ is well-known. $\qed$

We now establish some properties of the Fourier transform on $L^1(\bb R)$.

__Proposition__: Let $f\in L^1(\bb R)$. Then $\widehat f$ is continuous and bounded, with $\sup_y\lvert\widehat f(y)\rvert\leq\\|f\\|_ 1$.

__Proof__: Note that both the real and imaaginary parts of $f(x)e^{-ixy}$ are bounded in absolute value by $\lvert f(x)\rvert$. Hence for any sequence $(y_n)$ converging to $y$, LDCT yields

$$\begin{aligned}
\lim_{n\to\infty}\widehat f(y_n)&=\lim_{n\to\infty}\int\!f(x)e^{-ixy_n}\,d\lambda(x)\\
&=\int\!\lim_{n\to\infty}f(x)e^{-ixy_n}\,d\lambda(x)\\
&=\int\!f(x)e^{-ixy}\,d\lambda(x)\\
&=\widehat f(y).
\end{aligned}$$

Hence $\widehat f$ is continuous. Now $\lvert\widehat f(y)\rvert\leq\\|f\\|_ 1$ follows from the triangle inequality for integrals. $\qed$

Next we list the effects of translation and scaling of the input function on the Fourier transform. These can all be proven with a linear change of variables.

__Proposition__: Let $f\in L^1(\bb R)$.
1. If $F(x)=f(x-k)$, then $\widehat F(y)=e^{-iky}\widehat f(y)$.
2. If $G(x)=f(\frac xk)$, then $\widehat G(y)=\lvert k\rvert\widehat f(ky)$.
3. If $H(x)=e^{ikx}f(x)$, then $\widehat H(y)=\widehat f(y-k)$. $\qed$

The Fourier transform decays to zero at $\pm\infty$:

__Riemann--Lebesgue lemma__: Let $f\in L^1(\bb R)$. Then $\lim_{y\to\pm\infty}\widehat f(y)=0$.

__Proof__: First we prove the statement for $g\in C^\infty_c(\bb R)$. Integration by parts gives

$$\begin{aligned}
|\widehat g(y)|&=\left|\int_{-\infty}^\infty\!g(x)e^{-ixy}\,dx\right|\\
&=\left|-\frac1{iy}\left([g(x)e^{-ixy}]_ {-\infty}^\infty-\int_{-\infty}^\infty g'(x)e^{-ixy}\,dx\right)\right|\\
&\leq\frac1{|y|}\int\!|g'(x)|\,dx,
\end{aligned}$$

which goes to $0$ as $y\to\pm\infty$.

Fix $\eps>0$. Now for general $f\in L^1(\bb R)$, pick $g\in C^\infty_c(\bb R)$ with $\\|f-g\\|_ 1<\frac\eps2$; then

$$\begin{aligned}
|\widehat f(y)|&\leq|\widehat g(y)|+|\widehat{(f-g)}(y)|\\
&<\frac\eps2+\|f-g\|_ 1<\eps
\end{aligned}$$

for large enough $\lvert y\rvert$; this is what we wanted to show. $\qed$

Next we see how the Fourier transform interacts with the convolution and product of two functions.

__Proposition__: Let $f,g\in L^1(\bb R)$. Then:
- $\widehat{f* g}=\widehat f\widehat g$; and
- $\int\\!\widehat fg\,d\lambda=\int\\!f\widehat g\,d\lambda$.

__Proof__: By the Fubini-Tonelli theorem, we have

$$\begin{aligned}
\widehat{f* g}(y)&=\int\!(f* g)(x)e^{-ixy}\,d\lambda(x)\\
&=\int\!\left(\int\!f(x-z)g(z)\,d\lambda(z)\right)e^{-ixy}\,d\lambda(x)\\
&=\int\!\left(\int\!f(x-z)e^{-i(x-z)y}\,d\lambda(x)\right)g(z)e^{-izy}\,d\lambda(z)\\
&=\widehat f(y)\widehat g(y),
\end{aligned}$$

and

$$\begin{aligned}
\int\!\widehat fg\,d\lambda&=\int\!\left(\int\!f(x)e^{-ixy}\,d\lambda(x)\right)g(y)\,d\lambda(y)\\
&=\int\!\left(\int\!g(y)e^{-iyx}\,d\lambda(y)\right)f(x)\,d\lambda(x)\\
&=\int\!f\widehat g\,d\lambda.\ \qed
\end{aligned}$$

## Fourier inversion

We now look at conditions under which we can recover a function $f$ from its Fourier transform $\hat f$. Our first result gives $f$ as an explicit formula in terms of $\hat f$, but only holds when $\hat f$ is sufficiently nice (namely, when it is Lebesgue integrable).

__Fourier Inversion Theorem__: Let $f\in L^1(\bb R)$, and suppose that $\widehat f\in L^1(\bb R)$. Then for $\lambda$-a.e. $x\in\bb R$, we have

$$f(x)=\frac1{2\pi}\int\!\widehat f(y)e^{ixy}\,d\lambda(y).$$

In other words, $f(x)=\frac1{2\pi}\widehat{\widehat f}(-x)$.

__Proof__: Let $g(x)=\frac1{\sqrt{2\pi}}e^{-\frac{x^2}2}$ be the Gaussian function, and let $g_\eps(x)=\frac1\eps g(\frac x\eps)$. Notice that if we define

$$h_\eps(x)=\frac1{\sqrt{2\pi}}e^{ix_0x}g(\eps x),$$

then

$$\widehat{h_\eps}(y)=\frac1{\sqrt{2\pi}\eps}\widehat g\left(\frac{y-x_0}\eps\right)=g_\eps(x_0-y).$$

Hence

$$\begin{aligned}
(f* g_\eps)(x_0)&=\int\!f(y)g_\eps(x_0-y)\,d\lambda(y)\\
&=\int\!f\widehat{h_\eps}\,d\lambda\\
&=\int\!\widehat fh_\eps\,d\lambda.
\end{aligned}$$

Now $\lvert\widehat fh_\eps\rvert\leq\frac1{\sqrt{2\pi}}\\|\widehat f\\|_ 1$, and

$$\lim_{\eps\to0^+}h_\eps(x)=\frac{g(0)}{\sqrt{2\pi}}e^{ix_0x}=\frac1{2\pi}e^{ix_0x},$$

so applying LDCT (to both the real and imaginary parts) gives

$$\lim_{\eps\to0^+}\int\!\widehat fh_\eps\,d\lambda=\frac1{\sqrt{2\pi}}\int\!e^{ix_0y}\widehat f(y)\,d\lambda(y).$$

However, since $\lim_{\eps\to0^+}\\|f* g_\eps-f\\|_ 1=0$, which implies that $f* g_\eps$ converges in measure to $f$ as $\eps\to0^+$, there is a subsequence $(\eps_k)$ converging to $0$ such that 

$$\lim_{k\to\infty}f* g_{\eps_k}(x)=f(x)\qquad\text{for }\lambda\text{-a.e. }x,$$

and we are done. $\qed$

## Fejér's theorem

However, in general $f\in L^1(\bb R)$ does not imply that $\widehat f\in L^1(\bb R)$. In this case, we can stil recover $f$ from $\widehat f$ by a limit process.

__Corollary__ (Fourier Summability Theorem): Let $(K_\eps)_ {\eps>0}$ be an approximate identity, with $\widehat{K_\eps}\in L^1(\bb R)$ for all $\eps>0$. Then for any $f\in L^1(\bb R)\cap L^p(\bb R)$, the functions

$$h_\eps(x)=\frac1{2\pi}\int\!\widehat f(y)\widehat{K_\eps}(y)e^{ixy}\,d\lambda(y)$$

converge to $f$ in $L^p(\bb R)$, ie.

$$\lim_{\eps\to0^+}\|h_\eps-f\|_ p=0.$$

__Proof__: Note that $f* K_\eps\in L^1(\bb R)\cap L^p(\bb R)$. By the Fourier inversion theorem, $h_\eps=f* K_\eps$ $\lambda$-a.e., so

$$\|h_\eps-f\|_ p=\|f* K_\eps-f\|_ p\to0.\ \qed$$

Next we investigate certain "windowing functions" or "kernels" given by

$$\mc F(x)=\frac1{2\pi}\frac{\sin^2(x/2)}{(x/2)^2},\qquad H(x)=\max(1-|x|,0).$$

The approximate identity $\mc F_\eps(x)=\frac1\eps\mc F(\frac x\eps)$ is known as __Fejér's kernel__.

__Proposition__: $\widehat H=2\pi\mc F$ and $\widehat{\mc F}=H$.

__Proof__: It is clear that $H\in L^1(\bb R)$, since it is continuous and has compact support. Also, since $\lvert\mc F(x)\rvert\leq\min(\frac1{2\pi},\frac2{\pi x^2})$, we also have $\mc F\in L^1(\bb R)$.

Now the first equation follows from direct computation:

$$\begin{aligned}
\widehat H(y)&=\int\!\max(1-|y|,0)e^{-ixy}\,d\lambda(x)\\
&=\int_{-1}^1\!(1-|y|)e^{-ixy}\,dx\\
&=2\int_0^1(1-y)\cos(xy)\,dx\\
&=\frac2y\left([ (1-x)\sin(xy)]_ 0^1+\int_0^1\!\sin(xy)\,dx\right)\\
&=\left[-\frac2{y^2}\cos(xy)\right]_ 0^1\\
&=2\frac{1-\cos y}{y^2}\\
&=\frac{\sin^2(y/2)}{(y/2)^2}=2\pi\mc F(y).
\end{aligned}$$

Now the Fourier inversion formula gives $H=\frac1{2\pi}\widehat{\widehat H}=\widehat{\mc F}$, as desired. $\qed$

Now applying the previous proposition to Fejér's kernel gives:

__Corollary (Fejér's theorem)__: Let $f\in L^1(\bb R)$. Then the functions

$$H_j(x)=\frac1{2\pi}\int_{[-j,j]}\!\widehat f(y)\left(1-\frac{|y|}j\right)e^{ixy}\,d\lambda(y)$$

converge to $f$ in $L^1(\bb R)$ as $j\to\infty$, ie.

$$\lim_{j\to\infty}\|H_j-f\|_ p=0.\ \qed$$