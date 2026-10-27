---
title: "Multivariable Taylor's Theorem and Extrema"
module: general
type: concept
sources: [raw/analysis3/analysis_3_1.pdf]
updated: 2026-10-25
---

# Multivariable Taylor's Theorem and Extrema

Related: [[taylor-series]] (1D precursor),
[[multivariable-chain-rule-and-jacobian]],
[[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]],
[[lagrange-multipliers]].

## Multi-index Taylor's theorem

For $f\in C^{m+1}(D)$, $D\subset\mathbb R^n$ open convex, multi-index
$\alpha\in\mathbb N_0^n$:
$$f(x) = \sum_{|\alpha|\le m}\frac{D^\alpha f(x^0)}{\alpha!}(x-x^0)^\alpha + R_m(x;x^0), \qquad R_m(x;x^0) = \sum_{|\alpha|=m+1}\frac{D^\alpha f(x^0+\theta(x-x^0))}{\alpha!}(x-x^0)^\alpha$$
for some $\theta\in(0,1)$; $R_m = \mathcal O(\|x-x^0\|^{m+1})$.

**Degree-1:** $f(x) = f(x^0)+\mathrm{grad}\,f(x^0)\cdot(x-x^0)+\mathcal O(\|x-x^0\|^2)$.
**Degree-2 (Hesse matrix):**
$$f(x) = f(x^0) + \mathrm{grad}\,f(x^0)(x-x^0) + \tfrac12(x-x^0)^TH_f(x^0)(x-x^0) + \mathcal O(\|x-x^0\|^3),$$
with $H_f(x^0)$ the **Hessian** (Jacobian of the gradient), symmetric for $f\in C^2$
(Schwarz's theorem).

## Extrema via the Hessian

Necessary: local extremum at interior $x^0 \Rightarrow \mathrm{grad}\,f(x^0)=0$
(stationary point). Sufficient/necessary conditions via $H_f(x^0)$:

| $H_f(x^0)$ | Conclusion |
|---|---|
| positive definite | sufficient for strict local min |
| negative definite | sufficient for strict local max |
| positive/negative semidefinite | necessary (not sufficient) for local min/max |
| indefinite | **saddle point** |

Non-degenerate case ($\det H_f(x^0)\ne0$, all eigenvalues same sign ⟺ definite):
exactly 3 possibilities (min/max/saddle). **Growth estimate:** if $H_f(x^0)$
positive definite with smallest eigenvalue $\lambda_{\min}$, $f$ grows at least
quadratically away from $x^0$.

## Constrained extrema

See [[lagrange-multipliers]] for the extension of this machinery (Lagrange
function, its Hessian restricted to the tangent space of the constraint set) to
extrema under equality constraints.

Cross-checked against the user's own condensed notes in
[[analysis3-formulas-handwritten-sheet]].
