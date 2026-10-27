---
title: "Analysis 2 — Lecture Slides 1 (Ch. 7–8): Fixed-Point Iteration (recap), Power Series & Elementary Functions"
module: analysis2
type: summary
sources: [raw/analysis2/analysis_2_1.pdf]
updated: 2026-10-25
---

# Overview

Source: *Analysis II für Studierende der Ingenieurwissenschaften*, Prof. Dr. Armin
Iske, TUHH, Sommersemester 2019. Lecture slides (4-up), 28 sheets. Course table of
contents (full module): Fixed-point iteration, Uniform convergence, Power series,
Elementary functions, Interpolation, Integration, Curves & curve integrals,
Numerical quadrature, Extrapolation, Periodic functions/Fourier series, FFT.

This source covers **Chapter 7 (Fixed-Point Iteration)** — a direct recap of
material already in the wiki from Analysis 1 — and **Chapter 8 (Power Series and
Elementary Functions)**, which is new.

Related: [[fixed-point-iteration]], [[banach-fixed-point-theorem]],
[[function-sequences-and-uniform-convergence]], [[power-series]], [[taylor-series]].

---

## Chapter 7 — Fixed-Point Iteration (recap, no new content)

This chapter is **identical in substance** to the fixed-point-iteration material
already ingested from `analysis_1_2.pdf`: the fixed-point problem $x=\Phi(x)$,
Newton's method as a special case, Lipschitz continuity / contractions, the
$C^1\Rightarrow$ Lipschitz theorem, and the full **Banach fixed-point theorem**
(existence/uniqueness, convergence, a priori/a posteriori error bounds), including
the same worked example $\Phi(x)=0.1\exp(x)$ on $[-1,1]$. No contradictions, no new
claims — see [[fixed-point-iteration]] and [[banach-fixed-point-theorem]] for the
full statements (already documented).

## Chapter 8 — Power Series and Elementary Functions

### 8.1 Uniform convergence (recap, no new content)

Pointwise vs. uniform convergence of function sequences, the theorem that a
uniform limit of continuous functions is continuous, the Weierstraß majorant
(M-test) criterion, and interchangeability of differentiation and summation for
uniformly convergent series of derivatives — all identical to the material at the
end of `analysis_1_2.pdf`. See [[function-sequences-and-uniform-convergence]].

### 8.2 Power series (new)

**Definition.** A series of the form
$$f(z) = \sum_{k=0}^\infty a_k(z-z_0)^k, \qquad a_k, z_0, z\in\mathbb C$$
is a **(complex) power series** around the **expansion point** $z_0$. Example: the
complex exponential series $\exp(z)=\sum_{k=0}^\infty z^k/k!$. The elementary
functions $\log(z), \cos(z), \sin(z), \dots$ are all *defined* via power series.

**Radius of convergence.** For every power series $\sum a_k(z-z_0)^k$ there exists
$r\ge0$ (possibly $r=\infty$) — the **radius of convergence** — such that:
$$|z-z_0|<r \implies \sum a_k(z-z_0)^k \text{ absolutely convergent}, \qquad |z-z_0|>r \implies \text{divergent}.$$
The series converges **uniformly** on every closed sub-disc
$\overline{K_\rho(z_0)}=\{z\in\mathbb C: |z-z_0|\le\rho\}$ for $0\le\rho<r$ (not
necessarily on the open disc $K_r(z_0)$ itself, nor at $|z-z_0|=r$).

*Proof idea:* define $r := \sup\{|w| : \sum a_k w^k \text{ convergent}\}$. For
$\rho<r$, pick $w$ with $\rho<|w|<r$ where $\sum a_kw^k$ converges, so
$(a_kw^k)$ is bounded by some $M$; then for $|z-z_0|\le\rho$,
$|a_k(z-z_0)^k| \le M\left(\frac{\rho}{|w|}\right)^k$, a convergent geometric
majorant (ratio $\rho/|w|<1$) — giving absolute and uniform convergence via the
Weierstraß M-test.

**Cauchy–Hadamard formula.** The radius of convergence can be computed by
$$r = \frac{1}{\limsup_{k\to\infty}\sqrt[k]{|a_k|}}$$
(with the convention $r=\infty$ if the $\limsup$ is 0, and $r=0$ if it is $\infty$).
*Proof:* apply the root test to $\sum a_k(z-z_0)^k$: convergent if
$\limsup\sqrt[k]{|a_k(z-z_0)^k|} = |z-z_0|\limsup\sqrt[k]{|a_k|} < 1 \iff |z-z_0|<r$.
Alternative (when the limit exists): $r = \lim_{k\to\infty}|a_k/a_{k+1}|$ (via the
ratio test instead — gives the same radius since $\sqrt[k]{k}\to1$).

**Term-by-term differentiation.** If $f(z)=\sum_{k=0}^\infty a_k(z-z_0)^k$ has
radius of convergence $r$, then $f$ is differentiable on $K_r(z_0)$ and
$$f'(z) = \sum_{k=1}^\infty k a_k (z-z_0)^{k-1},$$
and this differentiated series has the **same radius of convergence** $r$ (even in
the edge cases $r=0$ or $r=\infty$) — since $\lim_{k\to\infty}\sqrt[k]{k}=1$ leaves
the Cauchy–Hadamard value unchanged.

### Worked examples

| Series | Radius $r$ |
|---|---|
| $\sum k! \, z^k$ | $0$ (only converges at $z=0$, since $(k!)^{1/k}\to\infty$) |
| $\sum z^k$ (geometric) | $1$ |
| $\sum z^k/k!$ (exponential) | $\infty$ |

From differentiating the geometric series $\frac1{1-z}=\sum_{k=0}^\infty z^k$
($|z|<1$) termwise:
$$\frac{1}{(1-z)^2} = \sum_{k=1}^\infty kz^{k-1} = 1+2z+3z^2+4z^3+\dots, \qquad \frac{1}{(1-z)^3} = \tfrac12\sum_{k=2}^\infty k(k-1)z^{k-2} = \tfrac12(2+6z+12z^2+\dots).$$

**Power series expansion of the logarithm** (via integrating the geometric series
in $-x$): since $\frac1{1+z}=\sum_{k=0}^\infty(-1)^kz^k$ for $|z|<1$, integrating
term-by-term (same radius of convergence is preserved under integration, by the
same argument as differentiation) gives
$$\log(1+x) = \sum_{k=0}^\infty \frac{(-1)^k}{k+1}x^{k+1}, \qquad -1<x<1.$$

---

## Notes for the wiki

- Chapter 7 and §8.1 are a verbatim continuation/recap of
  [[analysis1-02-continuity-differentiability-taylor-fixedpoint]] — confirmed
  consistent, no wiki updates needed for those sections beyond this note.
- New concept page created: [[power-series]].
