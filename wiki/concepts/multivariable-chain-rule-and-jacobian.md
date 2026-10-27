---
title: "Multivariable Chain Rule and the Jacobian"
module: general
type: concept
sources: [raw/analysis3/analysis_3_1.pdf]
updated: 2026-10-25
---

# Multivariable Chain Rule and the Jacobian

Related: [[partial-derivatives-and-gradient]],
[[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]],
[[implicit-function-theorem]], [[multivariable-newton-method]].

## Total differentiability

$f:D\to\mathbb R^m$ is (totally) differentiable at $x^0$ if
$f(x)=f(x^0)+A(x-x^0)+o(\|x-x^0\|)$ for a (unique) matrix $A=Jf(x^0)$, the
**Jacobi matrix**:
$$Jf(x^0) = \begin{pmatrix}\mathrm{grad}\,f_1(x^0)\\\vdots\\\mathrm{grad}\,f_m(x^0)\end{pmatrix}\in\mathbb R^{m\times n}.$$

**Theorem:** differentiable $\Rightarrow$ continuous; differentiable
$\Rightarrow$ all partials exist (giving $Jf$ as above); $f\in C^1 \Rightarrow$
differentiable (continuity of partials upgrades partial to total
differentiability — mirrors the warning in [[partial-derivatives-and-gradient]]
that partial differentiability alone is not enough).

## Chain rule

$$J(g\circ f)(x^0) = Jg(f(x^0))\cdot Jf(x^0).$$
Special case (curve composition): $(f\circ h)'(t_0) = \mathrm{grad}\,f(h(t_0))\cdot h'(t_0)$.

## Curvilinear coordinates

For a regular $C^1$ coordinate change $x=\Phi(u)$: chain rule gives
$\partial f/\partial u_i = \sum_jg^{ij}\partial f/\partial x_j$ with
$(g^{ij})=(J\Phi)^T$. Worked out explicitly for polar and spherical coordinates
(Jacobians and transformed Laplacians) in
[[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]].

## Mean value theorems (multivariable)

- **Scalar MVT:** $f(b)-f(a)=\mathrm{grad}\,f(a+\theta(b-a))\cdot(b-a)$ for some
  $\theta\in(0,1)$ — **only valid for scalar-valued $f$**, fails for
  vector-valued functions (counterexample: a circular arc parametrization).
- **Mean value estimate (vector-valued):**
  $\|f(b)-f(a)\|_2 \le \sup_{t\in[0,1]}\|Jf(a+t(b-a))\|_2\|b-a\|_2$.

## Inverse function theorem

If $Jf(x^0)$ is regular, $f$ is locally a $C^1$-diffeomorphism near $x^0$, with
$Jf^{-1}(y)=(Jf(f^{-1}(y)))^{-1}$ — proved via the
[[implicit-function-theorem]] applied to $g(x,y):=y-f(x)$.
