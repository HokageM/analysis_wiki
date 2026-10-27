---
title: "Sequences and Convergence"
module: general
type: concept
sources: [raw/analysis1/analysis_1_1.pdf]
updated: 2026-10-25
---

# Sequences and Convergence

Core concept page, updated across Analysis 1/2/3 as new sources are ingested.
Full derivations: [[analysis1-01-logic-sets-functions-numbers-sequences]].
Related: [[bolzano-weierstrass-theorem]], [[cauchy-convergence-criterion]],
[[series-and-convergence-tests]], [[real-numbers-and-axioms]].

## Definitions

A sequence in a normed vector space $(V,\|\cdot\|)$ is a map $\mathbb N\to V$. It is:
- **bounded**: $\exists C>0\,\forall n: \|a_n\|\le C$;
- **convergent** with limit $a$: $\forall\epsilon>0\,\exists N\,\forall n\ge N: \|a_n-a\|<\epsilon$, written $a_n\to a$;
- **Cauchy**: $\forall\epsilon>0\,\exists N\,\forall n,m\ge N: \|a_n-a_m\|<\epsilon$.

Basic facts: convergent $\Rightarrow$ bounded; convergent $\Rightarrow$ Cauchy; limits
are unique. Algebra of limits (sum, scalar multiple, product, quotient, radical)
holds for convergent sequences.

## Monotone real sequences

Monotone increasing + bounded above $\Rightarrow$ convergent, with limit
$= \sup\{a_n\}$ (uses completeness of $\mathbb R$; see [[real-numbers-and-axioms]]).
**Nested-interval principle**: monotone increasing $(a_n)$ and decreasing $(b_n)$
with $a_n\le b_n$, $b_n-a_n\to0$ converge to a common limit.

## Key theorems

- [[bolzano-weierstrass-theorem]]: every bounded real sequence has a convergent subsequence.
- [[cauchy-convergence-criterion]]: $\mathbb R$ (and every finite-dim. normed space) is complete — Cauchy $\iff$ convergent.

## Convergence speed

A convergent $(a_n)\to a$ is linearly convergent if $\|a_{n+1}-a\|\le C\|a_n-a\|$
for some $0<C<1$; superlinearly convergent for a null sequence $C_n$; convergent of
order $p>1$ if $\|a_{n+1}-a\|\le C\|a_n-a\|^p$. Relevant to root-finding methods:
the bisection method is linearly convergent; Newton's method is (typically)
convergent of order 2 near a simple root.

## Dependence on the norm

In **infinite-dimensional** spaces (e.g. $C[a,b]$), convergence genuinely depends
on the chosen norm — e.g. a "tent function" sequence converges to 0 in the
$L^2$-type norm but not in the maximum norm. In **finite-dimensional** spaces this
cannot happen: the norm equivalence theorem guarantees all norms induce the same
convergent sequences, and convergence in $\mathbb R^n$ reduces to componentwise
convergence in $\mathbb R$.

## Numerical root-finding as sequence constructions

- **Bisection method**: linearly convergent, robust, needs only continuity and a sign change.
- **Newton's method**: $x_{n+1}=x_n-f(x_n)/f'(x_n)$, needs differentiability, converges
  fast locally but may fail far from a root.

(Pseudocode for both given in [[analysis1-01-logic-sets-functions-numbers-sequences]].
Cross-checked against the user's own condensed notes in
[[analysis1-formulas-handwritten-sheet]].)
