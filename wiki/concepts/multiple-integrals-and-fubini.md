---
title: "Multiple Integrals and Fubini's Theorem"
module: general
type: concept
sources: [raw/analysis3/analysis_3_2.pdf]
updated: 2026-10-25
---

# Multiple Integrals and Fubini's Theorem

Related:
[[analysis3-02-multiple-integrals-fubini-curve-surface-green-gauss-stokes]],
[[numerical-quadrature]] (1D precursor to Riemann sums), [[curve-and-surface-integrals]].

## Construction

Partition a box $D\subset\mathbb R^n$, form upper/lower Riemann sums
$U_f(Z)\le R_f(Z)\le O_f(Z)$; refining partitions make $U_f$ increase, $O_f$
decrease; $f$ is **Riemann-integrable** if $\sup_ZU_f(Z)=\inf_ZO_f(Z)=:\int_Df\,dx$.
**Riemann criterion:** integrable iff $\forall\epsilon\,\exists Z: O_f(Z)-U_f(Z)<\epsilon$.
Elementary properties: linearity, monotonicity, positivity, additivity over
non-overlapping sub-domains, estimate $|\int_Df|\le\sup|f|\cdot\mathrm{vol}(D)$.

## Fubini's theorem

$$\int_D f(\mathbf x)\,d\mathbf x = \int_{a_1}^{b_1}\int_{a_2}^{b_2}f(x,y)\,dy\,dx = \int_{a_2}^{b_2}\int_{a_1}^{b_1}f(x,y)\,dx\,dy$$
(reduces multi-D integration to iterated 1D integration; existence of the
iterated integrals alone does not imply integrability of $f$ — must be
established separately, e.g. via continuity).

## Measurability, null sets, normal domains

$D$ measurable if $\mathrm{vol}(D)=\int_D1\,dx$ exists; **null set** if
measurable with volume 0. Key facts: compact $D$ measurable iff $\partial D$ is a
null set; continuous $f$ on compact measurable $D$ is integrable; **mean value
theorem** $\exists\xi\in D: \int_Df\,dx=f(\xi)\mathrm{vol}(D)$ (connected case).

**Normal domain** $D=\{(x,y)\mid a\le x\le b,\ g(x)\le y\le h(x)\}$:
$$\int_Df(x,y)\,dx\,dy = \int_a^b\int_{g(x)}^{h(x)}f(x,y)\,dy\,dx.$$
Generalizes to **projectable sets** in $\mathbb R^n$.

## Applications

**Center of mass** $\mathbf x_s = \int_D\rho(x)x\,dx / \int_D\rho(x)\,dx$.
**Moment of inertia** $\Theta=\int_D\rho(x)r(x)^2\,dx$.
**Steiner's (parallel axis) theorem:** $\Theta_A=md^2+\Theta_S$.

## Transformation (substitution) theorem

For a $C^1$-diffeomorphism $\Phi$:
$$\int_{\Phi(D)}f(\mathbf x)\,d\mathbf x = \int_D f(\Phi(\mathbf u))\,|\det J\Phi(\mathbf u)|\,d\mathbf u$$
(bijectivity only needed on $D^0$, not $\partial D$). Key applications: polar/
spherical-coordinate integrals (centroids, moments), and the **Gaussian
integral** $\int_0^\infty e^{-x^2}dx=\sqrt\pi/2$ via squaring + polar substitution.
