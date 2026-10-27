---
title: "Taylor Series"
module: general
type: concept
sources: [raw/analysis1/analysis_1_2.pdf]
updated: 2026-10-25
---

# Taylor Series

Related: [[differentiability]], [[mean-value-theorems-and-extrema]],
[[series-and-convergence-tests]],
[[analysis1-02-continuity-differentiability-taylor-fixedpoint]].

## Taylor's theorem

For $f\in C^{n+1}([a,b])$, $x_0\in(a,b)$:
$$f(x) = T_n(x;x_0)+R_n(x;x_0), \qquad T_n(x;x_0)=\sum_{k=0}^n\frac{f^{(k)}(x_0)}{k!}(x-x_0)^k.$$

Remainder forms: **Lagrange** $R_n=\frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}$;
**integral** $R_n=\frac1{n!}\int_{x_0}^x(x-t)^nf^{(n+1)}(t)\,dt$; **Cauchy**
$R_n=\frac{f^{(n+1)}(\xi)}{n!}(x-x_0)^{n+1}(1-\theta)^n$; **Schlömilch**
(generalizes both, parameter $p$). $T_n$ is the unique degree-$n$ polynomial
matching $f^{(j)}(x_0)$ for $j=0,\dots,n$.

## Taylor series vs. real-analytic functions

$T_\infty(x;x_0)=\sum_{k=0}^\infty\frac{f^{(k)}(x_0)}{k!}(x-x_0)^k$. A $C^\infty$
function's Taylor series need **not converge**, and even if convergent need **not
equal $f$**. If it does (locally), $f$ is *real analytic*. Canonical convergent
examples: $\exp,\sin,\cos$ (converge everywhere on $\mathbb R$/$\mathbb C$ and equal
the original function).

## Key worked expansions (around 0)

$$\exp(x)=\sum_{k=0}^n\frac{x^k}{k!}+R_n, \qquad \sin(x)=\sum_{k=0}^n(-1)^k\frac{x^{2k+1}}{(2k+1)!}+R_{2n+2}.$$

## Corollaries

- $f\in C^{n+1}$ with $f^{(n+1)}\equiv0 \Rightarrow f$ is a polynomial of degree $\le n$.
- A degree-$n$ polynomial equals its own degree-$n$ Taylor polynomial about any point.
- **Newton's method converges quadratically** near a simple root (via 2nd-order Taylor expansion):
  $$x_{n+1}-x^* = \frac{f''(\xi_n)}{2f'(x_n)}(x_n-x^*)^2.$$

## Pseudocode: Horner's scheme (stable polynomial evaluation, used alongside Taylor polynomials)

```
y := a_n
for k = n-1, n-2, ..., 0:
    y := a_k + (x - x0) * y
# result: y = p(x)
```

Cross-checked against the user's own condensed notes in
[[analysis1-formulas-handwritten-sheet]].
