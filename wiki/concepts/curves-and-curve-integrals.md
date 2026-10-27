---
title: "Curves and Curve Integrals"
module: general
type: concept
sources: [raw/analysis2/analysis_2_2.pdf]
updated: 2026-10-25
---

# Curves and Curve Integrals

Related: [[analysis2-02-integration-curves-fourier-quadrature-fft]], [[functions]].

## Curves

$c:[a,b]\to\mathbb R^n$ continuous; $C^1$-curve if each component is continuously
differentiable; piecewise $C^1$; **smooth** if $\dot c(t)\ne0$ everywhere.
Reparametrization via continuous bijective monotone $h$ (or $C^1$ for $C^1$-curves).

## Arc length

$L(c)=\sup_Z L(Z)$ over partitions $Z$ (polygon approximations); for $C^1$-curves,
$$L(c) = \int_a^b\|\dot c(t)\|\,dt,$$
reparametrization-invariant. **Arc-length parametrization**
$\tilde c(s)=c(S^{-1}(s))$ with $S(t)=\int_a^t\|\dot c\|\,d\tau$: unit-speed
($\|\tilde c'(s)\|=1$), acceleration $\perp$ velocity.

**Curvature:** $\kappa(s)=\|\tilde c''(s)\|$ (arc-length parametrization); for a
function graph $y=y(x)$: $\kappa(x)=\dfrac{|y''(x)|}{(1+y'(x)^2)^{3/2}}$.

**Polar/spherical coordinates:** $L(c)=\int\sqrt{\dot r^2+r^2\dot\varphi^2}\,dt$
(polar); analogous 3D spherical formula.

**Enclosed area:** $F(c)=\frac12\int_a^b(x\dot y-\dot xy)\,dt$ for a closed $C^1$-curve.

## Curve (line) integrals

$$\int_c f\,ds := \int_a^b f(c(t))\|\dot c(t)\|\,dt$$
(parametrization-invariant). Applications: mass $\int_c\rho\,ds$, center of mass,
moment of inertia $\int_c\rho(x)r(x)^2\,ds$ of a wire with density $\rho$.

This is the "1st-kind" curve integral; Analysis 3 extends it to vector fields
("2nd-kind" curve integrals) and adds surface integrals — see
[[curve-and-surface-integrals]] and [[vector-calculus-integral-theorems]].
