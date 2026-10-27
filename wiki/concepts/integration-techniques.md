---
title: "Integration Techniques"
module: general
type: concept
sources: [raw/analysis2/analysis_2_2.pdf]
updated: 2026-10-25
---

# Integration Techniques

Related: [[analysis2-02-integration-curves-fourier-quadrature-fft]],
[[improper-integrals]], [[taylor-series]], [[numerical-quadrature]].

## Partial fraction decomposition

For rational $R=p/q$ with $\deg p\ge\deg q$: polynomial division first, then
decompose $p_2/q$ over the real/complex root factorization of $q$ (real roots →
$\alpha_j/(x-x_j)^k$ terms; complex-conjugate pairs → $(\gamma x+\delta)/((x-a)^2+b^2)^k$
terms), solving for coefficients via comparison of coefficients.

**Four basic antiderivative building blocks:**
1. $\int x^k\,dx = x^{k+1}/(k+1)+C$.
2. $\int (x-x_0)^{-\ell}dx = \log|x-x_0|+C$ ($\ell=1$) or $\frac{(x-x_0)^{1-\ell}}{1-\ell}+C$ ($\ell\ge2$).
3. $I_\ell=\int(x^2+1)^{-\ell}dx$: $I_1=\arctan x+C$; recursion for $\ell>1$.
4. $\int\frac{cx+d}{((x-a)^2+b^2)^\ell}dx$ — split via substitution into type 3.

## Substitution tricks

- $t=e^x$: turns $\int R(e^x)\,dx$ into $\int R(t)/t\,dt$.
- **Weierstraß substitution** $t=\tan(x/2)$: $\cos x = \frac{1-t^2}{1+t^2}$,
  $\sin x = \frac{2t}{1+t^2}$ — turns any $\int R(\cos x,\sin x)\,dx$ into a
  rational-function integral.

## Parameter-dependent integrals

$F(x)=\int_a^b f(x,y)\,dy$: continuous in $x$ if $f$ continuous on a compact
product set; differentiable with $F'(x)=\int_a^b\partial_xf(x,y)\,dy$ (Leibniz
rule) if $f,\partial_xf$ continuous. Extends to improper integrals under uniform
convergence (see [[improper-integrals]]). Key example: the Gamma function
$\Gamma(x)=\int_0^\infty e^{-t}t^{x-1}dt$, with $\Gamma(x+1)=x\Gamma(x)$,
$\Gamma(n)=(n-1)!$.
