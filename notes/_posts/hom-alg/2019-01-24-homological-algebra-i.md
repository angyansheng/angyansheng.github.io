---
title: 'Homological Algebra (I): The Five Lemma and the Snake Lemma'
layout: post
date: 2019-01-24 09:08:18 +0800
tag: [homological algebra, commutative algebra]
macros: >-
  "\\im":"\\operatorname{im}",
  "\\coker":"\\operatorname{coker}",
  "\\tca":"\\text{\\textcircled1}",
  "\\tcb":"\\text{\\textcircled2}",
  "\\tcc":"\\text{\\textcircled3}",
  "\\tcd":"\\text{\\textcircled4}",
  "\\tce":"\\text{\\textcircled5}",
  "\\tcf":"\\text{\\textcircled6}",
  "\\tcg":"\\text{\\textcircled7}"
---

In this post, we prove two useful results in homological algebra, namely the five lemma and the snake lemma.

<!--more-->

The results of homological algebra are applicable in any abelian category (roughly, any category in which we can define kernels and cokernels). However, for this set of notes, we will work over categories with forgetful functor to the category of sets, such as:
- the category of abelian groups;
- the category of commutative rings; and
- the category of $A$-modules for a commutative ring $A$.

This enables us to speak of elements of objects, which makes diagram chasing arguments possible.

Many of the proofs in this post involve checking a large number of elementary steps. To present these proofs more compactly, and as an aid to the reader, we have opted for an experimental visual approach to diagram chasing.

In any case, it should be noted that the proofs are, in some sense, less important than the statement of the lemmas themselves. For instance, in most cases we will not need the explicit form of the connecting map in the snake lemma, only that it exists and forms part of an exact sequence. As such, the reader can choose to skip the proofs of these lemmas on first reading.

## The five lemma

__Five Lemma__: Let

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
A&\ra{}&B&\ra{}&C&\ra{}&D&\ra{}&E\\
\da{f_1}&&\da{f_2}&&\da{f_3}&&\da{f_4}&&\da{f_5}\\
A'&\ra{}&B'&\ra{}&C'&\ra{}&D'&\ra{}&E'
\end{matrix}$$

be a commutative diagram of modules with exact rows.

1. If $f_1$ is surjective and $f_2,f_4$ are injective, then $f_3$ is injective.
2. If $f_5$ is injective and $f_2,f_4$ are surjective, then $f_3$ is surjective.

__Proof__: (1) Take $c\in\ker f_3$. Then by elementary diagram chasing, we get the following elements of the respective objects (circled numbers represent order of deduction):

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
a_\tcf&\ra{\tcg}&b_\tcc&\ra{}&c&\ra{}&0_\tcb\\
\da{f_1}&&\da{f_2}&&\da{f_3}&&\da{f_4}\\
a'_ \tce&\ra{}&b'_ \tcd&\ra{}&0&\ra{}&0_\tca
\end{matrix}$$

