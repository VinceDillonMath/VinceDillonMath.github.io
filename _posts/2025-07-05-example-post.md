---
layout: post
title: "The Class Field Tower Problem and Golod-Shafarevich Groups"
date: 2025-08-18
---

The purpose of this post is to present a counterexample to the so-called class field tower problem. Interestingly, the solution lies almost entirely within the realm of pure algebra and can be understood with almost no background in algebraic number theory. Nonetheless, the problem remained open for decades (~1925-1965) despite being a natural question arising from elementary algebraic number theory. We roughly follow Ershov's notes which can be found [here](https://m-ershov.github.io/Research/gssurvey_revised.pdf).

For any number field $K$, let $\mathcal I_K$ be the group of fractional ideals in $\mathcal O_K$ and $\mathcal P_K$ the (normal) subgroup of principal ideals. The finite quotient
\begin{equation}
    \mathrm{Cl}_K:=\mathcal I_K/\mathcal P_K
\end{equation}

is the ideal class group of the number field. This group is a really important invariant of the number field $K$: it's order, called the class number of $K$, measures how far $\mathcal O_K$ is from being a PID. 

Let $\mathbb{H}(K)$ denote the Hilbert class field of $K$; this is the maximal abelian unramified extension of $K$. Beautifully, by the formalism of class field theory, we have that
\begin{equation}
    \mathrm{Gal}(\mathbb{H}(K)/K)\cong\mathrm{Cl}_K.
\end{equation}
This means that a number field has $\mathcal O_K$ a PID if and only if it has no abelian unramified extensions. By Minkowski's bound, this gives an amusing proof of unique prime factorization in $\mathbb Z$.

Let's now state the problem at hand. It has a slightly dynamical flavor that I find very appealing. 

### The Class Field Tower Problem
Let $K$ be a number field and consider the tower of extensions
\begin{equation}
    K=\mathbb{H}^0(K)\subset \mathbb{H}^1(K)\subset \mathbb{H}^2(K)\subset \dots
\end{equation}
    where $\mathbb{H}^n(K)=\mathbb{H}(\mathbb{H}^{n-1}(K)).$ We call the sequence ${\mathbb{H}^i(K)}_{i=0}^\infty$ the class field tower of $K$. The question is this: for any number field $K$, does the class field tower ${\mathbb{H}^i(K)}$ eventually stabilize? That is, does there exist some $N\in \mathbb{N}$ such that for every $i\geq N$, $[\mathbb{H}^i(K):\mathbb{H}^N(K)]=1$?
There's a nice equivalent formulation: given a number field $K$, does the exist a finite extension $L$ such that $\mathcal O_L$ is a PID? 

*Proof of equivalence:* One direction is easy. If the CFTP has a positive solution, then for any number field $K$, we can find some 
    \begin{equation} [\mathbb{H}^i(K):\mathbb{H}^{i-1}(K)]=1.
    \end{equation}
    Then since $\mathrm{Gal}(\mathbb{H}^i(K)/\mathbb{H}^{i-1}(K))\cong C_{\mathbb{H}^{i-1}(K)}$ are both trivial, we have $\lvert C_{\mathbb{H}^{i-1}(K)}\rvert =1$ and hence $\mathcal{O}_{\mathbb{H}^{i-1}(K)}$ is a PID. \\
    \\
    Conversely, suppose we can find some finite extension $L/K$ such that $\lvert C_L\rvert =1$. Since the extensions $\mathbb{H}^i(K)/\mathbb{H}^{i-1}(K)$ are abelian and unramified for each $i$, so are the compositum extensions $L\mathbb{H}^i(K)/L\mathbb{H}^{i-1}(K)$. Since $\lvert C_L\rvert =1$, $\mathbb{H}(L)=L$ so any abelian unramified extension of $L$ must be trivial. We have 
    \begin{equation}
    L=L\mathbb{H}^1(K)=L\mathbb{H}^0(K)=LK=L.
    \end{equation}
    Inductively, this gives $L\mathbb{H}^i(K)=L$ and hence $\mathbb{H}^i(K)\subset L$ for every $i\in \mathbb N$. Since $L$ is a finite extension, the class field tower must eventually stabilize. $\square$
The first formulation will be used to construct the counterexample, the second is nice motivation.

The counterexample is essentially constructed as follows: we isolate the pro-p subgroup of the limiting Galois group, show the corresponding $\mathbb F_p$-algebra is infinite dimensional, and conclude the group itself (and hence the extension) is infinite.

The *Magnus algebra* over a field k and a finite set of variables $U$, denoted $k\langle\langle U\rangle\rangle$ is the algebra of formal, non-commuting power series in the variables from $U$. For example,
\begin{equation}
    x+xy+xy^2+xy^3+\dots\neq x+yx+y^2x+y^3x+\dots
\end{equation}
in $\mathbb C\langle\langle {x,y}\rangle\rangle$.

**Some Definitions.** Let $A=\mathbb F_p\langle\langle U\rangle\rangle/I$ where $I$ is some closed two-sided ideal and $I$ is the kernel of the map $\pi:\mathbb F_p\langle\langle U\rangle\rangle\twoheadrightarrow A$. Notice that $A$ is naturally filtered by $A_n=\pi(F_n)$. Algebras (such as $A$) isomorphic to quotients of the Magnus algebra are called complete filtered algebras. Let $R\subset I$ be a generating set of the ideal and define $r_n=\lvert {r\in R: \deg(r)=n}\rvert $. Since $r_n=A_n/A_{n+1}$ is a finite-dimensional space we may assume $r_n<\infty$ for each $n$. Let $a_n=\dim_{\mathbb F_p}A_n/A_{n+1}$ and define the formal power series (called the Hilbert series) associated to the presentation $(U,R)$ of $A$
    \begin{equation}
        \text{Hilb}_A(t)=\sum_{n=1}^\infty a_nt^n \quad \text{and} \quad H_R(t)=\sum_{n=1}^\infty r_nt^n.
    \end{equation}
    Similarly, for a presentation $(X,R)$ of pro-p group $G$ define the series 
    \begin{equation}
        H_R^G(t)=\sum_{r\in R} t^{D(r)}.
    \end{equation}

