---
title: 'Measure Theory (XVII): Functions of Bounded Variation'
layout: post
tag: [measure theory]
date: 2018-11-23 18:30:01 +0800
---

In the buildup to the analogues of the Fundamental Theorem of Calculus for the Lebesgue integral on $\bb R$, we study two special classes of functions, namely monotone functions and functions of bounded variation. In particular, we look at the derivatives $f'$ and their Lebesgue integrals $\int\\!f'\,d\lambda$, and relate them to the original function $f$.

<!--more-->

## Derivative of monotone functions

Given a function $f:(a,b)\to\bb R$, its __lower and upper derivatives__ are defined respectively as

$$\begin{aligned}
\underline Df(x)&=\liminf_{y\to x}\frac{f(y)-f(x)}{y-x},\\
\overline Df(x)&=\limsup_{y\to x}\frac{f(y)-f(x)}{y-x}.
\end{aligned}$$

Then $\underline Df\leq\overline Df$, and $f$ is differentiable at $x$ if and only if $\underline Df(x)=\overline Df(x)$ is a finite value.

__Lemma__: Let $f:(a,b)\to\bb R$ be a nondecreasing function, and let $\alpha>0$. Then

$$\lambda^* \{x\in(a,b)\,:\,\overline Df(x)>\alpha\}\leq\frac{f(b)-f(a)}\alpha.$$

__Proof__: Let $E_\alpha=\\{x\in(a,b)\,:\,\overline Df(x)>\alpha\\}$. Then for any $x\in E_\alpha$ and $\delta>0$, there exists $0<\lvert h\rvert<\delta$ with

$$\frac{f(x+h)-f(x)}h\geq\alpha.$$

Hence the collection of closed intervals

$$\mc I=\left\{[c,d]\subseteq(a,b)\,:\,\frac{f(d)-f(c)}{d-c}\geq\alpha\right\}$$

is a Vitali cover of $E_\alpha$.

Fix $\eps>0$. By Vitali's covering theorem, there is a finite subcollection of pairwise disjoint intervals in $\mc I$, say $([c_k,d_k] )_ {k=1}^n$, with

$$\lambda^* \left(E_\alpha\backslash\bigcup_{k=1}^n[c_k,d_k]\right)<\eps.$$

Now $f$ is nondecreasing implies

$$\sum_{k=1}^n(d_k-c_k)\leq\frac1\alpha\sum_{k=1}^n(f(d_k)-f(c_k))\leq\frac{f(b)-f(a)}\alpha,$$

so

$$\begin{aligned}
\lambda^* (E_\alpha)&\leq\lambda^* \left(E_\alpha\backslash\bigcup_{k=1}^n[c_k,d_k]\right)+\lambda^* \left(\bigcup_{k=1}^n[c_k,d_k]\right)\\
&<\eps+\frac{f(b)-f(a)}\alpha.
\end{aligned}$$

Taking $\eps\to0^+$ gives the desired result. $\qed$

__Corollary__: Let $f:(a,b)\to\bb R$ be a nondecreasing function, and let $\alpha>0$. Then

$$\lambda\{x\in(a,b)\,:\,\overline Df(x)=\infty\}=0.$$

__Proof__: With $E_\alpha$ as defined in the previous proof, the result follows from

$$\{x\in(a,b)\,:\,\overline Df(x)=\infty\}=\bigcap_{\alpha=1}^\infty E_\alpha.\ \qed$$

The following is Lebesgue's theorem on the differentiability of monotone functions.

__Theorem__: Let $I$ be an interval in $\bb R$, and let $f:I\to\bb R$ be monotone. Then $f$ is differentiable $\lambda$-a.e. on $I$.

__Proof__: It suffices to prove the statement when $I=(a,b)$ is a bounded open interval (if $I$ is unbounded, partition it into countably many pieces; if $I$ is closed, we can ignore its endpoints, since they are of measure $0$), and $f$ is nondecreasing (otherwise replace $f$ by $-f$).

Fix $\eps>0$. For $s,t\in\bb R$ with $s< t$, define

$$A_{s,t}=\left\{x\in(a,b)\,:\,\underline Df(x)< s,\,\overline Df(x)>t\right\},$$

and take an open set $O\subseteq(a,b)$ with $A_{s,t}\subseteq O$ and $\lambda(O)<\lambda^* (A_{s,t})+\eps$.

