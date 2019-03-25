---
title: 'Commutative Algebra (IX): The Induced Map on the Spectrum'
layout: post
date: 2019-03-21 22:32:47 +0800
tag: [commutative algebra]
macros: >-
  "\\Spec":"\\operatorname{Spec}",
  "\\id":"\\operatorname{id}",
  "\\nil":"\\operatorname{nil}",
---

In the [previous post]({% post_url 2019-03-08-commutative-algebra-viii %}), we defined the prime spectrum of a ring as a topological space. In this post, we complete the definition of $\Spec$ as a contravariant functor from the category of (commutative unital) rings to the category of topological spaces.

<!--more-->

## The induced map

Let $A$ and $B$ be rings with spectra $X=\Spec(A)$ and $Y=\Spec(B)$. For this post, fix a ring homomorphism $\phi:A\to B$.

As in the coordinate ring case, $\phi$ induces a map $\phi^* :Y\to X$, defined by $\mf q\mapsto\phi^{-1}(\mf q)$. This is a well-defined map by the following result.

__Proposition__: If $\mf q\subseteq B$ is a prime ideal, then $\phi^{-1}(\mf q)$ is also a prime ideal.

__Proof__: For $f,g\in A$, we have

$$\begin{aligned}
fg\in\phi^{-1}(\mf q)&\implies\phi(fg)=\phi(f)\phi(g)\in\mf q\\
&\implies\phi(f)\in\mf q\text{ or }\phi(g)\in\mf q\\
&\implies f\in\phi^{-1}(\mf q)\text{ or }g\in \phi^{-1}(\mf q).\ \qed
\end{aligned}$$

This is also why we define the spectrum as the set of prime ideals rather than maximal ideals: the inverse image of a maximal ideal might not be maximal.

<!-- __Proposition__: For all $f\in A$, we have $(\phi^* )^{-1}(X_f)=Y_{\phi(f)}$.

__Proof__: For any $\mf q\in Y$, ie. $\mf q\subseteq B$ a prime ideal, we have

$$\begin{aligned}
\mf q\in(\phi^* )^{-1}(X_f)&\iff \phi^* (\mf q)\in X_f\\
&\iff Af\not\subseteq\phi^{-1}(\mf q)\\
&\iff f\not\in\phi^{-1}(\mf q)\\
&\iff\phi(f)\not\in\mf q\\
&\iff\mf q\in Y_{\phi(f)}.\ \qed
\end{aligned}$$

Since the $X_f$ form a basis of open sets for $X$, we have:

__Corollary__: $\phi^* $ is a continuous map. $\qed$

The map $\phi:A\to B$ gives a way to turn ideals of $A$ into ideals of $B$, or vice versa, as follows. (Here it might be useful to imagine that $\phi$ is injective, so that it embeds $A$ into $B$, though the constructions below work for the general case.) Given an ideal $\mf a\subseteq A$, we define the __extended ideal__ $\mf a^e=\phi(\mf a)B$, which is an ideal in $B$. Also, given an ideal $\mf b\subseteq B$, we define the __contracted ideal__ $\mf b^c=\phi^{-1}(\mf b)$, which is an ideal in $A$.

__Proposition__: Let $\mf a\subseteq A$ and $\mf b\subseteq B$ be ideals. Then

$$\mf a^{ec}\supseteq\mf a,\qquad\mf b^{ce}\subseteq\mf b.$$

__Proof__: We have $\phi(\mf a)\subseteq\phi(\mf a)B=\mf a^e$, so 

$$\mf a\subseteq\phi^{-1}(\phi(\mf a))\subseteq\phi^{-1}(\mf a^e)=\mf a^{ec}.$$

Also, we have $\phi(\mf b^c)\subseteq\mf b$, so

$$\mf b^{ce}=\phi(\mf b^c)B\subseteq\mf bB=\mf b.\ \qed$$

__Corollary__: Let $\mf a\subseteq A$ and $\mf b\subseteq B$ be ideals. Then

$$\mf a^{ece}=\mf a^e,\qquad\mf b^{cec}=\mf b^c.$$

__Proof__: The first equality follows from $\mf a^e\supseteq(\mf a^{ec})^e$ and $\mf a^e\subseteq(\mf a^e)^{ce}$. The second equality is similar. $\qed$

Hence there is a canonical bijection between ideals of $B$ of the form $\mf a^e$, and ideals of $A$ of the form $\mf b^c$. -->

__Proposition__: The induced map of the identity $\id_A:A\to A$ is $(\id_A)^* =\id_X$.

__Proof__: Note that $(\id_A)^{-1}(\mf p)=\mf p$. $\qed$

__Proposition__: Let $f:A\to B$ and $g:B\to C$ be ring homomorphisms, which give the induced maps $f^* :Y\to X$, $g^* :Z\to Y$, and $(gf)^* :Z\to X$, where $Z=\Spec(C)$. Then

$$(gf)^* =f^* g^* .$$

__Proof__: This follows from $f^{-1}(g^{-1}(\mc p))=(gf)^{-1}(\mc p)$. $\qed$

__Proposition__: Let $\mf a\subseteq A$ be an ideal. Then $(\phi^* )^{-1}(V(\mf a))=V(\phi(\mf a))$.

__Proof__: For any $\mf q\in Y$, ie. $\mf q\subseteq B$ a prime ideal, we have

$$\begin{aligned}
\mf q\in(\phi^* )^{-1}(V(\mf a))&\iff\phi^* (\mf q)\in V(\mf a)\\
&\iff\mf a\subseteq\phi^{-1}(\mf q)\\
&\iff\phi(\mf a)\subseteq\mf q\\
&\iff\mf q\in V(\phi(\mf a)).\ \qed
\end{aligned}$$

