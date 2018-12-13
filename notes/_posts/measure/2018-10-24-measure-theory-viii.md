---
title: 'Measure Theory (VIII): The Lebesgue Measure on $\bb R^n$'
layout: post
tag: [measure theory]
date: 2018-10-24 10:37:13 +0800
---

One of the most important applications of the Carathéodory construction of measures is to extend the notion of "length" or "volume" in $\bb R^n$ to the __Lebesgue measure__, yielding a more powerful integration theory. In this post, we cover the basic properties of the Lebesgue measure.
<!--more-->

## The Lebesgue measure

Recall that for $a=(a_1,\ldots,a_n)$, $b=(b_1,\ldots,b_n)$, with $-\infty\leq a_k\leq b_k\leq\infty$, the [__half-open interval__]({% post_url 2018-09-11-measure-theory-i %}) in $\bb R^n$ is the set

$$[a,b)=[a_1,b_1)\times\cdots\times[a_n,b_n)\subseteq\bb R^n.$$

We write $\mc H_n$ for the collection of all half-open intervals in $\bb R^n$. We have shown that $\mc H_n$ generates the Borel $\sigma$-algebra, ie. $\sigma(\mc H_n)=\mc B_n$.

Define $\lambda_0:\mc H_n\to[0,\infty]$ by

$$\lambda_0[a,b)=\prod_{k=1}^n(b_k-a_k).$$

Then the Carathéodory construction gives the __Lebesgue outer measure__ $\lambda^* $ on $\bb R^n$, which is given by

$$\lambda^* (A)=\inf\left\{\sum_{k=1}^\infty\lambda_0(I_k)\,:\,I_k\in\mc H_n,\,A\subseteq\bigcup_{k=1}^\infty I_k\right\}.$$

The $\lambda^* $-measurable sets, called __Lebesgue measurable sets__, form a $\sigma$-algebra $\Sigma$, and the corresponding measure $\lambda=\lambda^* \vert_\Sigma$ is called the __Lebesgue measure__ on $\bb R^n$. As we have shown in the [previous post]({% post_url 2018-10-23-measure-theory-vii %}), $(\bb R^n,\Sigma,\lambda)$ is a complete measure space.

We now consider some elementary properties of the Lebesgue measure. For any $A\subseteq\bb R^n$, $x\in\bb R^n$, and $c\in\bb R\backslash\\{0\\}$, define

$$\begin{aligned}
A+x&=\{\omega+x\,:\,\omega\in A\},\\
cA&=\{c\omega\,:\,\omega\in A\}.
\end{aligned}$$

Geometrically, these operations are translation by $x$ and scaling by $c$, respectively. We first show that the Lebesgue measure is translation-invariant and homogeneous under scaling.

__Proposition__: Let $A\subseteq\bb R^n$, $x\in\bb R^n$, and $c>0$. Then

$$\begin{aligned}
\lambda^* (A+x)&=\lambda^* (A),\\
\lambda^* (cA)&=c^n\lambda^* (A).
\end{aligned}$$

__Proof__: First note that for all $I\in\mc H_n$, we have

$$\begin{aligned}
\lambda_0(I+x)&=\lambda_0(I),\\
\lambda_0(cI)&=c^n\lambda_0(I).
\end{aligned}$$

Let $(I_k)$ be a countable covering of $A$ with half-open intervals. Then $(I_k+x)$ and $(cI_k)$ are coverings of $A+x$ and $cA$, respectively. Hence

$$\begin{aligned}
\lambda^* (A+x)&\leq\sum_k\lambda_0(I_k+x)\\
&=\sum_k\lambda_0(I_k),\\
\lambda^* (cA)&\leq\sum_k\lambda_0(cI_k)\\
&=c^n\sum_k\lambda_0(I_k).
\end{aligned}$$

Taking infimum over all $(I_k)$ gives

$$\begin{aligned}
\lambda^* (A+x)&\leq\lambda^* (A),\\
\lambda^* (cA)&\leq c^n\lambda^* (A).
\end{aligned}$$

Now the same argument with $-x$ replacing $x$ and $\frac1c$ replacing $c$ gives

$$\begin{aligned}
\lambda^* (A+x)&\geq\lambda^* ((A+x)-x)\\
&=\lambda^* (A),\\
\lambda^* (cA)&\geq c^n\lambda^* (\frac1c(cA))\\
&=\lambda^* (A),
\end{aligned}$$

