---
title: "Series and Convergence Tests"
module: general
type: concept
sources: [raw/analysis1/analysis_1_1.pdf]
updated: 2026-10-25
---

# Series and Convergence Tests

Related: [[sequences-and-convergence]], [[cauchy-convergence-criterion]],
[[analysis1-01-logic-sets-functions-numbers-sequences]].

## Definitions

A series $\sum a_k$ is the sequence of partial sums $s_n=\sum_{k=0}^n a_k$; it
converges with sum $s$ iff $(s_n)\to s$. It is **absolutely convergent** iff
$\sum|a_k|$ converges (absolute convergence $\Rightarrow$ convergence, not
conversely — see the alternating harmonic series below).

## Necessary condition & Cauchy criterion

$\sum a_k$ convergent $\Rightarrow a_k\to0$ (not sufficient — harmonic series).
Cauchy criterion for series (from [[cauchy-convergence-criterion]]):
$\sum a_k$ convergent $\iff \forall\epsilon\,\exists N\,\forall m,n\ge N: |\sum_{k=n}^m a_k|<\epsilon$.

## Convergence tests (for absolute convergence)

| Test | Condition | Conclusion |
|---|---|---|
| Boundedness | $(\sum_{k=0}^n\|a_k\|)_{n\ge0}$ bounded | $\sum a_k$ abs. convergent |
| Comparison / majorant | $\|a_k\|\le b_k$, $\sum b_k$ convergent | $\sum a_k$ abs. convergent |
| Ratio (quotient) | $\|a_{k+1}/a_k\|\le q<1$ for $k\ge k_0$ | abs. convergent (divergent if limit $>1$) |
| Root | $\sqrt[k]{\|a_k\|}\le q<1$ for $k\ge k_0$ | abs. convergent (divergent if limit $>1$) |

**Leibniz criterion** (alternating series): $\sum(-1)^k a_k$ with $a_k\ge0$
monotonically decreasing to $0$ converges (not necessarily absolutely).

## Key examples

- **Geometric series** $\sum q^k = \frac1{1-q}$ for $|q|<1$; diverges for $|q|\ge1$.
- **Harmonic series** $\sum 1/k$ diverges.
- **Alternating harmonic series** $\sum(-1)^k/(k+1) = \ln2$: convergent, but **not**
  absolutely convergent — the canonical example that convergence $\ne$ absolute convergence.
- **Exponential series** $\exp(z) := \sum z^k/k!$ absolutely convergent for all $z\in\mathbb C$ (ratio test).
- $\sum 1/k^2=\pi^2/6$, $\sum1/k^4=\pi^4/90$, $\sum1/k^6=\pi^6/945$ (stated without proof).

## Rearrangement and products

- **Rearrangement theorem**: an absolutely convergent series may be reordered
  (via any bijection $\sigma$ on the index set) without changing its sum. This
  fails for conditionally convergent series (e.g. the alternating harmonic series
  can be rearranged to sum to any value — a fact to flag if a later source states
  this explicitly).
- **Cauchy product**: for absolutely convergent $\sum a_\ell,\sum b_m$,
  $$\Big(\sum a_\ell\Big)\Big(\sum b_m\Big) = \sum_{n=0}^\infty\Big(\sum_{k=0}^n a_kb_{n-k}\Big).$$
