---
title: "Fourier Series"
module: general
type: concept
sources: [raw/analysis2/analysis_2_2.pdf]
updated: 2026-10-25
---

# Fourier Series

Related: [[analysis2-02-integration-curves-fourier-quadrature-fft]],
[[power-series]], [[series-and-convergence-tests]], [[fast-fourier-transform]].

## Definitions

$T$-periodic $f$; $\omega=2\pi/T$. Real form:
$$f(t) = \frac{a_0}2+\sum_{k=1}^\infty[a_k\cos(k\omega t)+b_k\sin(k\omega t)].$$
Complex form (via Euler's formula): $f(t)=\sum_{k=-\infty}^\infty\gamma_ke^{ik\omega t}$,
$\gamma_0=a_0/2$, $\gamma_k=\tfrac12(a_k-ib_k)$, $\gamma_{-k}=\tfrac12(a_k+ib_k)$.

**Fourier coefficients:** $\gamma_k = \frac1T\int_0^T f(t)e^{-ik\omega t}dt$;
$a_k=\frac2T\int_0^Tf(t)\cos(k\omega t)dt$, $b_k=\frac2T\int_0^Tf(t)\sin(k\omega t)dt$.
$\{e^{ik\omega t}\}$ orthonormal w.r.t. $\langle u,v\rangle=\frac1T\int_0^T\bar u(t)v(t)dt$.
Even $f \Rightarrow b_k=0$; odd $f\Rightarrow a_k=0$.

## Convergence theorems

- **Pointwise convergence:** $f$ piecewise $C^1$ $\Rightarrow$ Fourier series
  converges everywhere to $\frac12(f(t^+)+f(t^-))$, uniformly on compact intervals
  of continuity. Continuity of $f$ alone does **not** guarantee convergence.
- **Best approximation:** partial sum $S_n$ = orthogonal projection onto
  $T_n=\mathrm{span}\{1,\cos(k\omega t),\sin(k\omega t): k\le n\}$ — minimizes
  $\|f-\varphi\|$ over $\varphi\in T_n$.
- **Bessel's inequality:** $\|S_n\|^2\le\|f\|^2$.
- **Riemann–Lebesgue lemma:** $a_k,b_k\to0$ as $k\to\infty$.
- **Convergence speed:** $f\in C^m$ piecewise $\Rightarrow |\gamma_k|\le C/|k|^{m+1}$
  (smoother $f$ ⟹ faster-decaying coefficients).
- **Parseval's equation:** $\lim_n\|S_n\|^2=\|f\|^2$, i.e.
  $\frac{|a_0|^2}2+\sum_{k=1}^\infty(|a_k|^2+|b_k|^2)=\frac2T\int_0^T|f(t)|^2dt$.
- **Uniqueness theorem:** same Fourier coefficients $\Rightarrow$ functions agree
  wherever both continuous.

## Key worked series

- Sawtooth: $S(t)\sim\sin t+\frac{\sin2t}2+\frac{\sin3t}3+\dots$
- Square wave: $R(t)\sim\frac4\pi(\sin t+\frac{\sin3t}3+\frac{\sin5t}5+\dots)$
- $f(t)=t^2$ on $(-\pi,\pi)$: $f(t)\sim\frac{\pi^2}3-4\cos t+\cos2t-\dots$
- Parseval applied to the square wave recovers $\sum_{k=0}^\infty\frac1{(2k+1)^2}=\frac{\pi^2}8$.

## Discrete analogue

The **discrete Fourier transform (DFT)** and its efficient computation via the
**FFT** are the finite/discrete analogue of this theory — see [[fast-fourier-transform]].