and we are done. $\qed$

__Corollary__: Let $A\subseteq\bb R^n$, $x\in\bb R^n$, and $c>0$. Then $A$ is Lebesgue measurable if and only if $A+x$ is Lebesgue measurable, if and only if $cA$ is Lebesgue measurable.

__Proof__: If $A$ is Lebesgue measurable, then for any $S\subseteq\bb R^n$, we have

$$\begin{aligned}
\lambda^* (S)&=\lambda^* (S-x)\\
&=\lambda^* ((S-x)\cap A)+\lambda^* ((S-x)\cap A^c)\\
&=\lambda^* (S\cap(A+x))+\lambda^* (S\cap(A+x)^c),
\end{aligned}$$

so $A+x$ is Lebesgue measurable. Conversely, if $A+x$ is Lebesgue measurable, then replacing $x$ by $-x$ gives $(A+x)-x=A$ is measurable.

Similarly,

$$\begin{aligned}
\lambda^* (S)&=c^n\lambda^* (\frac1cS)\\
&=c^n(\lambda^* ((\frac1cS)\cap A)+\lambda^* ((\frac1cS)\cap A^c))\\
&=\lambda^* (S\cap(cA))+\lambda^* (S\cap(cA)^c),
\end{aligned}$$

so $cA$ is Lebesgue measurable. Conversely, if $cA$ is Lebesgue measurable, then replacing $c$ by $\frac1c$ gives $\frac1c(cA)=A$ is measurable. $\qed$

__Corollary__: Let $f:\bb R^n\to[-\infty,\infty]$, $x\in\bb R^n$, and $c>0$. Define $g(\omega)=f(\omega-x)$ and $h(\omega)=f(\frac\omega c)$. Then:
1. $f$ is Lebesgue measurable if and only if $g$ is Lebesgue measurable, if and only if $h$ is Lebesgue measurable;
2. $f$ is Lebesgue integrable if and only if $g$ is Lebesgue integrable, if and only if $h$ is Lebesgue integrable, in which case we have

$$\int\!g\,d\lambda=\int\!f\,d\lambda,\qquad\int\!h\,d\lambda=c^n\int\!f\,d\lambda.$$

__Proof__: (1): This follows from $g^{-1}(a,\infty]=f^{-1}(a,\infty]+x$ and $h^{-1}(a,\infty]=cf^{-1}(a,\infty]$.

(2): Note that $g^\pm(\omega)=f^\pm(\omega-x)$ and $h^\pm(\omega)=f^\pm(\frac\omega c)$. Hence it suffices to prove the identity for $f\geq0$.

For any sequence of step functions $0\leq\varphi_1\leq\varphi\leq\cdots$ with $(\varphi_k)\to f$, let $\psi_k(\omega)=\varphi_k(\omega-x)$. Then $0\leq\psi_1\leq\psi_2\leq\cdots$ is a sequence of step functions with $(\psi_k)\to g$. Now

$$\begin{aligned}
\int\!\psi_k\,d\lambda&=\sum_ja_j\lambda(\psi_k^{-1}(a_j))\\
&=\sum_ja_j\lambda(\varphi_k^{-1}(a_j)+x)\\
&=\sum_ja_j\lambda(\varphi_k^{-1}(a_j))\\
&=\int\!\varphi_k\,d\lambda.
\end{aligned}$$

Taking $k\to\infty$ gives $\int\\!g\,d\lambda=\int\\!f\,d\lambda$.

Similarly, let $\eta_k(\omega)=\varphi_k(\frac\omega c)$, so $0\leq\eta_1\leq\eta_2\leq\cdots$ is a sequence of step functions with $(\eta_k)\to h$. Now

$$\begin{aligned}
\int\!\eta_k\,d\lambda&=\sum_ja_j\lambda(\eta_k^{-1}(a_j))\\
&=\sum_ja_j\lambda(c\varphi_k^{-1}(a_j))\\
&=c^n\sum_ja_j\lambda(\varphi_k^{-1}(a_j))\\
&=c^n\int\!\varphi_k\,d\lambda.
\end{aligned}$$

Taking $k\to\infty$ gives $\int\\!h\,d\lambda=c^n\int\\!f\,d\lambda$. $\qed$

