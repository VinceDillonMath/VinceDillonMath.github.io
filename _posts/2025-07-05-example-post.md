---
layout: post
title: "The Class Field Tower Problem and Golod-Shafarevich Groups"
date: 2025-08-18
---

The purpose of this post is to present a counterexample to the so-called class field tower problem. Interestingly, the solution lies almost entirely within the realm of pure algebra and can be understood with almost no background in algebraic number theory. Nonetheless, the problem remained open for decades (~1925-1965) despite being a natural question arising from elementary algebraic number theory. We roughly follow Ershov's notes which can be found \href{https://m-ershov.github.io/Research/gssurvey_revised.pdf}{here}.

For any number field $K$, let $\mathcal I_K$ be the group of fractional ideals in $\mathcal O_K$ and $\mathcal P_K$ the (normal) subgroup of principal ideals. The finite quotient
$$\mathrm{Cl}_K:=\mathcal I_K/\mathcal P_K$$
is the ideal class group of the number field. This group is a really important invariant of the number field $K$: it's order, called the class number of $K$, measures how far $\mathcal O_K$ is from being a PID. 

Let $\mathbb{H}(K)$ denote the Hilbert class field of $K$; this is the maximal abelian unramified extension of $K$. Beautifully, by the formalism of class field theory, we have that
$$\mathrm{Gal}(\mathbb{H}(K)/K)\cong\mathrm{Cl}_K.$$
This means that a number field has $\mathcal O_K$ a PID if and only if it has no abelian unramified extensions. By Minkowski's bound, this gives an amusing proof of unique prime factorization in $\mathbb Z$.

Let's now state the problem at hand. It has a slightly dynamical flavor that I find very appealing. 

### The Class Field Tower Problem
Let $K$ be a number field and consider the tower of extensions
    $$K=\mathbb{H}^0(K)\subset \mathbb{H}^1(K)\subset \mathbb{H}^2(K)\subset \dots$$
    where $\mathbb{H}^n(K)=\mathbb{H}(\mathbb{H}^{n-1}(K)).$ We call the sequence $\{\mathbb{H}^i(K)\}_{i=0}^\infty$ the class field tower of $K$. The question is this: for any number field $K$, does the class field tower $\{\mathbb{H}^i(K)\}$ eventually stabilize? That is, does there exist some $N\in \mathbb{N}$ such that for every $i\geq N$, $[\mathbb{H}^i(K):\mathbb{H}^N(K)]=1$?
There's a nice equivalent formulation: given a number field $K$, does the exist a finite extension $L$ such that $\mathcal O_L$ is a PID? 

\textit{Proof of equivalence:} One direction is easy. If the CFTP has a positive solution, then for any number field $K$, we can find some 
    $$[\mathbb{H}^i(K):\mathbb{H}^{i-1}(K)]=1.$$
    Then since $\mathrm{Gal}(\mathbb{H}^i(K)/\mathbb{H}^{i-1}(K))\cong C_{\mathbb{H}^{i-1}(K)}$ are both trivial, we have $|C_{\mathbb{H}^{i-1}(K)}|=1$ and hence $\mathcal{O}_{\mathbb{H}^{i-1}(K)}$ is a PID. \\
    \\
    Conversely, suppose we can find some finite extension $L/K$ such that $|C_L|=1$. Since the extensions $\mathbb{H}^i(K)/\mathbb{H}^{i-1}(K)$ are abelian and unramified for each $i$, so are the compositum extensions $L\mathbb{H}^i(K)/L\mathbb{H}^{i-1}(K)$. Since $|C_L|=1$, $\mathbb{H}(L)=L$ so any abelian unramified extension of $L$ must be trivial. We have $$L=L\mathbb{H}^1(K)=L\mathbb{H}^0(K)=LK=L.$$
    Inductively, this gives $L\mathbb{H}^i(K)=L$ and hence $\mathbb{H}^i(K)\subset L$ for every $i\in \N$. Since $L$ is a finite extension, the class field tower must eventually stabilize.
The first formulation will be used to construct the counterexample, the second is nice motivation.