In detail, we have the following deductions:
- $\tcb$: by injectivity of $f_4$;
- $\tcc$: by row exactness;
- $\tce$: by row exactness;
- $\tcf$: by surjectivity of $f_1$;
- $\tcg$: by injectivity of $f_2$ (since both $b$ and the image of $a$ map to $b'$).

{% comment -%}
<!-- If $c\in C$ maps to $0\in C'$, then it maps to some $d\in D$ which goes to $0\in D'$. By injectivity of $f_4$ we get $d=0$.

Hence by exactness of the top row, there exists some $b\in B$ mapping to $c$. This maps to $b'\in B'$, which by exactness of the bottom row comes from some $a'\in A'$. By surjectivity of $f_1$ this comes from some $a\in A$.

In the general case, mapping $a$ to $B$ might not give the element $b$; but since both the image of $a$ and $b$ map to $b'$, and $f_2$ is injective, we have $a$ maps to $b$. -->
{% endcomment -%}

Hence by exactness of the top row, $b$ maps to $0=c$. Thus $\ker f_3=\\{0\\}$, ie. $f_3$ is injective.

(2) Take any $c'\in C'$. Then diagram chasing gives:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
c_\tce&\ra{}&d_\tcb&\ra{}&0_\tcd\\
&&\da{f_4}&&\da{f_5}\\
c'&\ra{}&d'_ \tca&\ra{}&0_\tcc
\end{matrix}$$

- $\tcb$: by surjectivity of $f_4$;
- $\tcc$: by row exactness;
- $\tcd$: by injectivity of $f_5$;
- $\tce$: by row exactness.

Now we also have:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
\widehat b_\tcc&\ra{}&\widehat c_\tcd\\
\da{f_2}&&\da{f_3}&&\\
\widehat{b'}_ \tcb&\ra{}&f_3(c)-c'&\ra{}&0_\tca
\end{matrix}$$

- $\tca$: since $f_3(c)$ and $c'$ both map to $d'$;
- $\tcb$: by row exactness;
- $\tcc$: by surjectivity of $f_2$.

Then $f_3(c-\widehat c)=c'$, so $f_3$ is surjective. $\qed$

{% comment -%}
<!-- For any $c'\in C'$, mapping to $d'\in D'$, by surjectivity of $f_4$ there is some $d\in D$ mapping to $d'$.

Now $d'$ maps to $0$ in $E'$, so by injectivity of $f_5$ we have $d$ maps to $0$ in $E$. Hence by exactness of the top row there exists $c\in C$ mapping to $d$.

Now $f_3(c)-c'$ maps to $0$ in $D'$, so by exactness of the bottom row there exists $\widehat{b'}\in B'$ mapping to $f_3(c)-c'$. By surjectivity of $f_2$, there exists $\widehat b\in B$ mapping to $\widehat{b'}$. If $\widehat b$ maps to $\widehat c\in C$, then $\widehat c+c$ maps to $c'$ in $C'$. $\qed$ -->
{% endcomment -%}

## Induced maps on $\ker$ and $\coker$

__Proposition__: Let

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
A&\ra{f}&B\\
\da{h}&&\da{k}\\
C&\ra{g}&D
\end{matrix}$$

be a commutative diagram. Then:

1. $f$ induces a map $\overline f:\ker h\to\ker k$;
2. $g$ induces a map $\underline g:\coker h\to\coker k$;
3. if $f$ is injective, then so is $\overline f$;
4. if $g$ is surjective, then so is $\underline g$.

__Proof__: (1) If $a\in A$ is mapped to $0\in C$, then $f(a)\in B$ is mapped to $0\in D$. Hence $f(\ker h)\subseteq\ker k$, so the restriction of $f$ to $\ker h$ is a map $\overline f:\ker h\to\ker k$.

(2) If $c\in\im h$, say $c=h(a)$, then $c$ maps to $g(c)=k\circ f(a)\in D$. Hence $g(\im h)\subseteq\im k$, so the map $C\to D\to D/\im k$ factors into a map $\underline g:C/\im h\to D/\im k$.

(Explicitly, we have $\underline g(c+\im h)=g(c)+\im k$.)

(3,4) Clear. $\qed$

__Proposition__: Let

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&A'&\ra{\overline f}&B'&\ra{\overline s}&C'\\
&&\da{}&&\da{I\!I}&&\da{I}\\
&&A&\ra{f}&B&\ra{s}&C&\ra{}&0\\
&&\da{h}&&\da{k}&&\da{l}\\
0&\ra{}&D&\ra{g}&E&\ra{t}&F\\
&&\da{I\!I\!I}&&\da{I\!V}&&\da{}\\
&&D'&\ra{\underline g}&E'&\ra{\underline t}&F'
\end{matrix}$$

be a commutative diagram with exact rows and exact columns. Then:
1. If $I$ is injective, then $\overline s\circ\overline f=0$;
2. If $I\\!I$ is injective, then $\ker\overline s\subseteq\im\overline f$;
3. If $I\\!I\\!I$ is surjective, then $\underline t\circ\underline g=0$;
4. If $I\\!V$ is surjective, then $\ker\underline t\subseteq\im\underline g$.

__Proof__: (1) Let $a'\in A'$. Then diagram chasing gives:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&a'&\ra{\overline f}&b'_ \tcb&\ra{\overline s}&0_\tcd\\
&&\da{}&&\da{I\!I}&&\da{I}\\
&&a_\tca&\ra{f}&b_\tcb&\ra{s}&0_\tcc&\ra{}&0\\
\end{matrix}$$

- $\tcc$: by row exactness;
- $\tcd$: by injectivity of $I$.

Hence $\overline s\circ\overline f=0$.

(2) Let $b'\in\ker\overline s$. Then diagram chasing gives:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&a'_ \tce&\ra{\overline f\tcf}&b'&\ra{\overline s}&0\\
&&\da{}&&\da{I\!I}&&\da{I}\\
&&a_\tcb&\ra{f}&b_\tca&\ra{s}&0_\tca&\ra{}&0\\
&&\da{h}&&\da{k}\\
0&\ra{}&0_\tcd&\ra{g}&0_\tcc
\end{matrix}$$

- $\tcb$: by row exactness;
- $\tcc$: by column exactness;
- $\tcd$: by injectivity of $g$;
- $\tce$: by column exactness;
- $\tcf$: by injectivity of $I\\!I$ (since both $b'$ and $\overline f(a')$ map to $b$).

Hence $\overline f(a')=b'$, so $\ker\overline s\subseteq\im\overline f$.

(3) Let $d'\in D'$. Then diagram chasing gives:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
0&\ra{}&d_\tca&\ra{g}&e_\tcb&\ra{t}&0_\tcc\\
&&\da{I\!I\!I}&&\da{I\!V}&&\da{}\\
&&d'&\ra{\underline g}&e'_ \tcb&\ra{\underline t}&0_\tcd
\end{matrix}$$

- $\tca$: by surjectivity of $I\\!I\\!I$;
- $\tcc$: by row exactness.

Hence $\underline t\circ\underline g=0$.

(4) Let $e'\in\ker\underline t$. Then diagram chasing gives:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
b_\tcd&\ra{s}&c_\tcc&\ra{}&0\\
&&\da{l}\\
e_\tca&\ra{t}&f_\tcb\\
\da{I\!V}&&\da{}\\
e'&\ra{\underline t}&0
\end{matrix}$$

- $\tca$: by surjectivity of $I\\!V$;
- $\tcc$: by column exactness;
- $\tcd$: by surjectivity of $s$.

Now we also have:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
0&\ra{}&d_\tcc&\ra{g}&e-k(b)&\ra{t}&0_\tcb\\
&&\da{I\!I\!I}&&\da{I\!V}&&\da{}\\
&&d'_ \tcd&\ra{\underline g}&e'_ \tca&\ra{\underline t}&f'
\end{matrix}$$

- $\tca$: since $I\\!V\circ k=0$;
- $\tcb$: since $k(b)$ and $e$ both map to $f'$;
- $\tcc$: by row exactness.

Hence $\underline g(d')=e'$, so $\ker\underline t\subseteq\im\underline g$.


__Corollary__: Let

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&A&\ra{f}&B&\ra{s}&C&\ra{}&0\\
&&\da{h}&&\da{k}&&\da{l}\\
0&\ra{}&D&\ra{g}&E&\ra{t}&F
\end{matrix}$$

be a commutative diagram with exact rows. Then the sequences of induced maps

$$\ker h\xrightarrow{\overline f}\ker k\xrightarrow{\overline s}\ker l$$

and

$$\coker h\xrightarrow{\underline g}\coker k\xrightarrow{\underline t}\coker l$$

are exact.

__Proof__: Consider the following commutative diagram:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&0&&0&&0\\
&&\da{}&&\da{}&&\da{}\\
&&\ker h&\ra{\overline f}&\ker k&\ra{\overline s}&\ker l\\
&&\da{}&&\da{I\!I}&&\da{I}\\
&&A&\ra{f}&B&\ra{s}&C&\ra{}&0\\
&&\da{h}&&\da{k}&&\da{l}\\
0&\ra{}&D&\ra{g}&E&\ra{t}&F\\
&&\da{I\!I\!I}&&\da{I\!V}&&\da{}\\
&&\coker h&\ra{\underline g}&\coker k&\ra{\underline t}&\coker l\\
&&\da{}&&\da{}&&\da{}\\
&&0&&0&&0
\end{matrix}$$

Note that all columns are exact, so all conditions of the previous proposition are satisfied. $\qed$

{% comment -%}
<!-- (1) Since $\overline f$, $\overline s$ are restrictions of $f$, $s$ respectively, we have $s\circ f=0$ implies $\overline s\circ\overline f=0$.

Now if $b\in\ker k$ satisfies $\overline s(b)=0$, then $s(b)=0$ implies that $f(a)=b$ for some $a\in A$. But $k(b)=0$ and $g$ is injective implies $h(a)=0$, so $a\in\ker h$. Thus $b\in\im\overline f$, so $\ker\overline s\subseteq\im\overline f$.

(2) We have

$$\begin{aligned}
\underline t\circ\underline g(c+\im h)&=\underline t(g(c)+\im k)\\
&=t\circ g(c)+\im l\\
&=0,
\end{aligned}$$

so $\underline t\circ\underline g=0$.

Now if $e+\im k\in\coker k$ satisfies $\underline t(e+\im k)=0$, then $t(e)\in\im l$ implies $l(c)=t(e)$ for some $c\in C$. By surjectivity of $s$, we have $c=s(b)$ for some $b\in B$.

Then $t(e-k(b))=0$, so $e-k(b)=g(d)$ for some $d\in D$. Hence $\underline g(d+\im h)=e+\im k$, so $\ker\underline t\subseteq\im\underline g$. $\qed$ -->
{% endcomment -%}

## The connecting map

Considering the same commutative diagram

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&A'&\ra{\overline f}&B'&\ra{\overline s}&C'\\
&&\da{}&&\da{I\!I}&&\da{I}\\
&&A&\ra{f}&B&\ra{s}&C&\ra{}&0\\
&&\da{h}&&\da{k}&&\da{l}\\
0&\ra{}&D&\ra{g}&E&\ra{t}&F\\
&&\da{I\!I\!I}&&\da{I\!V}&&\da{}\\
&&D'&\ra{\underline g}&E'&\ra{\underline t}&F'
\end{matrix}$$

with exact rows and columns, we will define a map $\delta:C'\to D'$, called the __connecting map__. Given $c'\in C'$, construct the following elements:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&&&&&c'\\
&&&&&&\da{I}\\
&&&&b_\tcb&\ra{s}&c_\tca&\ra{}&0\\
&&&&\da{k}&&\da{l}\\
0&\ra{}&d_\tce&\ra{g}&e_\tcd&\ra{t}&0_\tcc\\
&&\da{I\!I\!I}\\
&&d'_ \tcf
\end{matrix}$$

- $\tcb$: by row exactness;
- $\tce$: by row exactness.

We then define $\delta(c')=d'$.

{% comment -%}
<!-- For any $c\in\ker l$, there exists $b\in B$ with $s(b)=c$, by surjectivity of $s$. Now $k(b)=e\in\ker t$, so there exists $d\in D$ with $g(d)=e$. Now we define $\delta(c)=d+\im h$. -->
{% endcomment -%}

__Proposition__: The connecting map $\delta:C'\to D'$ is well-defined.

__Proof__: We need to show that $d'$ is independent of any choices that we make during our construction. Note that we made one such arbitrary choice, at $\tcb$. (The choice at $\tce$ was _not_ arbitrary, since $g$ is injective.)

As such, suppose that we made a different choice $\tilde b$ at $\tcb$, which leads to the elements $\tilde e$, $\tilde d$, and $\tilde d'$ respectively. Then we have the following diagram:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&\widehat a_\tcb&\ra{f}&b-\tilde b&\ra{s}&0_\tca&\ra{}&0\\
&&\da{h\tcc}&&\da{k}&&\da{l}\\
0&\ra{}&d-\tilde d&\ra{g}&e-\tilde e&\ra{t}&0\\
&&\da{I\!I\!I}\\
&&d'-\tilde d'
\end{matrix}$$

- $\tca$: by $s(b)=s(b')=c$;
- $\tcb$: by row exactness;
- $\tcc$: by injectivity of $g$.

Hence by exactness of the left column, $d'=\tilde d'$. $\qed$

The drawback of the diagram chasing proof is that it is not clear why $\delta$ is in fact a homomorphism; however, this can be easily checked in each case for abelian groups, commutative rings, and $A$-modules.

Here are some more properties of the connecting map.

__Proposition__: Consider the same diagram

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&A'&\ra{\overline f}&B'&\ra{\overline s}&C'\\
&&\da{}&&\da{I\!I}&&\da{I}\\
&&A&\ra{f}&B&\ra{s}&C&\ra{}&0\\
&&\da{h}&&\da{k}&&\da{l}\\
0&\ra{}&D&\ra{g}&E&\ra{t}&F\\
&&\da{I\!I\!I}&&\da{I\!V}&&\da{}\\
&&D'&\ra{\underline g}&E'&\ra{\underline t}&F'
\end{matrix}$$

with exact rows and columns, and let $\delta:C'\to D'$ be the connecting map. Then:
1. $\delta\circ\overline s=0$;
2. if $I$ is injective, then $\ker\delta\subseteq\im\overline s$;
3. $\underline g\circ\delta=0$;
4. if $I\\!I\\!I$ is surjective, then $\ker\underline g\subseteq\im\delta$.

__Proof__: (1) Take $b'\in B'$. Then we have:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&&&b'&\ra{\overline s}&c'_ \tca\\
&&&&\da{I\!I}&&\da{I}\\
&&&&b_\tca&\ra{s}&c_\tca&\ra{}&0\\
&&&&\da{k}&&\da{l}\\
0&\ra{}&0_\tcd&\ra{g}&e_\tcc&\ra{t}&0_\tcb\\
&&\da{I\!I\!I}\\
&&0_\tce
\end{matrix}$$

- $\tcb$: by column exactness;
- $\tcc$: by column exactness;
- $\tcd$: by injectivity of $g$.

Hence $0=\delta(c')=\delta\circ\overline s(b')$, so $\delta\circ\overline s=0$.

(2) If $\delta(c')=d'=0$ then we have:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&&&&&c'\\
&&&&&&\da{I}\\
&&a_\tca&&b&\ra{s}&c&\ra{}&0\\
&&\da{h}&&\da{k}&&\da{l}\\
0&\ra{}&d&\ra{g}&e&\ra{t}&0\\
&&\da{I\!I\!I}\\
&&0
\end{matrix}$$

- $\tca$: by column exactness.

Now we also have:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
\widehat{b'}_ \tcc&\ra{\overline s\tcd}&c'\\
\da{I\!I}&&\da{I}\\
b-f(a)&\ra{s}&c_\tca&\ra{}&0\\
\da{k}&&\da{l}\\
0_\tcb&\ra{t}&0
\end{matrix}$$

- $\tca$: by row exactness;
- $\tcb$: since $k\circ f(a)=g\circ h(a)=e=k(b)$;
- $\tcc$: by column exactness;
- $\tcd$: by injectivity of $I$.

Hence $c'=\overline s(\widehat{b'})$, so $\ker\delta\subseteq\im\overline s$.

(3) Take $c'\in C'$. Then we have:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&&&&&c'\\
&&&&&&\da{I}\\
&&&&b&\ra{s}&c&\ra{}&0\\
&&&&\da{k}&&\da{l}\\
0&\ra{}&d&\ra{g}&e&\ra{t}&0\\
&&\da{I\!I\!I}&&\da{I\!V}\\
&&d'&\ra{\underline g}&0_\tca
\end{matrix}$$

- $\tca$: by column exactness.

Hence $0=\underline g(d')=\underline g\circ\delta(c')$, so $\underline g\circ\delta=0$.

(4) If $\underline g(d')=0$ then we have:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&&&&&c'_ \tcf\\
&&&&&&\da{I}\\
&&&&b_\tcd&\ra{s}&c_\tce&\ra{}&0\\
&&&&\da{k}&&\da{l}\\
0&\ra{}&d_\tca&\ra{g}&e_\tcb&\ra{t}&0_\tcc\\
&&\da{I\!I\!I}&&\da{I\!V}\\
&&d'&\ra{\underline g}&0
\end{matrix}$$

- $\tca$: by surjectivity of $I\\!I\\!I$;
- $\tcc$: by row exactness;
- $\tcd$: by column exactness;
- $\tcf$: by column exactness.

Hence $d'=\delta(c')$, so $\ker\underline g\subseteq\im\delta$. $\qed$

## The snake lemma

__Snake Lemma__: Let

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&A&\ra{f}&B&\ra{s}&C&\ra{}&0\\
&&\da{h}&&\da{k}&&\da{l}\\
0&\ra{}&D&\ra{g}&E&\ra{t}&F
\end{matrix}$$

be a commutative diagram with exact rows. Then the sequence

$$\ker h\xrightarrow{\overline f}\ker k\xrightarrow{\overline s}\ker l\xrightarrow{\delta}\coker h\xrightarrow{\underline g}\coker k\xrightarrow{\underline t}\coker l$$

is exact.

__Proof__: Consider the following commutative diagram:

$$\def\ra#1{\kern-1.5ex\xrightarrow{\ \ \smash{#1}\ \ }\phantom{}\kern-1.5ex}
\def\da#1{\bigg\downarrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
&&0&&0&&0\\
&&\da{}&&\da{}&&\da{}\\
&&\ker h&\ra{\overline f}&\ker k&\ra{\overline s}&\ker l\\
&&\da{}&&\da{I\!I}&&\da{I}\\
&&A&\ra{f}&B&\ra{s}&C&\ra{}&0\\
&&\da{h}&&\da{k}&&\da{l}\\
0&\ra{}&D&\ra{g}&E&\ra{t}&F\\
&&\da{I\!I\!I}&&\da{I\!V}&&\da{}\\
&&\coker h&\ra{\underline g}&\coker k&\ra{\underline t}&\coker l\\
&&\da{}&&\da{}&&\da{}\\
&&0&&0&&0
\end{matrix}$$

Note that all columns are exact. We have already shown exactness at $\ker k$ and $\coker k$. Now all conditions of the previous proposition are satisfied, which implies exactness at $\ker l$ and $\coker h$. $\qed$