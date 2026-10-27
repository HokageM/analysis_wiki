---
title: "Implicit Function Theorem"
module: general
type: theorem
sources: [raw/analysis3/analysis_3_1.pdf]
updated: 2026-10-25
---

# Implicit Function Theorem

Related: [[multivariable-chain-rule-and-jacobian]],
[[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]],
[[lagrange-multipliers]].

## Statement

Let $\mathbf g:D\to\mathbb R^m$ be $C^1$, $D\subset\mathbb R^{n-m}\times\mathbb R^m$
open, $(\mathbf x^0,\mathbf y^0)\in D$ with $\mathbf g(\mathbf x^0,\mathbf y^0)=\mathbf 0$,
and suppose $\partial\mathbf g/\partial\mathbf y(\mathbf x^0,\mathbf y^0)$ (the
$m\times m$ block) is **regular**. Then there exist neighborhoods $U\ni\mathbf x^0$,
$V\ni\mathbf y^0$ and a unique $C^1$-function $\mathbf f:U\to V$ with
$\mathbf f(\mathbf x^0)=\mathbf y^0$, $\mathbf g(\mathbf x,\mathbf f(\mathbf x))=\mathbf 0\ \forall\mathbf x\in U$, and
$$J\mathbf f(\mathbf x) = -\left(\frac{\partial\mathbf g}{\partial\mathbf y}\right)^{-1}\frac{\partial\mathbf g}{\partial\mathbf x}\bigg|_{(\mathbf x,\mathbf f(\mathbf x))}.$$

## Worked examples

- Circle $g(x,y)=x^2+y^2-r^2=0$: solvable near $(x^0,r)$ since $g_y=2r\ne0$,
  giving $y=\sqrt{r^2-x^2}$ explicitly.
- Transcendental $g(x,y)=e^{y-x}+3y+x^2-1=0$: not explicitly solvable, but
  implicit differentiation gives $y'=-g_x/g_y$ and a general second-derivative
  formula $y''=\frac{-g_{xx}g_y^2-2g_{xy}g_xg_y-g_{yy}g_x^2}{g_y^3}$.

## Implicit curves/surfaces

A point $(x^0,y^0)$ on $\{g=0\}$ is **regular** if $\mathrm{grad}\,g\ne0$ there
(curve is locally a graph), else **singular**. Singular-point classification via
$\det H_g$: $>0$ isolated point, $<0$ double point, $=0$ cusp. Analogous theory
for implicit surfaces $g(x,y,z)=0$ in $\mathbb R^3$ (tangent plane
$\mathrm{grad}\,g(x^0)\cdot\Delta x=0$).

## Consequence: inverse function theorem

Applying this theorem to $\mathbf g(\mathbf x,\mathbf y):=\mathbf y-\mathbf f(\mathbf x)$:
if $Jf(x^0)$ is regular, $f$ is locally invertible with $C^1$ inverse
(local diffeomorphism) — see [[multivariable-chain-rule-and-jacobian]].