Note that we have omitted the case of $c<0$: the main problem here is that $I\in\mc H_n$ does not imply that $-I=(-1)I\in\mc H_n$. To deal with this case, we will need stronger theorems about the structure of Lebesgue measurable sets, which we will cover in the next post.

## Half-open intervals

Due to the indirect nature of the Carathéodory construction, it is not obvious that the Lebesgue measure $\lambda$ on half-open intervals corresponds to their volume $\lambda_0$; indeed, it is not obvious that half-open intervals are ($\lambda^* $-)measurable at all! The proof of these two statements are technical, and will take up the rest of the post.

__Lemma__: Let $I,I_1,I_2,\ldots,I_n\in\mc H_n$ be half-open intervals.
1. If $I$ is the disjoint union of $I_1,\ldots,I_m$, then

   $$\lambda_0(I)=\sum_{k=1}^m\lambda_0(I_k).$$

2. If $I$ is contained in the (not necessarily disjoint) union of $I_1,\ldots,I_m$, then

   $$\lambda_0(I)\leq\sum_{k=1}^m\lambda_0(I_k).$$

{% comment %}
<!-- This is certainly true in dimension 1: any decomposition of $[a,b)$ must be of the form

$$[a,b)=[a,x_1)\cup[x_1,x_2)\cup\cdots\cup[x_{m-1},b),$$

up to rearrangement, and clearly

$$b-a=(x_1-a)+(x_2-x_1)+\cdots+(b-x_{m-1}).$$

For general dimension $n$, --> 
{% endcomment %}
__Proof__: (1): Consider the special case of a "product partition" of the form

$$[a,b)=\bigcup_{i_1=0}^{m_1-1}\cdots\bigcup_{i_n=0}^{m_n-1}[x^1_{i_1},x^1_{i_1+1})\times\cdots\times[x^n_{i_n},x^n_{i_n+1}),$$

where $a_k=x^k_0< x^k_1<\cdots< x^k_{m_k}=b_k$. Writing the half-open intervals in the partition as $S_{i_1\ldots i_n}$, we have

$$\begin{aligned}
\sum_{i_1,\ldots,i_n}\lambda_0(S_{i_1\ldots i_n})&=\sum_{i_1,\ldots,i_n}(x^1_{i_1+1}-x^1_{i_1})\cdots(x^n_{i_n+1}-x^1_{i_n})\\
&=\left(\sum_{i_1}(x^1_{i_1+1}-x^1_{i_1})\right)\cdots\left(\sum_{i_n}(x^n_{i_n+1}-x^1_{i_n})\right)\\
&=(b_1-a_1)\cdots(b_n-a_n)\\
&=\lambda_0[a,b),
\end{aligned}$$

so the statement holds in this special case.

For a general partition of $I=[a,b)$, we "extend the sides" of each half-open interval to get a sub-partition of $I$, as follows. For each $k$, list all lower and upper endpoints of the $k$-th coordinates of every $I_j$, and arrange them in increasing order as $a_k=x^k_0< x^k_1<\cdots< x^k_{m_k}=b_k$.

Now consider the product partition of $I$ associated to these $x^k_i$; by the special case, we have

$$\sum_{i_1,\ldots,i_n}\lambda_0(S_{i_1\ldots i_n})=\lambda_0(I).$$

On the other hand, note that for each $I_j$, the $S_{i_1\ldots i_n}$ which intersect $I_j$ also form a product partition of $I_j$, and each $S_{i_1\ldots i_n}$ is contained in exactly one $I_j$. Hence

$$\lambda_0(I)=\sum_{i_1,\ldots,i_n}\lambda_0(S_{i_1\ldots i_n})=\sum_j\lambda_0(I_j),$$

and we are done.

(2): Without loss of generality, we may replace $I_j$ by $I\cap I_j$. Then the same operation as above gives a product partition of $I$<!-- , so $\sum\lambda_0(S_{i_1\ldots i_n})=\lambda_0(I)$ -->. However, now each $S_{i_1\ldots i_n}$ is contained in at least one $I_j$, so

$$\lambda_0(I)=\sum_{i_1,\ldots,i_n}\lambda_0(S_{i_1\ldots i_n})\leq\sum_j\lambda_0(I_j),$$

as desired. $\qed$

__Proposition__: For any half-open interval $I\in\mc H_n$, we have $\lambda^* (I)=\lambda_0(I)$.