Now consider the collection of closed intervals

$$\mc I=\left\{[c,d]\subseteq O\,:\,\frac{f(d)-f(c)}{d-c}\leq s\right\}.$$

By an analogous argument to that used in the Lemma, this is a Vitali cover of $A_{s,t}$.

Since $\lambda^* (A_{s,t})\leq b-a<\infty$, by Vitali's covering theorem there is a finite subcollection of pairwise disjoint intervals in $\mc I$, say $([c_k,d_k] )_ {k=1}^n$, with

$$\lambda^* \left(A_{s,t}\backslash\bigcup_{k=1}^n[c_k,d_k]\right)<\eps.$$

But by the Lemma above, we have

$$\lambda^* (A_{s,t}\cap[c_k,d_k])\leq\frac{f(d_k)-f(c_k)}t\leq\frac st(d_k-c_k).$$

Hence

$$\begin{aligned}
\lambda^* (A_{s,t})&<\eps+\frac st\sum_{k=1}^n(d_k-c_k)\\
&\leq\eps+\frac st\lambda(O)\\
&\leq\eps+\frac st(\lambda^* (A_{s,t})+\eps).
\end{aligned}$$

Taking $\eps\to0^+$ gives $\lambda^* (A_{s,t})\leq\frac st\lambda^* (A_{s,t})$, which implies $\lambda(A_{s,t})=0$.

To finish, note that $f$ is not differentiable at $x$ if and only if there exists $s,t\in\bb Q$ with

$$\underline Df(x)< s< t<\overline Df(x).$$

Thus $f$ is not differentiable only on the set $\bigcup_{s,t\in\bb Q}A_{s,t}$, which is a countable union of Lebesgue-null sets, and is hence Lebesgue-null. Hence $f$ is differentiable $\lambda$-a.e. $\qed$

__Proposition__: Let $f:[a,b]\to\bb R$ be a nondecreasing function, and let

$$g(x)=\begin{cases}f'(x),&f\text{ differentiable at }x\\0,&\text{otherwise}.\end{cases}$$

Then $g\geq0$, and

$$\int_{[a,b]}\!g\,d\lambda\leq f(b)-f(a).$$

__Proof__: By the previous theorem, $f$ is differentiable $\lambda$-a.e. Hence the functions

$$f_n(x)=\begin{cases}\frac{f(x+\frac1n)-f(x)}{\frac1n},&a\leq x\leq b-\frac1n\\0,&b-\frac1n< x\leq b\end{cases}$$

converge pointwise to $g$ for $\lambda$-a.e. $x\in[a,b]$. Now Fatou's theorem gives

$$\begin{aligned}
\int_{[a,b]}\!g\,d\lambda&\leq\liminf_{n\to\infty}\int_{[a,b-\frac1n]}\!f_n\,d\lambda\\
&=n\liminf_{n\to\infty}\left(\int_{[a+\frac1n,b]}-\int_{[a,b-\frac1n]}\right)f\,d\lambda\\
&=n\liminf_{n\to\infty}\left(\int_{[b-\frac1n,b]}-\int_{[a,a+\frac1n]}\right)f\,d\lambda\\
&\leq n\liminf_{n\to\infty}\left(\int_{[b-\frac1n,b]}\!f(b)\,d\lambda-\int_{[a,a+\frac1n]}\!f(a)\,d\lambda\right)\\
&=\liminf_{n\to\infty}(f(b)-f(a))\\
&=f(b)-f(a),
\end{aligned}$$

as desired. $\qed$

## Functions of bounded variation

$\gdef{\Var}{\operatorname{Var}}$

Let $f:[a,b]\to\bb R$. The __total variation__ of $f$ on $[a,b]$ is

$$\Var_{[a,b]}f=\sup\left\{\sum_{j=1}^k|f(x_j)-f(x_{j-1})|\,:\,a=x_0< x_1<\cdots< x_k=b\right\}.$$

We say that $f$ is __of bounded variation__ on $[a,b]$ if $\Var_{[a,b]}f<\infty$. These form a family of well-behaved functions; for instance, since

$$\begin{aligned}
&\quad|f(x_k)-f(x_{k-1})|\\
&\leq\sqrt{(x_k-x_{k-1})^2+(f(x_k)-f(x_{k-1}))^2}\\
&\leq|x_k-x_{k-1}|+|f(x_k)-f(x_{k-1})|,
\end{aligned}$$

