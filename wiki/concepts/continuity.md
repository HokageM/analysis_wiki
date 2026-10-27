---
title: "Continuity"
module: general
type: concept
sources: [raw/analysis1/analysis_1_2.pdf]
updated: 2026-10-25
---

# Continuity

Related: [[analysis1-02-continuity-differentiability-taylor-fixedpoint]],
[[compactness]], [[functions]], [[differentiability]],
[[function-sequences-and-uniform-convergence]].

## Definitions

Accumulation point, closure $\overline D=D\cup D'$, closed/open/bounded sets,
interior $D^0$. $\lim_{x\to x_0}f(x)=y_0$ (sequential definition, via all sequences
$x_n\to x_0$, $x_n\ne x_0$); one-sided limits. $f$ continuous at $x_0\in D\cap D'$
iff $\lim_{x\to x_0}f(x)=f(x_0)$.

**$\epsilon$-$\delta$ equivalence:** $f$ continuous at $x_0$ $\iff$
$\forall\epsilon>0\,\exists\delta>0\,\forall x\in D: \|x-x_0\|<\delta\Rightarrow\|f(x)-f(x_0)\|<\epsilon$.

## Closure properties

Constants, identity, polynomials, power series (within their domain of absolute
convergence), roots, $\log,\sin,\cos$ are continuous; sums, scalar multiples,
products, quotients (nonzero denominator), and compositions of continuous
functions are continuous.

## Uniform continuity

$\forall\epsilon\,\exists\delta\,\forall x,y\in D: \|x-y\|<\delta\Rightarrow\|f(x)-f(y)\|<\epsilon$
— $\delta$ independent of the point. Every continuous function on a **compact**
set is uniformly continuous (see [[compactness]]). Not every continuous function
is uniformly continuous on a non-compact domain (e.g. $1/x$ on $(0,1)$, $\exp(x)$
on $\mathbb R$).

## Key theorems for continuous functions on $[a,b]$

- Existence of a zero if $f(a)f(b)<0$.
- **Intermediate value theorem.**
- **Min-max theorem** (needs compactness — see [[compactness]]).
- Continuity of the inverse of a strictly monotone continuous function.

## Relation to uniform convergence of function sequences

A uniform limit of continuous functions is continuous (see
[[function-sequences-and-uniform-convergence]]) — this is how continuity of power
series sums (e.g. $\exp$, $\sin$, $\cos$) on their full domain of convergence is established.

Cross-checked against the user's own condensed notes in
[[analysis1-formulas-handwritten-sheet]].
