---
title: "Multivariable Newton's Method and Gauss–Newton"
module: general
type: concept
sources: [raw/analysis3/analysis_3_1.pdf]
updated: 2026-10-25
---

# Multivariable Newton's Method and Gauss–Newton

Related: [[fixed-point-iteration]], [[banach-fixed-point-theorem]],
[[multivariable-chain-rule-and-jacobian]],
[[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]].

## Newton's method for $f(\mathbf x)=\mathbf 0$

Linearize via Taylor: $f(x)\approx f(x^k)+Jf(x^k)(x-x^k)$; solve for the
**Newton correction** $\Delta x^k$:
$$Jf(x^k)\,\Delta x^k = -f(x^k), \qquad x^{k+1} := x^k+\Delta x^k.$$
One linear system per iteration. **Invariant under linear transformations**
$f\to Af$ ($A$ regular) — same iterates as for $f$ alone.

```
FOR k = 0, 1, 2, ...:
    Solve  Jf(x^k) * dx^k = -f(x^k)
    x^(k+1) := x^k + dx^k
```

## Local quadratic convergence

If $Jf(x^*)$ regular at a zero $x^*$ and $(Jf)^{-1}$ Lipschitz near $x^*$, then
for $x^0$ sufficiently close to $x^*$, Newton's method converges **quadratically**
and $x^*$ is the unique zero in that neighborhood (cf.
[[banach-fixed-point-theorem]] for the analogous fixed-point convergence
machinery, and [[taylor-series]] for the 1D quadratic-convergence result that
this generalizes).

## Damped Newton's method (global convergence)

Pure Newton is only locally convergent. **Damping:**
$x^{k+1}:=x^k+\lambda_k\Delta x^k$, $\lambda_k\in(0,1]$, chosen via the test
function $T(x):=\|f(x)\|_2^2$ so that $T(x^{k+1})<T(x^k)$ strictly decreases.
Existence of a valid $\mu_k>0$ is guaranteed (via $\varphi'(0)<0$ for
$\varphi(\lambda):=\|f(x^k+\lambda\Delta x^k)\|_2^2$). See full damping-strategy
pseudocode in
[[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]].

## Gauss–Newton (nonlinear least squares)

**Problem:** fit $y=f(t;\mathbf x)$ to data $(t_i,y_i)_{i=1}^m$ ($m\gg n$) by
minimizing $g(\mathbf x)=\|\mathbf F(\mathbf x)-\mathbf y\|_2^2$.
**Algorithm:** linearize $\mathbf F$, solve a **linear least-squares** problem
for $\Delta x$ each iteration:
```
FOR k = 0, 1, 2, ...:
    Solve (linear least squares):  minimize_dx || JF(x^k) dx - (y - F(x^k)) ||_2^2
    x^(k+1) := x^k + dx
```
Worked example: fitting $y=x_1+x_2\exp(tx_3)$ to 5 data points converges in 13
iterations.
