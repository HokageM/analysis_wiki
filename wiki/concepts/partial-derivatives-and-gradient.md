---
title: "Partial Derivatives and Gradient"
module: general
type: concept
sources: [raw/analysis3/analysis_3_1.pdf]
updated: 2026-10-25
---

# Partial Derivatives and Gradient

Related: [[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]],
[[vector-calculus-operators]], [[multivariable-chain-rule-and-jacobian]],
[[differentiability]].

## Partial derivative

$$\frac{\partial f}{\partial x_i}(x^0) := \lim_{t\to0}\frac{f(x^0+te_i)-f(x^0)}{t}.$$
$f\in C^1$ if all partials exist and are continuous. **Partial differentiability
does NOT imply continuity** — classic counterexample
$f(x,y)=\frac{xy}{x^2+y^2}$ ($f(0,0):=0$): both partials exist everywhere, but $f$
is discontinuous at the origin.

## Gradient

$$\mathrm{grad}\,f(x^0) := \left(\partial_{x_1}f(x^0),\dots,\partial_{x_n}f(x^0)\right), \qquad \nabla := (\partial_{x_1},\dots,\partial_{x_n})^T.$$
Linearity, product, quotient rules carry over componentwise.

## Higher-order derivatives & Schwarz's theorem

For $f\in C^2$: $\partial^2f/\partial x_i\partial x_j = \partial^2f/\partial x_j\partial x_i$
(**Schwarz's theorem** — symmetry of mixed partials; fails without $C^2$). For
$C^k$ functions, mixed partials of order $\le k$ can be freely reordered.

## Directional derivative and steepest ascent

$$D_{\mathbf v}f(x^0) = \lim_{t\to0}\frac{f(x^0+t\mathbf v)-f(x^0)}t = \mathrm{grad}\,f(x^0)\cdot\mathbf v \ (\|\mathbf v\|=1).$$
**Gradient properties:** $\mathrm{grad}\,f(x^0)\perp$ level set through $x^0$;
by Cauchy–Schwarz, $|D_{\mathbf v}f(x^0)|\le\|\mathrm{grad}\,f(x^0)\|_2$ with
equality iff $\mathbf v$ points along the gradient — **the gradient is the
direction of steepest ascent**.

## Laplace operator

$$\Delta u := \sum_i\partial_{x_i}^2u = \mathrm{div}(\mathrm{grad}\,u).$$
Governs the wave equation, heat equation, and Laplace/potential equation
($\Delta u=0 \Leftrightarrow u$ **harmonic**). See [[vector-calculus-operators]].
