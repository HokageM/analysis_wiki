---
title: "Cauchy Convergence Criterion"
module: general
type: theorem
sources: [raw/analysis1/analysis_1_1.pdf]
updated: 2026-10-25
---

# Cauchy Convergence Criterion

Used in: [[analysis1-01-logic-sets-functions-numbers-sequences]],
[[sequences-and-convergence]], [[bolzano-weierstrass-theorem]],
[[series-and-convergence-tests]].

## Statement

$\mathbb R$ is **complete**: every real Cauchy sequence converges. (A sequence
$(a_n)$ is Cauchy iff $\forall\epsilon>0\,\exists N\,\forall n,m\ge N: |a_n-a_m|<\epsilon$.)

## Proof

1. Every Cauchy sequence is bounded: for $\epsilon=1$ there is $N$ with
   $|a_n|=|a_n-a_N+a_N|\le|a_n-a_N|+|a_N|<1+|a_N|$ for $n\ge N$, and finitely many
   terms before $N$ are trivially bounded.
2. By boundedness and the [[bolzano-weierstrass-theorem]], $(a_n)$ has a convergent
   subsequence $(a_{n_k})\to\xi$ with accumulation point $\xi$.
3. For $m, n_k \ge N(\epsilon/2)$:
   $$|a_m-\xi| = |a_m-a_{n_k}+a_{n_k}-\xi| \le \underbrace{|a_m-a_{n_k}|}_{\text{Cauchy}} + \underbrace{|a_{n_k}-\xi|}_{\text{accumulation pt.}} < \tfrac\epsilon2+\tfrac\epsilon2=\epsilon.$$
   Hence $a_m \to \xi$. $\blacksquare$

## Consequence for series

A series $\sum a_k$ converges iff its partial sums form a Cauchy sequence:
$$\sum_{k=0}^\infty a_k \text{ convergent} \iff \forall\epsilon>0\,\exists N\,\forall m,n\ge N: \left|\sum_{k=n}^m a_k\right|<\epsilon.$$
This underlies the necessary condition ($a_k\to0$) and all the absolute-convergence
tests in [[series-and-convergence-tests]].

## Finite-dimensional vector spaces

In any finite-dimensional normed vector space $V$, the Cauchy criterion also holds
(componentwise, using the norm equivalence theorem): $(a_m)$ is Cauchy in $V$ iff
$\exists \mathbf a\in V: \mathbf a_m \to \mathbf a$.
