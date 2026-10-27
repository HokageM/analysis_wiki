---
title: "Numerical Quadrature"
module: general
type: concept
sources: [raw/analysis2/analysis_2_2.pdf]
updated: 2026-10-25
---

# Numerical Quadrature

Related: [[analysis2-02-integration-curves-fourier-quadrature-fft]],
[[taylor-series]] (interpolation error formula), [[integration-techniques]].

## Setup

Approximate $I[f]=\int_a^bf(x)\,dx$ by $I_n[f]=\sum_{i=0}^n g_if(x_i)$ (nodes
$x_i$, weights $g_i$). Both families below are built from [[interpolation]]
(Newton–Cotes directly; Gauss quadrature via orthogonal-polynomial roots).

## Newton–Cotes formulas (equidistant nodes)

Built by integrating the Lagrange interpolation polynomial through $(x_i,f(x_i))$.

| $n$ | Rule | Formula | Error $R_n[f]$ |
|---|---|---|---|
| 1 | Trapezoidal | $(b-a)\frac{f(a)+f(b)}2$ | $\frac{h^3}{12}f^{(2)}(\xi)$ |
| 2 | Simpson | $\frac{b-a}6(f(a)+4f(\tfrac{a+b}2)+f(b))$ | $\frac{h^5}{90}f^{(4)}(\xi)$ |
| 3 | 3/8-rule | — | $\frac{h^5}{80}f^{(4)}(\xi)$ |
| 4 | Milne | — | $\frac{h^7}{945}f^{(6)}(\xi)$ |

Newton–Cotes with $n+1$ nodes integrates $\mathcal P_n$ exactly ($h=(b-a)/n$).

**Composite rules:** subdivide $[a,b]$ into $N$ panels, apply a fixed rule per
panel. Composite trapezoidal error $\le\frac{h^2}{12}(b-a)\|f^{(2)}\|_\infty$;
composite Simpson error $\le\frac{h^4}{180}(b-a)\|f^{(4)}\|_\infty$.

## Gauss quadrature

**Idea:** vary the nodes (not just equidistant) to maximize exactness degree for
$I[f]=\int_a^bf(x)w(x)\,dx$ (weight function $w>0$). **Result:** $n+1$ nodes (zeros
of the degree-$(n+1)$ orthogonal polynomial for weight $w$) integrate
$\mathcal P_{2n+1}$ exactly — double the degree of Newton–Cotes for the same node count.

| Name | Interval | Weight $w(x)$ | Polynomial family |
|---|---|---|---|
| Gauss–Legendre | $[-1,1]$ | $1$ | Legendre $L_n$ |
| Gauss–Chebyshev | $[-1,1]$ | $1/\sqrt{1-x^2}$ | Chebyshev $T_n$ |
| Gauss–Jacobi | $[-1,1]$ | $(1-x)(1+x)$ | Jacobi |
| Gauss–Laguerre | $[0,\infty)$ | $e^{-x}$ | Laguerre |
| Gauss–Hermite | $(-\infty,\infty)$ | $e^{-x^2}$ | Hermite |

Chebyshev: $T_n(x)=\cos(n\arccos x)$, recursion $T_{k+1}=2xT_k-T_{k-1}$; Gauss–
Chebyshev nodes $x_i=\cos\frac{(2i+1)\pi}{2n+2}$, constant weights $\pi/(n+1)$.
Legendre: $L_n(x)=\frac1{2^nn!}\frac{d^n}{dx^n}(x^2-1)^n$, recursion
$L_{n+1}=\frac{2n+1}{n+1}xL_n-\frac{n}{n+1}L_{n-1}$.