__Proof__: We first consider the case where $I$ is finite, ie. bounded. Since $\\{I\\}$ is a covering of $I$ by half-open intervals, we have $\lambda^* (I)\leq\lambda_0(I)$; in particular, $\lambda^* (I)<\infty$. Hence, we only need to consider countable coverings $(I_k)$ of $I$ by half-open intervals where $\sum_k\lambda_0(I_k)<\infty$; this implies that each $I_k$ is finite.

Fix $\eps>0$. By shrinking $I$ slightly, we can get $I'\in\mc H_n$ such that $I\supseteq\overline{I'}$, the closure of $I'$, and

$$\lambda_0(I')\geq\lambda_0(I)-\eps.$$

Similarly, by enlarging $I_k$ slightly, we can get $I_k'\in\mc H_n$ such that $I_k\subseteq I_k'^\circ$, the interior of $I_k'$, and

$$\lambda_0(I_k')\leq\lambda_0(I_k)+\frac\eps{2^k}.$$

Now $(I_k')$ is an open covering of the compact set $I'$, so it has a finite subcovering, say $I_{k_1}'\cup\cdots\cup I_{k_m}'$. By the previous lemma, we have

$$\begin{aligned}
\lambda_0(I)&\leq\lambda_0(I')+\eps\\
&\leq\sum_{i=1}^m\lambda_0(I_{k_i}')+\eps\\
&\leq\sum_{k=1}^\infty\lambda_0(I_k)+2\eps,
\end{aligned}$$

and taking $\eps\to0^+$ gives $\sum_k\lambda_0(I_k)\geq\lambda_0(I)$. Now taking infimum over all $(I_k)$ gives $\lambda^* (I)\geq\lambda_0(I)$, as desired.

Now suppose that $I=[a,b)$ is not finite, say $b_k=\infty$ (the argument for $a_k=-\infty$ is analogous). Then

$$S=[a_1,b_1)\times\cdots\times[a_k,a_k+N)\times\cdots\times[a_n,b_n)$$

is contained in $I$, so

$$\lambda^* (I)\geq\lambda^* (S)=N\prod_{i\neq k}(b_i-a_i).$$

Taking $N\to\infty$ gives $\lambda^* (I)=\infty=\lambda_0(I)$, and we are done. $\qed$


__Proposition__: Every half-open interval $I\in\mc H_n$ is Lebesgue measurable.

__Proof__: We need to show that

$$\lambda^* (S)\geq\lambda^* (S\cap I)+\lambda^* (S\cap I^c)$$

for any $S\subseteq\bb R^n$. If $\lambda^* (S)=\infty$ there is nothing to prove, so assume that $\lambda^* (S)<\infty$.

Fix $\eps>0$, and take a countable cover $(R_k)$ of $S$ by half-open intervals, such that

$$\sum_{k=1}^\infty\lambda_0(R_k)\leq\lambda^* (S)+\eps.$$

Note that each $R_k$ can be written as the disjoint union of finitely many half-open intervals,

$$R_k=\tilde R_k\cup\bigcup_{i=1}^NS_k^i,$$

where $\tilde R_k=R_k\cap I$, by "extending the sides" into a product partition. By the lemma, we have

$$\lambda_0(R_k)=\lambda_0(\tilde R_k)+\sum_{i=1}^N\lambda_0(S_k^i),$$

so

$$\begin{aligned}
\lambda^* (S)+\eps&\geq\sum_{k=1}^\infty\lambda_0(R_k)\\
&=\sum_{k=1}^\infty\lambda_0(\tilde R_k)+\sum_{k=1}^\infty\sum_{i=1}^N\lambda_0(S_k^i)\\
&\geq\lambda^* (S\cap I)+\lambda^* (S\cap I^c),
\end{aligned}$$

since $(\tilde R_k)$ cover $S\cap I$ and $(S_k^i)$ cover $S\cap I^c$. Taking $\eps\to0^+$ gives

$$\lambda^* (S)\geq\lambda^* (S\cap I)+\lambda^* (S\cap I^c),$$

as desired. $\qed$

__Corollary__: Every Borel subset of $\bb R^n$ is Lebesgue measurable.

__Proof__: Since the collection $\Sigma$ of all Lebesgue measurable sets is a $\sigma$-algebra, $\mc H_n\subseteq\Sigma$ implies $\mc B_n=\sigma(\mc H_n)\subseteq\Sigma$. $\qed$