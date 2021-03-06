---
title: 'Algebraic Number Theory (IV): Number Rings'
layout: post
date: 2019-02-10 10:16:43 +0800
tag: [algebraic number theory]
series-order: 4
macros: >-
  "\\disc":"\\operatorname{disc}",
---

In the [previous post]({% post_url 2019-02-08-algebraic-number-theory-iii %}), we proved that the set of algebraic integers $\bb A\cap K$ in any number field $K$ forms a ring, known as the __number ring__ corresponding to $K$. In this post, we study number rings in more detail.

<!--more-->

## Discriminant of an $n$-tuple

Let $K$ be a number field of degree $n$ over $\bb Q$, and let $\sigma_1,\ldots,\sigma_n$ be the $n$ embeddings of $K$ into $\bb C$. Then for any $\alpha_1,\ldots,\alpha_n\in K$, define the __discriminant__ of this $n$-tuple to be

$$\disc(\alpha_1,\ldots,\alpha_n)=\left[\det(\sigma_i(\alpha_j))_ {i,j}\right]^2.$$

Note that the determinant in RHS is well-defined up to sign, depending on the ordering of $\sigma_i$ and $\alpha_j$; hence the discriminant is independent of these orderings.

__Proposition__: For any $\alpha_1,\ldots,\alpha_n\in K$, we have

$$\disc(\alpha_1,\ldots,\alpha_n)=\det(T(\alpha_i\alpha_j))_ {i,j}.$$

__Proof__: Note that $\disc(\alpha_1,\ldots,\alpha_n)$ is the determinant of the product

$$\begin{aligned}
(\sigma_j(\alpha_i))_ {i,j}(\sigma_i(\alpha_j))_ {i,j}&=(\sigma_1(\alpha_i\alpha_j)+\cdots+\sigma_n(\alpha_i\alpha_j))_ {i,j}\\
&=(T(\alpha_i\alpha_j))_ {i,j},
\end{aligned}$$

as desired. $\qed$

__Corollary__: Let $\alpha_1,\ldots,\alpha_n\in K$. Then:
1. $\disc(\alpha_1,\ldots,\alpha_n)\in\bb Q$; 
2. If all $\alpha_i$ are algebraic integers, then $\disc(\alpha_1,\ldots,\alpha_n)\in\bb Z$. $\qed$

Since the discriminant of an $n$-tuple is (the square of) the determinant of some matrix, we expect that there is special significance to the condition $\disc(\alpha_1,\ldots,\alpha_n)=0$. Indeed, we have the following:

__Proposition__: Let $\alpha_1,\ldots,\alpha_n\in K$. Then $\disc(\alpha_1,\ldots,\alpha_n)=0$ if and only if $\\{\alpha_1,\ldots,\alpha_n\\}$ are linearly dependent over $\bb Q$.

__Proof__: ($\Leftarrow$) If $\sum_jq_j\alpha_j=0$ for some $q_j\in\bb Q$, not all zero, then

$$\sum_jq_j\sigma_i(\alpha_j)=0\quad\text{for all }i,$$

so the columns of the matrix $(\sigma_i(\alpha_j))_ {i,j}$ are linearly dependent. Hence this matrix has determinant $0$, so the discriminant of the $\alpha_j$ is also $0$.

($\Rightarrow$) We prove the contrapositive. Suppose $\\{\alpha_1,\ldots,\alpha_n\\}$ are linearly independent over $\bb Q$. Consider the matrix $(T(\alpha_i\alpha_j))_ {i,j}$, which has entries in $\bb Q$, and take any linear relation of its rows over $\bb Q$, say

$$\sum_iq_iT(\alpha_i\alpha_j)=0\quad\text{for all }j,$$

for some $q_i\in\bb Q$. Now if we define

$$\alpha=\sum_iq_i\alpha_i,$$

we have $T(\alpha\alpha_j)=0$ for all $j$. Since the $\alpha_j$ form a basis of $K$ over $\bb Q$, we have $T(\alpha\beta)=0$ for all $\beta\in K$. But $T(1)=n$, so $\alpha$ is not invertible in $K$, ie. $\alpha=0$. This implies that $q_i=0$ for all $i$. Hence the rows of $(T(\alpha_i\alpha_j))_ {i,j}$ are linearly independent over $\bb Q$, so its determinant is nonzero. $\qed$

