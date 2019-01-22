---
title: 'A Quick Note on Markov Chain Monte Carlo'
layout: post
date: 2019-01-09 23:48:05 +0800
tag: [statistics, mathematical biology]
---

In this note, we give a quick overview of the core ideas of Markov chain Monte Carlo methods, used to sample from probability distributions.

<!--more-->

Most of the information in this post is taken from [these notes by Torbjörn Karfunkel](http://www.math.chalmers.se/~olleh/Markov_Karfunkel.pdf), with additional input from my two roommates (both life sciences PhD students). All errors and omissions are my own.

## Metropolis-Hastings algorithm

Suppose that we want to sample from a given probability distribution on a space $\Omega$. Usually we cannot directly compute the probability distribution function, but sometimes we _can_ compute some function $f(x)\geq0$ which is proportional to it. Then there is a simple way of generating a sample from the given probability distribution:

1. Choose a random element $x_1\in\Omega$ (to simplify matters, we assume that there is some way of sampling from $\Omega$ uniformly);
2. For any $t\geq1$, choose a random element $x'\in\Omega$; then set $x_{t+1}=x'$ if $f(x')\geq f(x_t)$, and

   $$x_{t+1}=\begin{cases}
   x'&\text{with probability }\frac{f(x')}{f(x_t)},\\
   x_t&\text{with probability }1-\frac{f(x')}{f(x_t)},
   \end{cases}$$

   if $f(x')< f(x_t)$.

In other words, we always jump from $x$ to $x'$ if $f(x')\geq f(x)$, but the probability of making the jump decreases linearly with $f(x')$ if $f(x')< f(x)$.

Intuitively, this ensures that regions in $\Omega$ with higher values of $f$ are sampled more often. In fact, it can be shown that the probability density of the resulting sequence $x_1,x_2,\ldots$ is exactly proportional to $f$; this is the essential content of the correctness of the [Metropolis-Hastings algorithm](https://en.wikipedia.org/wiki/Metropolis%E2%80%93Hastings_algorithm).

## Bayesian inference

Recall that in Bayesian statistics, we have a given __prior probability__ $\bb P(H)$ on some hypothesis $H$, which represents one's _a priori_ beliefs. Now when we collect some new data or evidence $E$, the __posterior probability__ for $H$ is given by Bayes's law:

$$\bb P(H\mid E)=\frac{\bb P(E\mid H)\bb P(H)}{\bb P(E)},$$

where $\bb P(E)$ is the __unconditional__ or __marginal probability__ for observing $E$, based on the prior probability distribution on all hypotheses, and $\bb P(E\mid H)$ is the __likelihood__ of observing $E$ given that $H$ holds.

Crucially, this means that the posterior probability distribution of hypotheses can be computed based on the prior distribution and the other terms. This means we can apply the Metropolis-Hastings algorithm, to obtain a sample of hypotheses from the posterior distribution.

## Application to phylogenetics

Consider the problem of reconstructing the evolutionary history for a collection of species. Generally, we compare certain morphological features or genetic data across the species, and we want to deduce the __phylogenetic tree__ for these species.

One approach is to use the Bayesian inference framework, by starting from a uniform prior distribution of trees, and then drawing conclusions from the posterior distribution sampled with the Metropolis-Hastings algorithm. More explicitly, we perform the following steps:

1. Pick a tree $T_1$ uniformly at random from among all possible phylogenetic trees. This is a hypothesis on the evolutionary history of the given collection of species, and so we can calculate its posterior probability given the observations.
2. For each $t\geq1$, pick a new tree $T'$ uniformly at random, and compute its posterior probability. Then set either $T_{t+1}=T'$ or $T_{t+1}=T_t$ based on the Metropolis-Hastings rule.

This produces a sequence $T_1,T_2,\ldots$, whose probability distribution tends to the posterior distribution of hypotheses as the number of samples increases.

> Note that in this case, even though we can compute the posterior probability for each tree, the total number of possible trees is so large that directly calculating each posterior is infeasible. This shows the power of the Metropolis-Hastings algorithm, where the number of posteriors we need to calculate only depends on the number of samples we want.

Now that we have a sample from the posterior distribution, we can estimate the posterior distribution of any quantity by calculating it for each tree in the sample. Such quantities of biological interest include time to last common ancestor (for simple models), and the probability that some subset of the given species form a monophyletic clade (ie. it is the set of all descendants of a common ancestor).