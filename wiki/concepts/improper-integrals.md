---
title: "Improper Integrals"
module: general
type: concept
sources: [raw/analysis2/analysis_2_2.pdf]
updated: 2026-10-25
---

# Improper Integrals

Related: [[integration-techniques]],
[[analysis2-02-integration-curves-fourier-quadrature-fft]],
[[series-and-convergence-tests]] (the convergence theory closely parallels series).

## Definitions

$$\int_a^\infty f\,dx := \lim_{b\to\infty}\int_a^b f\,dx, \qquad \int_{-\infty}^b f\,dx := \lim_{a\to-\infty}\int_a^b f\,dx, \qquad \int_{-\infty}^\infty f := \int_{-\infty}^a f + \int_a^\infty f.$$
$f$ is **locally integrable** on $D$ if integrable on every compact subinterval.

## Convergence criteria (parallel to series)

- **Cauchy criterion:** $\int_a^\infty f\,dx$ exists iff
  $\forall\epsilon\,\exists C\,\forall z_1,z_2>C: |\int_{z_1}^{z_2}f\,dx|<\epsilon$.
- **Absolute convergence:** $\int|f|\,dx$ convergent $\Rightarrow\int f\,dx$ convergent.
- **Majorant/minorant criterion:** $|f|\le g$, $\int g$ convergent $\Rightarrow\int f$
  absolutely convergent; $0\le g\le f$, $\int g$ divergent $\Rightarrow\int f$ divergent.

## Key worked examples

- $\int_1^\infty x^{-\alpha}dx$ convergent iff $\alpha>1$.
- **Dirichlet integral** $\int_0^\infty\frac{\sin x}xdx=\pi/2$: convergent but
  **not absolutely convergent** (parallels the alternating harmonic series in
  [[series-and-convergence-tests]]).
- **Gamma function** $\Gamma(x)=\int_0^\infty e^{-t}t^{x-1}dt$ ($x>0$): absolutely
  convergent via majorant bounds at both the $t\to0^+$ singularity and $t\to\infty$.

## Parameter-dependent improper integrals

$F(x)=\int_a^\infty f(x,y)\,dy$ is **uniformly convergent** if
$\forall\epsilon\,\exists C\,\forall x\in I,y_1,y_2>C: |\int_{y_1}^{y_2}f(x,y)\,dy|<\epsilon$;
majorant criterion, continuity, and Leibniz differentiation theorems all extend
from the eigentlich (proper) case — see [[integration-techniques]].