## Free abelian groups of finite rank

At this point, we want to investigate the algebraic structure of number rings. To do this, we need to review some basic results in group theory. Recall that a __free abelian group of finite rank__ is a group isomorphic to $\bb Z^n$ for some integer $n\geq0$. In this case, we call $n$ the __rank__ of this group.

__Proposition__: If $\bb Z^n\cong\bb Z^m$ then $n=m$.

__Proof__: Any isomorphism between the two groups gives an isomorphism $\bb Z^n/2\bb Z^n\cong\bb Z^m/2\bb Z^m$. Now note that $\bb Z^n/2\bb Z^n$ is a $\bb Z/2\bb Z$-vector space of dimension $n$, so it has $2^n$ elements, and similarly for $m$. Hence $2^n=2^m$, so $n=m$. $\qed$

Thus the rank of a free abelian group of finite rank is uniquely determined.

__Theorem__: Any subgroup of $\bb Z^n$ is a free abelian group with rank at most $n$.

__Proof__: We proceed by induction on $n$. For $n=1$, note that the subgroups of $\bb Z$ are $k\bb Z\cong\bb Z$ for $k\geq1$, and $\\{0\\}\cong\bb Z^0$.

Suppose that the claim holds for $n-1$. Let $H\subseteq\bb Z^n$ be a subgroup, and let $\pi:\bb Z^n\to\bb Z$ denote the projection map onto the first coordinate, ie.

$$\pi(a_1,\ldots,a_n)=a_1.$$

Note that $\ker\pi\cong\bb Z^{n-1}$, so by induction hypothesis, $H\cap\ker\pi$ is a free abelian group of rank at most $n-1$.

Also, $\pi(H)$ is a subgroup of $\bb Z$. If $\pi(H)=\\{0\\}$ then $H=H\cap K$, and we are done. Otherwise, $\pi(H)\cong k\bb Z$ is generated by $k=\pi(h_0)$ for some $h_0\in H$.

Note that $\pi(ch_0)=ck$, so $\bb Zh_0\cap(H\cap\ker\pi)=\\{0\\}$. On the other hand, for any $h\in H$ we have $\pi(h)=ck=c\pi(h_0)$ for some $c\in\bb Z$, so $h-ch_0\in H\cap\ker\pi$ implies $H=\bb Zh_0+(H\cap\ker\pi)$. Hence

$$H=\bb Zh_0\oplus(H\cap\ker\pi),$$

so $H$ is a free abelian group with rank at most $n$. $\qed$

__Corollary__: If $G'\subseteq H\subseteq G$ are abelian groups such that $G'$ and $G$ are both free of rank $n$, then $H$ is also free of rank $n$. $\qed$

## The additive group of a number ring

Let $K$ be a number field of degree $n$ over $\bb Q$, and let $R=\bb A\cap K$ be the ring of algebraic integers in $K$. In this section, we show that the additive group of $R$ is in fact a free abelian group of rank $n$. From the previous result, it suffices to show that $R$ is "sandwiched" between two free abelian groups of rank $n$.

__Proposition__: For any algebraic number $\alpha$, there exists an integer $m\geq1$ such that $m\alpha$ is an algebraic integer.

__Proof__: If $\sum_{i=0}^ka_i\alpha^i=0$ for some $a_i\in\bb Z$, then

$$0=a_k^{k-1}\sum_{i=0}^ka_i\alpha^i=\sum_{i=0}^ka_k^{k-1-i}a_i(a_k\alpha)^i,$$

so $a_k\alpha$ is a root of the polynomial

$$X^k+a_{k-1}X^{k-1}+a_ka_{k-2}X^{k-2}+\cdots+a_k^{k-2}a_1X+a_k^{k-1},$$

which is monic and has integer coefficients. Hence we may take $m=a_k$. $\qed$

__Corollary__: $R$ contains an additive subgroup which is free of rank $n$.

__Proof__: Let $\\{\alpha_1,\ldots,\alpha_n\\}$ be a basis for $K$ over $\bb Q$. By replacing each $\alpha_i$ by an integer multiple, we may assume that all $\alpha_i$ are algebraic integers.

