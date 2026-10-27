---
title: "Fixed-Point Iteration"
module: general
type: concept
sources: [raw/analysis1/analysis_1_2.pdf]
updated: 2026-10-25
---

# Fixed-Point Iteration

Related: [[banach-fixed-point-theorem]], [[sequences-and-convergence]],
[[analysis1-02-continuity-differentiability-taylor-fixedpoint]].

## Idea

Solve $f(x)=0$ by rewriting as a fixed-point problem $x=\Phi(x)$ and iterating
$x_{k+1}=\Phi(x_k)$, $k=0,1,2,\dots$. If $x_k\to x^*$ and $\Phi$ continuous, then
$x^*=\Phi(x^*)$. Newton's method is the special case $\Phi(x)=x-f(x)/f'(x)$.
**Caution:** the iteration function $\Phi$ for a given fixed-point problem is not
unique, and different choices can have very different convergence behavior (e.g.
$2x=\tan x \Rightarrow \Phi_1(x)=\frac12\tan x$ or $\Phi_2(x)=\arctan(2x)$).

## Lipschitz continuity & contractions

$\Phi$ is Lipschitz on $D$ with constant $L$ if $\|\Phi(x)-\Phi(y)\|\le L\|x-y\|$
for all $x,y\in D$; a **contraction** if additionally $L<1$. Lipschitz $\Rightarrow$
continuous. Every $C^1$ function $\Phi:[a,b]\to[a,b]$ is Lipschitz with
$L=\sup_{\xi\in[a,b]}|\Phi'(\xi)|$ (via the mean value theorem).

## Banach fixed-point theorem

See [[banach-fixed-point-theorem]]: a contraction $\Phi:D\to D$ on a complete,
nonempty, closed $D$ has a unique fixed point, reached from any starting point,
with explicit a priori/a posteriori error bounds.

## Cross-module confirmation

This entire concept (fixed-point problem, Lipschitz/contraction, Banach
fixed-point theorem, worked example $\Phi(x)=0.1\exp(x)$) was repeated verbatim as
Chapter 7 of Analysis 2 — see
[[analysis2-01-fixedpoint-recap-power-series]]. No discrepancies found between
the Analysis 1 and Analysis 2 presentations. Analysis 3 extends this theory to
systems of equations via [[multivariable-newton-method]].
