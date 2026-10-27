---
title: "Function Sequences and Uniform Convergence"
module: general
type: concept
sources: [raw/analysis1/analysis_1_2.pdf]
updated: 2026-10-25
---

# Function Sequences and Uniform Convergence

Related: [[continuity]], [[series-and-convergence-tests]],
[[analysis1-02-continuity-differentiability-taylor-fixedpoint]].

## Definitions

For $(f_n)_{n\ge0}$, $f_n:D\to\mathbb C$: **pointwise convergence** to $f$ means
$\forall z\in D: f_n(z)\to f(z)$; **uniform convergence** means
$\|f_n-f\|_\infty=\sup_{z\in D}|f_n(z)-f(z)| \to 0$. Uniform $\Rightarrow$ pointwise,
not conversely (tent-function counterexample converging pointwise to a
discontinuous step function).

## Key theorems

- **Uniform limit of continuous functions is continuous** (uniform convergence
  "transfers" continuity; pointwise convergence does not, as the counterexample shows).
- **Weierstraß M-test:** $|f_n(z)|\le b_n\ \forall z\in D$, $\sum b_n<\infty$
  $\Rightarrow \sum f_n$ converges absolutely and uniformly on $D$.
- **Term-by-term differentiation:** if $\sum f_n(x)$ converges pointwise and
  $\sum f_n'(x)$ converges uniformly on $(a,b)$, then
  $\frac{d}{dx}\sum f_n(x) = \sum f_n'(x)$.

## Why this matters

This is the rigorous foundation for treating power series (exponential, sine,
cosine, and later series expansions in Analysis 2/3) as continuous,
term-by-term-differentiable functions on their domain of convergence. Formalized
further in [[power-series]] (radius of convergence, Cauchy–Hadamard formula).

Cross-checked against Analysis 2 Ch. 8.1, which repeats this material verbatim —
see [[analysis2-01-fixedpoint-recap-power-series]].