Since $0$ has only the trivial representation as a $\bb Q$-linear combination of the $\alpha_i$'s, $0$ also has only the trivial representation as a $\bb Z$-linear combination of the $\alpha_i$'s. This shows that the following sum is direct:

$$\begin{aligned}
A&=\left\{\sum_im_i\alpha_i\,:\,m_i\in\bb Z\text{ for all }i\right\}\\
&=\bb Z\alpha_1\oplus\cdots\oplus\bb Z\alpha_n
\end{aligned}$$

Hence $A$ is a free abelian group of rank $n$. Furthermore, all elements of $A$ are algebraic integers, so $A$ is a subgroup of the additive group of $R$. $\qed$

In the other direction, we have to show that $R$ is contained in some free abelian group of rank $n$. We will do this by using the discriminant.

__Theorem__: Let $\\{\alpha_1,\ldots,\alpha_n\\}$ be a basis for $K$ over $\bb Q$, such that each $\alpha_i$ is an algebraic integer. Let $d=\disc(\alpha_1,\ldots,\alpha_n)$. Then every $\alpha\in R$ can be written as

$$\alpha=\frac1d\sum_jm_j\alpha_j,$$

where $m_j\in\bb Z$ and $d\mid m_j^2$ for all $i$.

__Proof__: Firstly, note that $d\neq0$ because the $\alpha_j$ are linearly independent, and $d\in\bb Z$ since all $\alpha_j$ are algebraic integers.

Write $\alpha=\sum_jq_j\alpha_j$ for $q_j\in\bb Q$. Let $\sigma_1,\ldots,\sigma_n$ be the embeddings of $K$ in $\bb C$, so we have

$$\sigma_i(\alpha)=q_1\sigma_i(\alpha_1)+\cdots+q_n\sigma_i(\alpha_n)\quad\text{ for all }i.$$

We can solve this system of linear equations for $q_j$ by Cramer's rule: if $\delta$ is the determinant of $(\sigma_i(\alpha_j))_ {i,j}$, and $y_j$ is the determinant of the same matrix with the $j$-th column replaced by $\sigma_i(\alpha)$, then

$$q_j=\frac{y_j}\delta.$$

Since all entries of both matrices above are algebraic integers, we have $y_j$ and $\delta$ are algebraic integers.

Define $m_j=q_jd$, so that

$$\alpha=\sum_jq_j\alpha_j=\frac1d\sum_jm_j\alpha_j.$$

Moreover, $\delta^2=d$, so

$$m_j=q_jd=y_j\delta,$$

which is an algebraic integer (by RHS) in $\bb Q$ (by LHS), so $m_j\in\bb Z$. Finally, we have

$$\frac{m_j^2}d=q_j^2d=(q_j\delta)^2=y_j^2,$$

which is an algebraic integer (by RHS) in $\bb Q$ (by LHS), so $d\mid m_j^2$. $\qed$

__Corollary__: $R$ is contained in an additive subgroup which is free of rank $n$.

__Proof__: By the above theorem, we have

$$R\subseteq\frac1dA=\bb Z\frac{\alpha_1}d\oplus\cdots\oplus\bb Z\frac{\alpha_n}d,$$

as desired. $\qed$

Thus we immediately have:

__Theorem__: $R$ is a free abelian group of rank $n$. $\qed$

To state this more explicitly, there exists $\beta_1,\ldots,\beta_n\in R$ such that every $\alpha\in R$ can be uniquely written as

$$m_1\beta_1+\cdots+m_n\beta_n,\quad m_i\in\bb Z.$$

In this case, we call $\\{\beta_1,\ldots,\beta_n\\}$ an __integral basis__ for $R$, or a __basis for $R$ over $\bb Z$__.

For example, we have determined the number rings of quadratic number fields in the [previous post]({% post_url 2019-02-08-algebraic-number-theory-iii %}), namely

$$R=\bb A\cap\bb Q[\sqrt m]=\begin{cases}
\bb Z[\sqrt m],&\text{if }m\equiv2,3\pmod4,\\
\bb Z\left[\frac{1+\sqrt m}2\right],&\text{if }m\equiv1\pmod4.
\end{cases}$$

