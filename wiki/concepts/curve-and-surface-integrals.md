---
title: "Curve and Surface Integrals (2nd Kind)"
module: general
type: concept
sources: [raw/analysis3/analysis_3_2.pdf]
updated: 2026-10-25
---

# Curve and Surface Integrals (2nd Kind)

Related: [[curves-and-curve-integrals]] (1st-kind curve integrals),
[[vector-calculus-integral-theorems]],
[[analysis3-02-multiple-integrals-fubini-curve-surface-green-gauss-stokes]].

## Curve integral of the 2nd kind

For vector field $\mathbf f$, curve $c:[a,b]\to D$:
$$\int_c\mathbf f(\mathbf x)\,d\mathbf x := \int_a^b\langle\mathbf f(c(t)),\dot c(t)\rangle\,dt$$
(work done by a force field along a path). Linear, orientation-reversing under
$-c$, additive over concatenated paths, parametrization-invariant. Relation to
1st-kind integral: $\int_c\mathbf f\,d\mathbf x = \int_c\langle\mathbf f,\mathbf T\rangle\,ds$
(unit tangent $\mathbf T$). **Circulation:** $\oint_c\mathbf u\,d\mathbf x$ for a
closed curve $c$ in a flow field $\mathbf u$.

**Curl-free / path-independent fields:** $\mathbf f$ is curl-free if
$\oint_c\mathbf f\,d\mathbf x=0$ for every closed curve in $D$ (equivalently,
path-independence). **Critical subtlety:** $\mathrm{rot}(\mathbf f)=0$ pointwise
does **not** imply curl-free in this sense unless $D$ is **simply connected**
(e.g. the field $\mathbf f=(-y,x)/(x^2+y^2)$ on $\mathbb R^2\setminus\{0\}$ has
$\mathrm{rot}\,\mathbf f=0$ but nonzero circulation around the origin). See
[[vector-calculus-integral-theorems]] for the precise theorem.

## Surface parametrization

$\mathbf p:D\to\mathbb R^3$, $C^1$, linearly independent partials
$\partial_{u_1}\mathbf p,\partial_{u_2}\mathbf p$ (tangent plane spanned by
these). **Surface element:**
$$do = \left\|\partial_{u_1}\mathbf p\times\partial_{u_2}\mathbf p\right\|d\mathbf u = \sqrt{EG-F^2}\,d\mathbf u$$
(first fundamental form $E,F,G$; parametrization-independent by the
transformation theorem). For a graph $x_3=\varphi(x_1,x_2)$:
$do=\sqrt{1+\varphi_{x_1}^2+\varphi_{x_2}^2}\,d(x_1,x_2)$.

## Surface integrals

**1st kind (scalar):** $\int_Ff(\mathbf x)\,do = \int_Kf(\mathbf p(\mathbf u))\|\partial_{u_1}\mathbf p\times\partial_{u_2}\mathbf p\|\,d\mathbf u$
— total mass if $f=\rho$ (density).
**2nd kind (vector field):**
$$\int_F\mathbf f(\mathbf x)\,d\mathbf x := \int_K\langle\mathbf f(\mathbf p(\mathbf u)),\partial_{u_1}\mathbf p\times\partial_{u_2}\mathbf p\rangle\,d\mathbf u = \int_F\langle\mathbf f,\mathbf n\rangle\,do$$
(unit normal $\mathbf n$, chosen outward for closed surfaces) — volumetric
**flux** of $\mathbf f$ through $F$ if $\mathbf f$ is a velocity field.

## Why this matters

Curve integrals (2nd kind) feed into the fundamental theorem for curve
integrals and Green's theorem; surface integrals (2nd kind) feed into Gauss's
and Stokes' theorems — see [[vector-calculus-integral-theorems]].