__Corollary__: $\phi^* $ is a continuous map.

__Proof__: By the above result, the preimage of all closed sets in $X$ under $\phi^* $ are closed in $Y$. $\qed$

Combining all the results above, we obtain:

__Theorem__: The mapping $\Spec$ sending $A\mapsto\Spec(A)$ and $f\mapsto\Spec(f)\coloneqq f^* $ defines a contravariant functor from the category of (commutative unital) rings to the category of topological spaces. $\qed$

## Direct image under the induced map

In the previous section, we worked out the inverse image of closed sets under $\phi^* $. For the direct image, we first prove some intermediate results.

__Proposition__: $\phi^* (Y)$ is dense in $X$ if and only if $\ker\phi\subseteq\nil(A)$.

__Proof__: ($\Leftarrow$) Note that for all $f\in A$, if $X_f\neq\emptyset$ then

$$\begin{aligned}
&f\not\in\mf p\text{ for some }\mf p\subseteq A\text{ prime}\\
&\implies f\not\in\nil(A)\\
&\implies f^n\not\in\nil(A)\text{ for all }n\geq1\\
&\implies\phi(f)\neq0\text{ for all }n\geq1\\
&\implies\phi(f)\not\in\nil(B)\\
&\implies\phi(f)\not\in\mf q\text{ for some }\mf q\subseteq B\text{ prime}\\
&\implies f\not\in\phi^{-1}(\mf q)=\phi^* (\mf q)\\
&\implies\phi^* (\mf q)\in X_f.
\end{aligned}$$

Hence $\phi^* (Y)$ intersects every nonempty basic open set $X_f\subseteq X$, so $\phi^* (Y)$ is dense in $X$.

($\Rightarrow$) We prove the contrapositive. If $\ker\phi\not\subseteq\nil(A)$, take any $f\in\ker\phi\backslash\nil(A)$. Then

$$\begin{aligned}
&0=\phi(f)\in\mf q\text{ for all }\mf q\in Y\\
&\implies f\in\phi^{-1}(\mf q)=\phi^* (\mf q)\text{ for all }\mf q\in Y\\
&\implies\phi^* (Y)\subseteq V(f)\\
&\implies\phi^* (Y)\cap X_f=\emptyset.
\end{aligned}$$

Now $f\not\in\nil(A)$, so $X_f$ is a nonempty open set in $X$. Hence $\phi^* (Y)$ is not dense in $X$. $\qed$

__Proposition__: Suppose that $\phi$ is surjective. Then $\phi^* $ is a homeomorphism of $Y$ onto $V_X(\ker\phi)\subseteq X$.

__Proof__: Note that $B\cong A/\ker\phi$. By the lattice isomorphism theorem, there is a correspondence

$$\begin{aligned}
Y=\left\{\begin{gathered}\text{prime ideals}\\\text{in }B\end{gathered}\right\}&\leftrightarrow\left\{\begin{gathered}\text{prime ideals in }A\\\text{containing }\ker\phi\end{gathered}\right\}=V_X(\ker\phi)\\
\mf q\quad&\mapsto\quad\phi^* (\mf q)\\
\phi(\mf p)\quad&\gets\quad\mf p,
\end{aligned}$$

so $\phi^* :Y\to V_X(\ker\phi)$ is a continuous bijection.

Moreover, this correspondence is inclusion-preserving, so for any ideal $\mf b\subseteq B$, the ideals containing $\mf b$ correspond exactly to the ideals containing $\phi^* (\mf b)$. In other words,

$$\phi^* (V_Y(\mf b))=V_X(\phi^* (\mf b)),$$

so $\phi^* $ maps every closed set in $Y$ to a closed set in $V_X(\ker\phi)$. Hence $\phi^* $ is a homeomorphism. $\qed$

__Corollary__: $\Spec(A)$ and $\Spec(A/\nil(A))$ are naturally homeomorphic.

__Theorem__: For any ideal $\mf b\subseteq B$, we have

$$\overline{\phi^* (V_Y(\mf b))}=V_X(\phi^* (\mf b)).$$

__Proof__: Note that the composition $A\overset\phi\to B\twoheadrightarrow B/\mf b$ has kernel $\phi^* (\mf b)$, so we have the induced map $\overline\phi$ in the following commutative diagram:

$$\begin{matrix}
A&\overset\phi\longrightarrow&B\\
\bigg\downarrow&&\bigg\downarrow\\
A/\phi^* (\mf b)&\underset{\overline\phi}\longrightarrow&B/\mf b
\end{matrix}$$

Now applying the $\Spec$ functor gives the following commutative diagram:

$$\def\ua#1{\bigg\uparrow\raisebox{.5ex}{\mathrlap{$\scriptstyle{#1}$}}}
\begin{matrix}
X&\overset{\phi^* }\longleftarrow&Y\\
\ua{\subseteq}&&\ua{\subseteq}\\
V_X(\phi^* (\mf b))&&V_Y(\mf b)\\
\ua{* }&&\ua{* }\\
\Spec(A/\phi^* (\mf b))&\overset{\overline\phi^* }\longleftarrow&\Spec(B/\mf b)
\end{matrix}$$

Now by the previous two results, the starred maps are homeomorphisms, and the image of $\overline\phi^* $ is dense in the codomain. Hence $\phi^* $ maps $V_Y(\mf b)$ into $V_X(\phi^* (\mf b))$ with dense image, as desired. $\qed$