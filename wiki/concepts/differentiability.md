---
title: "Differentiability"
module: general
type: concept
sources: [raw/analysis1/analysis_1_2.pdf]
updated: 2026-10-25
---

# Differentiability

Related: [[analysis1-02-continuity-differentiability-taylor-fixedpoint]],
[[continuity]], [[mean-value-theorems-and-extrema]], [[taylor-series]], [[functions]].

## Definition

$f$ differentiable at $x_0$: $f'(x_0) := \lim_{x\to x_0}\frac{f(x)-f(x_0)}{x-x_0}$
exists. One-sided derivatives $f'(x_0^\pm)$; differentiable iff both exist and agree.
**Differentiable $\Rightarrow$ continuous** (not conversely: $f(x)=|x|$).

## Rules

Linearity $(f+g)'=f'+g'$, $(\lambda f)'=\lambda f'$; **product rule**
$(fg)'=f'g+fg'$; **quotient rule** $(f/g)'=\frac{f'g-fg'}{g^2}$; **chain rule**
$(g\circ f)'(x_0)=g'(f(x_0))f'(x_0)$; **inverse function rule**
$(f^{-1})'(y_0)=1/f'(f^{-1}(y_0))$ (for strictly monotone, differentiable $f$ with
$f'\ne0$); generalized product rule for bilinear forms.

## Derivative table

| $f(x)$ | $f'(x)$ | domain |
|---|---|---|
| $x^\alpha$ | $\alpha x^{\alpha-1}$ | $\alpha\in\mathbb R, x>0$ |
| $e^x$ | $e^x$ | $x\in\mathbb R$ |
| $\log x$ | $1/x$ | $x>0$ |
| $\sin x$ | $\cos x$ | $x\in\mathbb R$ |
| $\cos x$ | $-\sin x$ | $x\in\mathbb R$ |
| $\tan x$ | $1/\cos^2x$ | $x\ne\pi/2+k\pi$ |

## Higher-order derivatives and smoothness classes

$f',f'',\dots,f^{(n)}$; $C^0,C^n,C^\infty$ classes. Used throughout
[[taylor-series]] and [[mean-value-theorems-and-extrema]] (second-derivative test,
convexity criterion, inflection-point criteria).
