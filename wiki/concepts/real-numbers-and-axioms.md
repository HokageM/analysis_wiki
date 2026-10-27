---
title: "Real Numbers and Field/Order/Completeness Axioms"
module: general
type: concept
sources: [raw/analysis1/analysis_1_1.pdf]
updated: 2026-10-25
---

# Real Numbers and Axioms

Related: [[analysis1-01-logic-sets-functions-numbers-sequences]],
[[sequences-and-convergence]].

## Number tower

$\mathbb N \subset \mathbb N_0 \subset \mathbb Z \subset \mathbb Q \subset \mathbb R \subset \mathbb C$
(complex numbers appear in examples, e.g. $a_n=i^n$, but are not yet formally defined
in this source). $\mathbb N$ is defined via the **Peano axioms**; $\mathbb Q$ is an
ordered field but is **not complete** (e.g. $\sqrt2\notin\mathbb Q$).

## Axioms of $\mathbb R$

- (I) Abelian group under $+$; (II) commutative group under $\cdot$ (for nonzero
  elements); (III) distributivity $\Rightarrow$ $\mathbb R$ is a **field**.
- (IV) Order axioms (totality, compatibility with $+,\cdot$) $\Rightarrow$ $\mathbb R$
  is an **ordered field**.
- (V) **Dedekind completeness**: every cut $\mathbb R=L\cup R$ has a cut number.
  Equivalent form used throughout analysis: every nonempty, bounded-above subset of
  $\mathbb R$ has a supremum (least upper bound).

## Supremum / infimum

Upper/lower bound, bounded above/below, supremum (least upper bound), infimum
(greatest lower bound) — see worked definitions in
[[analysis1-01-logic-sets-functions-numbers-sequences]]. Consequences of
completeness: $\mathbb N$ unbounded above (Archimedean property); density of
$\mathbb Q$ in $\mathbb R$.

## Absolute value

$|a|$, triangle inequality $|a+b|\le|a|+|b|$, $\epsilon$-neighborhoods
$U_\epsilon(a)=(a-\epsilon,a+\epsilon)$ — foundational for all $\epsilon$-$N$ and
$\epsilon$-$\delta$ definitions later (convergence, continuity, limits).

## Why this matters for the rest of the wiki

Completeness (V) is the single axiom that distinguishes $\mathbb R$ from $\mathbb Q$
and underlies: monotone bounded sequences converge; the
[[bolzano-weierstrass-theorem]]; the [[cauchy-convergence-criterion]]; and (in
later Analysis modules) the intermediate value theorem and existence of extrema of
continuous functions on compact intervals.
