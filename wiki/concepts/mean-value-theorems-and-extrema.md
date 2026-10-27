---
title: "Mean Value Theorems and Extrema"
module: general
type: concept
sources: [raw/analysis1/analysis_1_2.pdf]
updated: 2026-10-25
---

# Mean Value Theorems and Extrema

Related: [[differentiability]], [[taylor-series]],
[[analysis1-02-continuity-differentiability-taylor-fixedpoint]].

## Extrema

Necessary condition: local extremum at interior $x_0$ $\Rightarrow f'(x_0)=0$
(stationary point; converse false, e.g. $x^3$ at 0). Sufficient (second-derivative
test): $f''(x_0)>0\Rightarrow$ strict local min; $f''(x_0)<0\Rightarrow$ strict
local max. Generalized test when derivatives up to order $2n-1$ vanish: sign of
first nonzero even-order derivative $f^{(2n)}(x_0)$ decides min/max; if the first
nonvanishing derivative is odd-order, $x_0$ is an inflection point instead.

## Rolle's theorem & mean value theorems

- **Rolle:** $f(a)=f(b)\Rightarrow\exists x_0\in(a,b): f'(x_0)=0$.
- **First MVT:** $\exists x_0: f'(x_0)=\frac{f(b)-f(a)}{b-a}$.
- **Cauchy's (second) MVT:** $\exists x_0: \frac{f'(x_0)}{g'(x_0)}=\frac{f(b)-f(a)}{g(b)-g(a)}$ (for $g'\ne0$).

**Corollaries:** sign of $f'$ on an interval determines monotonicity (constant if
$f'\equiv0$; increasing/decreasing per sign of $f'$).

## Convexity / concavity / inflection points

$f\in C^2$: convex $\iff f''\ge0$; concave $\iff f''\le0$. Inflection point:
necessary $f''(x_0)=0$; sufficient (for $C^3$) $f''(x_0)=0\wedge f'''(x_0)\ne0$.

## L'Hôpital's rule

For $\frac00,\frac\infty\infty$ forms: $\lim\frac{f}{g}=\lim\frac{f'}{g'}$ (if RHS
limit exists); proved via Cauchy's MVT; variants for one-sided and $x\to\pm\infty$ limits.

## Curve sketching checklist (Kurvendiskussion)

Domain/range → symmetry → poles → asymptotic behavior/asymptotes → zeros → local
extrema → monotonicity → inflection points → sketch. (Full worked example in
[[analysis1-02-continuity-differentiability-taylor-fixedpoint]].)
