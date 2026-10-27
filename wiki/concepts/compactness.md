---
title: "Compactness"
module: general
type: concept
sources: [raw/analysis1/analysis_1_2.pdf]
updated: 2026-10-25
---

# Compactness

Related: [[continuity]], [[bolzano-weierstrass-theorem]],
[[analysis1-02-continuity-differentiability-taylor-fixedpoint]].

## Definition

$D\subset\mathbb R^n$ is compact iff every sequence in $D$ has a subsequence
converging to a point **in $D$** (sequential compactness).

## Equivalence theorem

For $D\subset\mathbb R^n$, the following are equivalent:
(a) $D$ compact; (b) $D$ closed and bounded; (c) Heine–Borel: every open cover of
$D$ has a finite subcover.

Proof sketch (a)$\Rightarrow$(b): unbounded $D$ gives a sequence with no bounded
(hence no convergent) subsequence; non-closed $D$ gives a sequence converging to a
point outside $D$, contradicting compactness. (b)$\Rightarrow$(a): bounded gives
(via [[bolzano-weierstrass-theorem]]) a convergent subsequence; closed ensures the
limit stays in $D$.

## Min-max / extreme value theorem

A continuous $f:D\to\mathbb R$ on a **compact** $D$ attains a global maximum and
minimum on $D$. Proof: let $s=\sup f(D)$ (finite since continuous image of a
sequence bounded by compactness-extracted subsequence argument), take a maximizing
sequence, extract a convergent subsequence via Bolzano–Weierstraß (using
compactness to stay inside $D$), use continuity to conclude $f$ attains $s$.

**Critical warning:** fails without compactness. Example: $f(x)=1/x$ on
$(0,\infty)$ (not closed/bounded) is continuous but has neither max nor min.

## Uniform continuity

Every continuous function on a compact set is uniformly continuous (see
[[continuity]]). This is why, e.g., a continuous function on a closed bounded
interval $[a,b]$ is automatically uniformly continuous, while the same function on
an open or unbounded interval may not be.