we see that $f$ is of bounded variation if and only if the graph $y=f(x)$ is a curve of finite length, in which case its length lies between $\Var_{[a,b]}f$ and $b-a+\Var_{[a,b]}f$.

Note that functions of bounded variation are necessarily bounded: for all $x\in[a,b]$, we have

$$\begin{aligned}
|f(x)|&\leq|f(a)|+|f(x)-f(a)|\\
&\leq|f(a)|+\Var_{[a,b]}f.
\end{aligned}$$

We give some examples of functions of bounded variation.

__Proposition__: Let $f:[a,b]\to\bb R$ be monotone. Then $f$ is of bounded variation, with $\Var_{[a,b]}f=\lvert f(b)-f(a)\rvert$. $\qed$

__Proposition__: Let $f\in L^1[a,b]$, and define $F:[a,b]\to\bb R$ by $F(x)=\int_a^x\\!f\,d\lambda$. Then $F$ has bounded variation on $[a,b]$.

__Proof__: Note that for any partition $\\{x_k\\}_ {k=0}^n$ of $[a,b]$, we have

$$\begin{aligned}
\sum_{j=1}^k|F(x_j)-F(x_{j-1})|&=\sum_{j=1}^k\left|\int_{x_{j-1}}^{x_j}f\,d\lambda\right|\\
&\leq\sum_{j=1}^k\int_{x_{j-1}}^{x_j}|f|\,d\lambda\\
&=\|f\|_ 1.
\end{aligned}$$

Hence $\Var_{[a,b]}F\leq\\|f\\|_ 1<\infty$. $\qed$

Given some functions of bounded variation, we can easily construct new ones:

__Proposition__: If $f,g:[a,b]\to\bb R$ are of bounded variation and $c\in\bb R$, then $f+g$, $cf$ and $fg$ are of bounded variation on $[a,b]$.

__Proof__: For any partition $\\{x_k\\}_ {k=0}^n$ of $[a,b]$, we have

$$\begin{aligned}
&\quad\sum_{k=1}^n|(f+g)(x_k)-(f+g)(x_{k-1})|\\
&\leq\sum_{k=1}^n|f(x_k)-f(x_{k-1})|+|g(x_k)-g(x_{k-1})|\\
&\leq\Var_{[a,b]}f+\Var_{[a,b]}g,
\end{aligned}$$

so $\Var_{[a,b]}(f+g)\leq\Var_{[a,b]}f+\Var_{[a,b]}g<\infty$, ie. $f+g$ is of bounded variation.

Let $\sup_{[a,b]}\lvert f\rvert=M<\infty$. Then

$$\begin{aligned}
&\quad\sum_{k=1}^n|f(x_k)^2-f(x_{k-1})^2|\\
&=\sum_{k=1}^n|f(x_k)-f(x_{k-1})||f(x_k)+f(x_{k-1})|\\
&\leq2M\sum_{k=1}^n|f(x_k)-f(x_{k-1})|\\
&\leq2M\Var_{[a,b]}f,
\end{aligned}$$

so $\Var_{[a,b]}f^2\leq2M\Var_{[a,b]}f<\infty$, ie. $f^2$ is of bounded variation whenever $f$ is of bounded variation. Hence

$$fg=\frac{(f+g)^2-f^2-g^2}2$$

is also of bounded variation. In particular, since the constant function $c$ has bounded variation, $cf$ is of bounded variation. $\qed$

Now we give some elementary properties of the variation function.

__Proposition__: Let $f:[a,b]\to\bb R$ be of bounded variation. Then:
1. $\Var_{[a,b]}f\geq\lvert f(b)-f(a)\rvert$;
2. $\Var_{[a,b]}f=\Var_{[a,c]}f+\Var_{[c,b]}f$ for any $c\in[a,b]$.

__Proof__: (1) is clear by taking the trivial partition $\\{a,b\\}$.