Hence $R$ has integral basis $\\{1,\sqrt m\\}$ when $m\equiv2,3\pmod4$, or $\\{1,\frac{1+\sqrt m}2\\}$ when $m\equiv1\pmod4$.

## Discriminant of a ring

It turns out that the discriminant of an integral basis is an invariant of the number ring:

__Proposition__: Let $\\{\beta_1,\ldots,\beta_n\\}$ and $\\{\gamma_1,\ldots,\gamma_n\\}$ be two integral bases for $R$. Then

$$\disc(\beta_1,\ldots,\beta_n)=\disc(\gamma_1,\ldots,\gamma_n).$$

__Proof__: Since each $\beta_i$ is a $\bb Z$-linear combination of the $\gamma_j$, we can write

$$\begin{pmatrix}\beta_1\\\vdots\\\beta_n\end{pmatrix}=M\begin{pmatrix}\gamma_1\\\vdots\\\gamma_n\end{pmatrix},$$

where $M$ is some $n\times n$ matrix with entries in $\bb Z$. Let $\sigma_1,\ldots,\sigma_n$ be the embeddings of $K$ in $\bb C$; by applying each $\sigma_j$ to the above equation, we have

$$(\sigma_j(\beta_i))_ {i,j}=M(\sigma_j(\gamma_i))_ {i,j}.$$

Taking determinants and squaring, we have

$$\disc(\beta_1,\ldots,\beta_n)=\det(M)^2\disc(\gamma_1,\ldots,\gamma_n).$$

Since $M$ has integer entries, $\det(M)^2$ is a positive integer. Hence $\disc(\gamma_1,\ldots,\gamma_n)$ divides $\disc(\beta_1,\ldots,\beta_n)$, and both discriminants have the same sign. But this is also true when we switch $\beta_i$ with $\gamma_i$, so the two discriminants are in fact equal. $\qed$

Hence all integral bases of $R$ have the same discriminant, which we can call the __discriminant of the number ring $R$__ and write as $\disc(R)$, or even the __discriminant of the number field $K$__ and write $\disc(K)$.

In fact, we can identify integral bases in $R$ by the discriminant alone.

__Proposition__: Let $\alpha_1,\ldots,\alpha_n\in R$. Then $\\{\alpha_1,\ldots,\alpha_n\\}$ form an integral basis for $R$ if and only if

$$\disc(\alpha_1,\ldots,\alpha_n)=\disc(R).$$

__Proof__: ($\Rightarrow$) By definition of $\disc(R)$.

($\Leftarrow$) Let $\\{\beta_1,\ldots,\beta_n\\}$ be any integral basis for $R$. Since each $\alpha_i$ is a $\bb Z$-linear combination of the $\beta_j$, we can write

$$\begin{pmatrix}\alpha_1\\\vdots\\\alpha_n\end{pmatrix}=M\begin{pmatrix}\beta_1\\\vdots\\\beta_n\end{pmatrix},$$

where $M$ is some $n\times n$ matrix with entries in $\bb Z$. As before, by applying each $\sigma_j$, taking determinants, and squaring, we have

$$\disc(\alpha_1,\ldots,\alpha_n)=\det(M)^2\disc(\beta_1,\ldots,\beta_n).$$

By hypothesis, we conclude $\det(M)=\pm1$, so $M^{-1}$ also has integer entries. Thus each $\beta_j$ is a $\bb Z$-linear combination of the $\alpha_i$; hence so is every element of $R$. Thus $\\{\alpha_1,\ldots,\alpha_n\\}$ form an integral basis for $R$. $\qed$

## Number rings of field compositions

Let $K,L$ be number fields of degree $m,n$ over $\bb Q$, respectively. Recall that the composite field $KL$ is the smallest subfield of $\bb C$ containing $K$ and $L$, and it consists of all finite sums of products of elements of $K$ with elements of $L$.

__Lemma__: Suppose that $[KL:\bb Q]=mn$. Then for any embeddings $\sigma,\tau$ of $K,L$ in $\bb C$ respectively, there is an embedding of $KL$ in $\bb C$ which restricts to $\sigma,\tau$ on $K,L$ respectively.