The main tool for constructing the counterexample is the following theorem.

**Theorem.** (Golod-Shafarevich Inequality for Complete Filtered Algebras)

*Let $A=\mathbb F_p\langle\langle U\rangle\rangle/I$ be a complete filtered algebra and $R$ a generating set for the ideal $I$. Let the formal power series $H_R(t)$ and $\text{Hilb}_A(t)$ be as before. Then,* 
    \begin{equation}
        \frac{(1-\lvert U\rvert t+H_R(t))\cdot \text{Hilb}_A(t)}{1-t}\geq \frac{1}{1-t}.
    \end{equation}


I believe an elementary proof has never been published in English, only in the original paper [CITATION]. At some point, I hope to transcribe the proof, at which point I will update this post.

We now have a few simple corollaries. The first and second give better criteria for when a complete filtered algebra is infinite. The third extends these results to pro-p groups by their completed group algebras.

**Corollary 1** If we can find $\tau\in (0,1)$ such that $1-\lvert U\rvert \tau +H_R(\tau)\leq 0,$ then $\text{Hilb}_A(t)$ diverges and hence $A$ is infinite-dimensional.

*Proof.* Suppose we have $\tau\in (0,1)$ such that $1-\lvert U\rvert \tau+H_R(\tau)\leq 0$ but such that $\text{Hilb}_A(\tau)$ converges. Since $H_R(\tau)$ has non-negative coefficients, the above bound means it converges. Plugging into the Golod-Shafarevich inequality, this gives
    \begin{equation}
        \frac{(1-\lvert U\rvert \tau+H_R(\tau))\cdot \text{Hilb}_A(\tau)}{1-\tau}\geq \frac{1}{1-\tau}
    \end{equation}
    as an inequality of real numbers (not of power series as defined above). Hence, we obtain
    \begin{equation}
        (1-\lvert U\rvert \tau+H_R(\tau))\cdot \text{Hilb}_A(\tau)\geq 1.
    \end{equation}
    However, this is clearly a contradiction since $\text{Hilb}_A(\tau)>0$.

**Corollary 2**  Let $\mathcal A$ be a finite-dimensional complete filtered algebra with minimal presentation $(U,R)$ and assume $\lvert U\rvert \geq 2.$ By minimal, we mean that no proper subset of $U$ generates $\mathcal A.$ We have
    \begin{equation}
        \lvert R\rvert >\frac{\lvert U\rvert ^2}{4}.
    \end{equation}

*Proof.* If $\lvert R\rvert =\infty $ the statement is vacuously true since we always assume the generating set $U$ to be finite. Thus, without loss of generality, we can restrict to the case where $\lvert R\rvert <\infty$ and hence $H_R(t)<\infty$ is a finite sum. Recall the filtration ${\mathcal A_n}$ on $\mathcal A$. Since we assume $(U,R)$ to be minimal, we have $r_1=\lvert R\cap \mathcal A_1\rvert =0$ for otherwise one of the generators can be expressed as a power series of the others, contradicting the minimality of $(U,R).$ Now, for any $\tau >0$ we have $H_R(\tau)\leq \lvert R\rvert \tau^2$. Moreover, by Corollary 1 and the fact that $\mathcal A$ is assumed to be finite-dimensional, we have that $1-\lvert U\rvert \tau+H_R(\tau)>0$ giving
    \begin{equation}
        0<1-\lvert U\rvert \tau +H_R(\tau)\leq 1-\lvert U\rvert \tau + \lvert R\rvert \tau^2.
    \end{equation}
    Thus, setting $\tau = 2/\lvert U\rvert $ gives
    \begin{equation}
        1<\lvert R\rvert \frac{4}{U^2}\implies \lvert R\rvert >\frac{\lvert U\rvert ^2}{4}.
    \end{equation}

**Corollary 3** Let $G\cong \hat F_p(X)/N(R)$ be a pro-p group such that $X$ is minimal and finite. If $\lvert R\rvert \leq \lvert X\rvert ^2/4,$ then $G$ is infinite.

*Proof.* Suppose $G$ is a finite p-group. As before, if $\lvert R\rvert =\infty$ the claim is trivial so we may assume the presentation is finite. From the pair $(X,R)$ for $G$, we get the corresponding presentation $(U,{1-r:r\in R})$ for the completed group algebra $mathbb F_p[[G]]$ with $\lvert U\rvert =\lvert X\rvert $ and with $\lvert {1-r: r\in R} \rvert = \lvert R\rvert $. Since $\mathbb F_p[[G]]$ is finite-dimensional, we have from Corollary 1 that

\begin{equation}
    1-\lvert U\rvert t+H_R(t)>0
\end{equation}
    for all $t\in (0,1).$ Furthermore, since $X$ is assumed to be minimal, we have from the lemma that $\deg(1-r)\geq 2$ for all $r\in R$ yielding $H_R(t)\leq \lvert R\rvert t^2$ for $t>0.$ Hence, setting $t=2/\lvert X\rvert =2/\lvert U\rvert $ gives the result.

### Constructing a Counterexample

