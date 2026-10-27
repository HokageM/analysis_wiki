---
title: "Functions"
module: general
type: concept
sources: [raw/analysis1/analysis_1_1.pdf]
updated: 2026-10-25
---

# Functions

Related: [[analysis1-01-logic-sets-functions-numbers-sequences]], [[logic-and-sets]].

## Core definitions

Function $f:M\to N$, domain/codomain, graph. Image $f(A)$ and preimage $f^{-1}(B)$.
Surjective / injective / bijective; inverse function $f^{-1}$ for injective $f$
(graph = reflection across $y=x$). Composition $g\circ f$: associative, generally
not commutative. The symmetric group $S(M)$ of bijections $M\to M$ satisfies the
group axioms.

## Elementary real functions catalog

Affine-linear, polynomials, exponential ($\exp(x)=e^x$, functional equation
$a^{x+y}=a^xa^y$), logarithm (inverse of exponential, $\log_a(xy)=\log_a x+\log_a y$),
trigonometric ($\sin,\cos$: Pythagorean identity, symmetry, periodicity, addition
theorems). These reappear as worked examples throughout later chapters (continuity,
differentiability, Taylor series) — update this page as later sources add
properties (e.g. derivatives, Taylor expansions).

**Continuity/differentiability of elementary functions** (added from
[[analysis1-02-continuity-differentiability-taylor-fixedpoint]]): all elementary
functions above are continuous on their natural domain and differentiable with
derivatives $\frac{d}{dx}e^x=e^x$, $\frac{d}{dx}\log x=1/x$,
$\frac{d}{dx}\sin x=\cos x$, $\frac{d}{dx}\cos x=-\sin x$,
$\frac{d}{dx}\tan x=1/\cos^2x$ (see [[differentiability]]). They are also **real
analytic** — equal to their own convergent Taylor series everywhere (see
[[taylor-series]]): $\exp(x)=\sum x^k/k!$, $\sin(x)=\sum(-1)^kx^{2k+1}/(2k+1)!$,
$\cos(x)=\sum(-1)^kx^{2k}/(2k)!$.