__Proof__: Note that if two embeddings of $KL$ in $\bb C$ agree on both $K$ and $L$, then they agree on all of $KL$. Hence the map

$$\left\{\begin{gathered}\text{embeddings}\\\text{of }KL\text{ in }\bb C\end{gathered}\right\}\to\left\{\begin{gathered}\text{embeddings}\\\text{of }K\text{ in }\bb C\end{gathered}\right\}\times\left\{\begin{gathered}\text{embeddings}\\\text{of }L\text{ in }\bb C\end{gathered}\right\}$$

given by $\rho\mapsto(\rho\rvert_ K,\rho\rvert_ L)$ is injective. But both sets have the same size, since

$$[KL:\bb Q]=mn=[K:\bb Q][L:\bb Q],$$

so this map is in fact bijective. In particular, there is some $\rho$ which maps to $(\sigma,\tau)$, as desired. $\qed$

Let the rings of algebraic integers in $K,L,KL$ be $R,S,T$, respectively. Clearly $T$ contains the ring

$$RS=\{\alpha_1\beta_1+\cdots+\alpha_r\beta_r\,:\,r\geq1,\,\alpha_i\in K,\,\beta_i\in L\}.$$

It is not true in general that $T=RS$, ie. that the reverse inclusion holds. However, we have the following result.

__Theorem__: Suppose that $[KL:\bb Q]=mn$, and let $d=\gcd(\disc R,\disc S)$. Then $T\subseteq\frac1dRS$.

__Proof__: This is a "relative" version of a previous proof. Let $\\{\alpha_1,\ldots,\alpha_m\\}$ and $\\{\beta_1,\ldots,\beta_n\\}$ be integral bases for $R$ and $S$, respectively. Then

$$\{\alpha_i\beta_j\,:\,1\leq i\leq m,\,1\leq j\leq n\}$$

is an integral basis for $RS$, and also a basis for $KL$ over $\bb Q$ (since $[KL:\bb Q]=mn$). Hence any $\alpha\in T$ can be written as

$$\alpha=\sum_{i,j}\frac{m_{ij}}r\alpha_i\beta_j$$

for some $m_{ij}\in\bb Z$, $r\in\bb Z_{>0}$. By taking $r$ minimal, we may assume that these $mn+1$ numbers have no common factors other than $1$, ie. $\gcd(r,\gcd(m_{ij}))=1$.

We now show that $r\mid\disc(R)$; then by symmetry, $r\mid\disc(S)$, so $r\mid d$, so $\alpha\in\frac1rRS\subseteq\frac1dRS$, and we would be done.

By the lemma above, every embedding $\sigma$ of $K$ in $\bb C$ extends to an embedding of $KL$ in $\bb C$ which restricts to identity on $L$; we will also call this embedding $\sigma$. Then

$$\sigma(\alpha)=\sum_{i,j}\frac{m_{ij}}r\sigma(\alpha_i)\beta_j.$$

Hence if we define

$$x_i=\sum_j\frac{m_{ij}}r\beta_j$$

for all $i$, then we have the linear system

$$\sum_i\sigma(\alpha_i)x_i=\sigma(\alpha).$$

As before, we can use Cramer's rule: if $\delta$ is the determinant of $(\sigma_i(\alpha_j))_ {i,j}$, and $\gamma_j$ is the determinant of the same matrix with the $j$-th column replaced by $\sigma_i(\alpha)$, then

$$x_j=\frac{\gamma_j}\delta.$$

Since all entries of both matrices above are algebraic integers, so are $\delta$ and $\gamma_j$.

Note that $\delta^2=\disc(R)$, so

$$x_j\disc(R)=\gamma_j\delta,$$

which is an algebraic integer (by RHS) in $L$ (by LHS), so $x_j\disc(R)\in S$. But

$$x_i\disc(R)=\sum_j\frac{m_{ij}\disc(R)}r\beta_j,$$

and $\beta_j$ form an integral basis for $S$, so the rational numbers $\frac{m_{ij}\disc(R)}r$ must all be integers. By assumption, $r$ is coprime to $\gcd(m_{ij})$, so we must have $r\mid\disc(R)$, and we are done. $\qed$