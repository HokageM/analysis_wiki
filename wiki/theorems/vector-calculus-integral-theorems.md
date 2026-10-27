---
title: "Vector Calculus Integral Theorems (Green, Gauss, Stokes)"
module: general
type: theorem
sources: [raw/analysis3/analysis_3_2.pdf]
updated: 2026-10-25
---

# Vector Calculus Integral Theorems (Green, Gauss, Stokes)

Related: [[curve-and-surface-integrals]], [[vector-calculus-operators]],
[[analysis3-02-multiple-integrals-fubini-curve-surface-green-gauss-stokes]].

## Potentials and conservative fields

$\mathbf f=\nabla\varphi$: **gradient/conservative field**, $\varphi$ its
**potential**. **Fundamental theorem for curve integrals:** if $\mathbf f$ has a
potential $\varphi$, $\int_c\mathbf f\,d\mathbf x=\varphi(c(b))-\varphi(c(a))$ for
any piecewise-$C^1$ curve $c$ (path-independent, and $\mathbf f$ curl-free);
conversely, curl-free (path-independent) $\mathbf f$ has a potential
$\varphi(\mathbf x)=\int_{c_{\mathbf x}}\mathbf f\,d\mathbf x$ (any path from a
fixed base point).

**Integrability condition:** $\mathbf f$ has a potential on $D$ iff $Jf$ is
symmetric ($\partial f_k/\partial x_j=\partial f_j/\partial x_k$), which for
$n=2,3$ coincides with $\mathrm{rot}(\mathbf f)=\mathbf 0$. **This is only
sufficient on a simply connected domain** — see the caveat in
[[curve-and-surface-integrals]] ($\mathrm{rot}=0$ pointwise does not suffice on
domains with "holes").

**Theorem (simply connected domains):** on simply connected $D$, curl-free
$\Rightarrow$ every closed-curve integral vanishes (resolves the apparent
counterexample: $\mathbb R^2\setminus\{0\}$ is not simply connected).

## Green's theorem (2D)

$$\oint_{\partial K}\mathbf f(\mathbf x)\,d\mathbf x = \int_K\mathrm{rot}(\mathbf f(\mathbf x))\,d\mathbf x$$
($K$ compact, $\partial K$ positively oriented so $K$ stays to the left).
Alternative (normal) form: $\oint_{\partial K}\langle\mathbf f,\mathbf n\rangle\,ds = \int_K\mathrm{div}(\mathbf f)\,d\mathbf x$
— the 2D special case of the divergence theorem; $\mathrm{div}\,\mathbf f=0$
("source-free"/solenoidal) $\Rightarrow$ zero net flux through any closed curve.

## Gauss's divergence theorem

$$\int_G\mathrm{div}(\mathbf f(\mathbf x))\,d\mathbf x = \oint_{\partial G}\mathbf f(\mathbf x)\,do$$
($G\subset\mathbb R^3$ compact with parametrizable boundary, outward normal).
Total divergence (sources) inside $G$ = net flux through $\partial G$.
Incompressible flow ($\mathrm{div}\,\mathbf f=0$) $\Rightarrow$ zero net flux
through any closed surface.

**Green's formulas (derived from Gauss, via $\mathbf F=f\nabla g$):**
$$\int_G(f\Delta g+\langle\nabla f,\nabla g\rangle)\,d\mathbf x = \oint_{\partial G}f\,\partial_{\mathbf n}g\,do, \qquad \int_G(f\Delta g-g\Delta f)\,d\mathbf x = \oint_{\partial G}(f\,\partial_{\mathbf n}g-g\,\partial_{\mathbf n}f)\,do.$$

## Stokes' theorem

$$\int_F\mathrm{rot}(\mathbf f(\mathbf x))\,do = \oint_{\partial F}\mathbf f(\mathbf x)\,d\mathbf x$$
($F$ a parametrized surface, $\partial F$ its induced boundary curve, consistently
oriented). Proof: convert the surface integral to a domain integral over the
parameter domain $K$, apply Green's theorem on $K$, map back via the
parametrization $\mathbf p$. Reduces to Green's theorem when $F$ is planar.

## Summary of the theorem hierarchy

Fundamental theorem of curve integrals (0D boundary of a curve) → Green's
theorem (1D boundary of a 2D region) → Gauss's theorem (2D boundary of a 3D
region) → Stokes' theorem (1D boundary of a 2D surface in 3D) are all instances
of a single underlying generalized Stokes/divergence pattern relating an
integral over a region to an integral over its boundary.

Cross-checked against the user's own condensed notes in
[[analysis3-formulas-handwritten-sheet]], including a personal note flagging the
simple-connectedness caveat for potentials.
