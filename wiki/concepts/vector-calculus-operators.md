---
title: "Vector Calculus Operators (div, curl, Laplacian)"
module: general
type: concept
sources: [raw/analysis3/analysis_3_1.pdf]
updated: 2026-10-25
---

# Vector Calculus Operators

Related: [[partial-derivatives-and-gradient]],
[[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]].

## Vector fields

$\mathbf f:D\to\mathbb R^n$ ($D\subset\mathbb R^n$ open) with $C^k$ components is
a $C^k$ vector field. Examples: fluid velocity fields, electromagnetic fields,
temperature gradients.

## Divergence

$$\mathrm{div}\,\mathbf f(x) := \sum_i\partial_{x_i}f_i(x) = \langle\nabla,\mathbf f(x)\rangle.$$
Linearity; $\mathrm{div}(\varphi\mathbf f)=\nabla\varphi\cdot\mathbf f+\varphi\,\mathrm{div}\,\mathbf f$;
and $\Delta f = \mathrm{div}(\mathrm{grad}\,f)$.

## Curl (rotation, $\mathbb R^3$ only)

$$\mathrm{rot}\,\mathbf f(x) := \nabla\times\mathbf f(x) = \left(\partial_{x_2}f_3-\partial_{x_3}f_2,\ \partial_{x_3}f_1-\partial_{x_1}f_3,\ \partial_{x_1}f_2-\partial_{x_2}f_1\right).$$
Linearity; $\mathrm{rot}(\varphi\mathbf f)=\nabla\varphi\times\mathbf f+\varphi\,\mathrm{rot}\,\mathbf f$.
**Key fact (via Schwarz's theorem):** $\mathrm{rot}(\mathrm{grad}\,f)=\mathbf 0$ —
every gradient field is curl-free/irrotational. (Expected to connect to Green's
theorem / Stokes' theorem later in the course, per the syllabus.)

## Laplacian

$$\Delta u = \sum_i\partial_{x_i}^2u = \mathrm{div}(\mathrm{grad}\,u).$$
PDEs: wave equation $\Delta u-\frac1{c^2}u_{tt}=0$; heat equation
$\Delta u-\frac1ku_t=0$; Laplace equation $\Delta u=0$ ($u$ harmonic). Radial
example: $u(x)=u(r)$, $r=\|x\|_2 \Rightarrow \Delta u=u''(r)+\frac{n-1}ru'(r)$.

**In curvilinear coordinates:** polar $\Delta=\partial_r^2+\frac1{r^2}\partial_\varphi^2+\frac1r\partial_r$;
spherical form given in
[[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]].
