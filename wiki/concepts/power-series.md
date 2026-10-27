---
title: "Power Series"
module: general
type: concept
sources: [raw/analysis2/analysis_2_1.pdf]
updated: 2026-10-25
---

# Power Series

Related: [[analysis2-01-fixedpoint-recap-power-series]], [[taylor-series]],
[[function-sequences-and-uniform-convergence]], [[series-and-convergence-tests]].

## Definition

$$f(z) = \sum_{k=0}^\infty a_k(z-z_0)^k, \qquad a_k,z_0,z\in\mathbb C.$$
Elementary functions ($\exp,\log,\sin,\cos,\dots$) are formally *defined* via
power series. This is the rigorous foundation beneath the Taylor series
discussed in [[taylor-series]] (a Taylor series is a power series with
$a_k=f^{(k)}(x_0)/k!$).

## Radius of convergence

There is $r\in[0,\infty]$ such that the series converges absolutely for
$|z-z_0|<r$ and diverges for $|z-z_0|>r$; convergence is **uniform** on every
closed sub-disc $\overline{K_\rho(z_0)}$, $\rho<r$ (proved via a geometric
majorant + Weierstraß M-test).

**Cauchy–Hadamard formula:**
$$r = \frac{1}{\limsup_{k\to\infty}\sqrt[k]{|a_k|}}$$
(equivalently $r=\lim|a_k/a_{k+1}|$ when that limit exists).

## Termwise differentiation (and integration)

$f$ is differentiable on $K_r(z_0)$ with
$$f'(z) = \sum_{k=1}^\infty k a_k(z-z_0)^{k-1},$$
and the differentiated (or integrated) series has the **same radius of
convergence** $r$ (since $\sqrt[k]{k}\to1$ doesn't change the Cauchy–Hadamard value).

## Worked radii

| Series | $r$ |
|---|---|
| $\sum k!\,z^k$ | $0$ |
| $\sum z^k$ | $1$ |
| $\sum z^k/k!$ | $\infty$ |

## Key derived expansions

$$\frac1{1-z}=\sum_{k=0}^\infty z^k\ (|z|<1), \qquad \frac1{(1-z)^2}=\sum_{k=1}^\infty kz^{k-1}, \qquad \log(1+x)=\sum_{k=0}^\infty\frac{(-1)^k}{k+1}x^{k+1}\ (-1<x<1).$$