(2): For any partitions $\\{y_k\\}_ {k=0}^{n'}$ and $\\{z_l\\}_ {l=0}^{n''}$ of $[a,c]$ and $[c,b]$ respectively, their union forms a partition $\\{x_j\\}_ {j=0}^n$ of $[a,b]$, with

$$\sum_{j=0}^n|f(x_j)-f(x_{j-1})|=\sum_{k=0}^{n'}|f(y_k)-f(y_{k-1})|+\sum_{l=0}^\infty|f(z_l)-f(z_{l-1})|.$$

Taking suprema over $\\{y_k\\}$, $\\{z_l\\}$ gives $\Var_{[a,b]}f\geq\Var_{[a,c]}f+\Var_{[c,b]}f$.

On the other hand, for any partition $\\{x_j\\}_ {j=0}^n$ of $[a,b]$, we can insert the point $c$ and split it into partitions $\\{y_k\\}_ {k=0}^{n'}$ and $\\{z_l\\}_ {l=0}^{n''}$ of $[a,c]$ and $[c,b]$ respectively. Then

$$\sum_{j=0}^n|f(x_j)-f(x_{j-1})|\leq\sum_{k=0}^{n'}|f(y_k)-f(y_{k-1})|+\sum_{l=0}^\infty|f(z_l)-f(z_{l-1})|.$$

(The sum might increase since we might have split a subinterval of the partition when inserting the point $c$.) Taking supremum over $\\{x_j\\}$ gives $\Var_{[a,b]}f\leq\Var_{[a,c]}f+\Var_{[c,b]}f$. $\qed$

The next result is a useful characterisation of functions of bounded variation:

__Theorem__: Let $f:[a,b]\to\bb R$. Then $f$ is of bounded variation if and only if there exists nondecreasing functions $f_1,f_2:[a,b]\to\bb R$ such that $f=f_1-f_2$. Moreover, $f_1,f_2$ may be chosen such that

$$\Var_{[a,b]}f=f_1(b)-f_1(a)+f_2(b)-f_2(a).$$

__Proof__: By the previous proposition, for all $a\leq x\leq y\leq b$ we have

$$\begin{aligned}
\Var_{[a,y]}f+f(y)&=\Var_{[a,x]}f+\Var_{[x,y]}f+f(y)\\
&\geq\Var_{[a,x]}f+(f(x)-f(y))+f(y)\\
&=\Var_{[a,x]}f+f(x),\\
\Var_{[a,y]}f-f(y)&=\Var_{[a,x]}f+\Var_{[x,y]}f-f(y)\\
&\geq\Var_{[a,x]}f+(f(y)-f(x))-f(y)\\
&=\Var_{[a,x]}f-f(x).
\end{aligned}$$

Write $V(x)=\Var_{[a,x]}f$, and let

$$f_1=\frac12(V+f),\qquad f_2=\frac12(V-f).$$

By the above computation, $f_1$ and $f_2$ are nondecreasing functions with $f=f_1-f_2$ and $V=f_1+f_2$. Hence

$$\begin{aligned}
\Var_{[a,b]}f&=V(b)-V(a)\\
&=f_1(b)-f_1(a)+f_2(b)-f_2(a),
\end{aligned}$$

as desired. $\qed$

Combined with Lebesgue's theorem on the differentiability of monotone functions, we have:

__Theorem__: Let $f:[a,b]\to\bb R$ be of bounded variation. Then:
- $f$ is differentiable $\lambda$-a.e. on $[a,b]$;
- The function

  $$g(x)=\begin{cases}f'(x),&f\text{ differentiable at }x\\0,&\text{otherwise}\end{cases}$$

  is Lebesgue integrable on $[a,b]$; and
- $\int_{[a,b]}\\!\lvert g\rvert\,d\lambda\leq\Var_{[a,b]}f$.

__Proof__: Write $f=f_1-f_2$, where $f_1,f_2$ are nondecreasing functions, hence differentiable $\lambda$-a.e.; hence $f$ is also differentiable $\lambda$-a.e. Now define

$$g_1(x)=\begin{cases}f_1'(x),&f\text{ differentiable at }x\\0,&\text{otherwise},\end{cases}$$

and $g_2$ similarly. Then $g=g_1-g_2$ $\lambda$-a.e., so

$$\begin{aligned}
\int_{[a,b]}\!|g|\,d\lambda&\leq\int_{[a,b]}\!|g_1|\,d\lambda+\int_{[a,b]}\!|g_1|\,d\lambda\\
&\leq f_1(b)-f_1(a)+f_2(b)-f_2(a)\\
&=\Var_{[a,b]}f,
\end{aligned}$$

and we are done. $\qed$