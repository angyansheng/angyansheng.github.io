---
title: 'A Theory That Proves Its Own Inconsistency'
layout: post
tag: [logic]
date: 2018-12-06 23:00:00 +0800
macros: >-
  "\\Con":"\\operatorname{Con}",
---

I recently read this [mind-bending blog post by Joel David Hamkins](http://jdh.hamkins.org/every-function-can-be-computable/) that proves this result: there is a Turing machine program $P$ such that for any function $f:\bb N\to\bb N$---possibly uncomputable!---there is a model of Peano arithmetic (PA) in which $P$ computes $f$ on the standard natural numbers. If this statement doesn't surprise you, I'm not sure what else would (except maybe those who work in logic or set theory; I'm convinced that these people routinely [believe as many as six impossible things before breakfast](http://www-history.mcs.st-andrews.ac.uk/Quotations/Dodgson.html)).

A extraordinary claim needs an extraordinary proof, and when I read through Hamkins's argument I came across a lesser absurdity: a theory that proves its own inconsistency. Since all my knowledge of formal logic is from folklore, this post is my attempt to informally explain (to myself, at least) how such a theory can be constructed, and why it is not a contradiction in terms.

<!--more-->
## Consistency

The great insight of Gödel's incompleteness theorems is the __arithmetisation of logic__. Fix a logical theory that contains a certain subsystem of arithmetic, strong enough to encode strings of logical symbols into natural numbers. (For this post, we will choose PA for simplicity.) Then within PA, we can write formulas that mean

$n$ encodes a well-formed formula
{: style="text-align: center;"}

for any natural number $n$.

Now a proof of some formula $p$ is just a (finite) sequence of such formulas, each of which is either an axiom or follows from previous statements by the inference rules of logic, such that the last formula in the sequence is $p$. These formal manipulations of symbols can also be done within PA, so we can write formulas that mean

$n$ encodes a proof of $p$
{: style="text-align: center;"}

for any natural number $n$ and formula $p$.

Hence there is a formula in PA that states the consistency of the theory PA, namely

$$\Con(PA)\coloneqq\neg\exists n\,[n\text{ encodes a proof of }``0=1"\text{ in PA}].$$

## The theory

Consider the theory

$$T\coloneqq PA+\neg\Con(PA).$$

Note that $T$ has the following properties:
- Assume that PA is consistent. Then by Gödel's second incompleteness theorem, PA cannot prove $\Con(PA)$. Hence __$T$ is consistent__.
- Note that a proof of any formula $p$ in PA is also a proof of $p$ in $T$. Moreover, this assertion can be proven in PA. In particular, taking $p$ to be the formula $``0=1"$, we see that PA proves

  $$\neg\Con(PA)\rightarrow\neg\Con(T).$$

  Thus $T$ also proves the above formula. But $\neg\Con(PA)$ is an axiom of $T$, so $T$ proves $\neg\Con(T)$, ie. __$T$ proves its own inconsistency__!

## Resolving the paradox

Taking a closer look, let us unpack what $\neg\Con(T)$ says:

$$\exists n\,[n\text{ encodes a proof of }``0=1"\text{ in }T].$$

But since $T$ is consistent, we actually have

For each natural number $n$, $T$ proves that $n$ does not encode a proof of "$0=1$".
{: style="text-align: center;"}

The important thing to note is that the above sentence is not a formula in $T$, but a statement in the meta-theory.

So we see the heart of this apparent contradiction: $T$ proves a statement of the form $\exists n\,[P(n)]$, but cannot actually exhibit an example of $n$ where $P(n)$ is true! The technical term for this phenomenon is [$\omega$-inconsistency](https://en.wikipedia.org/wiki/%CE%A9-consistent_theory).

## Philosophical implications

Since I'm not nearly qualified enough to know what all this _really_ means, I'll list here some opinions from people who are.

Robert Seely notes that [consistency is actually a rather weak property](http://www.math.mcgill.ca/rags/JAC/124/second.html) of a theory: our example $T$ is consistent but unsound, in that it proves the false (by assumption) arithmetic statement $\neg\Con(T)$. More disconcertingly, there is no logical contradiction if we suppose the following three statements are all true:
1. ZFC is consistent;
2. For any even integer $n>2$, $n$ is a sum of two prime numbers (Goldbach's conjecture); and
3. ZFC proves that there exists an even integer $n>2$ that is not the sum of two prime numbers.

So the relationship between truth and provability is really subtle; a consistent theory can even prove a false arithmetical statment. Of course, the exact moral of this story would be different to a Platonist, a formalist, and an intuitionist, since even the notion of truth in itself varies across the different philosophies.

Also, there is a different interpretation of the resolution of the paradox. By Gödel's completeness theorem, $T$ is consistent implies that $T$ has a model $M$, say in ZFC. Then in $M$, there is an actual "natural number" $n$ that encodes a proof of $0=1$; it just happens that $M$ is a [nonstandard model of arithmetic](https://en.wikipedia.org/wiki/Non-standard_model_of_arithmetic), so $n$ is not a "standard" natural number, and the proof encoded by $n$ is of nonstandard length, hence invalid. So we should really modify one of the statements we made above to read:

For each __standard__ natural number $n$, $T$ proves that $n$ does not encode a proof of "$0=1$".
{: style="text-align: center;"}

But then [John Baez raises](https://johncarlosbaez.wordpress.com/2016/04/02/computing-the-uncomputable/) the following question: what exactly is the "standard model" of the natural numbers? We can define this as any model of second-order Peano arithmetic, which is provably unique up to isomorphism in ZFC. However, ZFC itself has nonstandard models (if ZFC is consistent, then so is $ZFC+\neg\Con(ZFC)$, which then has a model by Gödel's completeness theorem). Then some such nonstandard model of ZFC could have the "wrong" standard model of natural numbers, and how could we tell _then_?

Finally, [a short post by cousin_it](https://www.lesswrong.com/posts/PWP5j38tihSHkLsMc/no-one-knows-what-peano-arithmetic-doesn-t-know) observes that for any formal system (eg. ZFC), you can encode statements and proofs of that formal system as natural numbers in PA. Hence the ability to resolve all arithmetical implications of PA is equivalent to the ability to resolve all logical implications of _any_ formal system! It is mind-boggling to me that there is a statement about natural numbers in PA which is equivalent to $\Con(ZFC)$, and is hence undecidable in ZFC.

My set theory professor once told me, in the context of the continuum hypothesis and forcing, that no one really understands the nature of the power set of the natural numbers (equivalently, the real numbers). Perhaps at this point I could go one step further to posit: I don't really understand the nature of the natural numbers either, not anymore...