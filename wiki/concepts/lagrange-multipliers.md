---
title: "Lagrange Multipliers"
module: general
type: concept
sources: [raw/analysis3/analysis_3_1.pdf]
updated: 2026-10-25
---

# Lagrange Multipliers

Related: [[multivariable-taylor-and-extrema]], [[implicit-function-theorem]],
[[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]].

## Setup

Find extrema of $f:\mathbb R^n\to\mathbb R$ on the constraint set
$G:=\{x\mid\mathbf g(x)=\mathbf 0\}$, $\mathbf g:\mathbb R^n\to\mathbb R^m$, $m<n$.

## Necessary condition

If $f,g_1,\dots,g_m\in C^1$, $x^0$ a local extremum on $G$ with
$\mathrm{rank}(J\mathbf g(x^0))=m$ (**regularity condition**), then there exist
$\lambda_1,\dots,\lambda_m$ (**Lagrange multipliers**) with
$$\mathrm{grad}\,f(x^0) + \sum_i\lambda_i\,\mathrm{grad}\,g_i(x^0) = \mathbf 0,$$
i.e. $x^0$ is a stationary point of the **Lagrange function**
$F(\mathbf x,\boldsymbol\lambda) := f(\mathbf x)+\sum_i\lambda_ig_i(\mathbf x)$.

## Sufficient condition

If additionally $H_F(x^0)$ (Hessian of the Lagrange function) is positive
(negative) definite on the tangent space
$TG(x^0):=\{y\mid\mathrm{grad}\,g_i(x^0)\cdot y=0\ \forall i\}$, then $x^0$ is a
strict local min (max) of $f$ on $G$.

## Practical recipe

1. Form $F(\mathbf x,\boldsymbol\lambda)=f(\mathbf x)+\sum\lambda_ig_i(\mathbf x)$.
2. Solve $\mathrm{grad}_{\mathbf x,\boldsymbol\lambda}F=\mathbf 0$ (generally
   nonlinear system in $\mathbf x$ and $\boldsymbol\lambda$).
3. Evaluate $f$ at each candidate to classify min/max (often easier than
   checking the sufficient condition directly).

## Worked examples

- $f(x,y)=xy$ on $x^2+y^2=1$: four critical points $(\pm1/\sqrt2,\pm1/\sqrt2)$,
  value $\pm1/2$.
- Can-minimization: $f(r,h)=2\pi r^2+2\pi rh$ subject to fixed volume
  $\pi r^2h=c$.
- $f(x,y,z)=2x+3y+2z$ on the intersection of a cylinder and a plane (two
  constraints, two multipliers).

Cross-checked against the user's own condensed notes in
[[analysis3-formulas-handwritten-sheet]].
