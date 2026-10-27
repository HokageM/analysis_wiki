---
title: "Banach Fixed-Point Theorem"
module: general
type: theorem
sources: [raw/analysis1/analysis_1_2.pdf]
updated: 2026-10-25
---

# Banach Fixed-Point Theorem

Used in: [[fixed-point-iteration]],
[[analysis1-02-continuity-differentiability-taylor-fixedpoint]].

## Statement

Let $(V,\|\cdot\|)$ be a complete normed space (Banach space). Let
$D\subset V$ be nonempty and closed, and $\Phi: D\to D$ a contraction with
Lipschitz constant $L<1$. Then:

(a) **Existence & uniqueness:** $\Phi$ has exactly one fixed point $x^*\in D$,
i.e. $\Phi(x^*)=x^*$.

(b) **Global convergence:** for every starting point $x_0\in D$, the iteration
$x_{k+1}=\Phi(x_k)$ converges to $x^*$.

(c) **Error estimates:**
$$\|x_n-x^*\| \le \frac{L^n}{1-L}\|x_1-x_0\| \quad \text{(a priori)}, \qquad \|x_n-x^*\| \le \frac{L}{1-L}\|x_n-x_{n-1}\| \quad \text{(a posteriori)}.$$

## Proof sketch

1. $(x_k)\subset D$ (since $\Phi:D\to D$); $\|x_{k+1}-x_k\| = \|\Phi(x_k)-\Phi(x_{k-1})\| \le L\|x_k-x_{k-1}\| \le L^k\|x_1-x_0\|$.
2. For $m>n$: $\|x_m-x_n\| \le \sum_{k=n}^{m-1}\|x_{k+1}-x_k\| \le \sum_{k=n}^{m-1}L^k\|x_1-x_0\| \le \frac{L^n}{1-L}\|x_1-x_0\| \to 0$,
   so $(x_k)$ is Cauchy; by completeness of $V$ and closedness of $D$, $x_k\to x^*\in D$.
3. Continuity of $\Phi$ (Lipschitz $\Rightarrow$ continuous) and $x_{k+1}=\Phi(x_k)$ give $x^*=\Phi(x^*)$.
4. **Uniqueness:** if $x^{**}$ is another fixed point, $\|x^*-x^{**}\| = \|\Phi(x^*)-\Phi(x^{**})\|\le L\|x^*-x^{**}\|$ with $L<1$ forces $\|x^*-x^{**}\|=0$.
5. Error estimates follow by letting $m\to\infty$ in the Cauchy estimate (a priori)
   and a short triangle-inequality argument (a posteriori). $\blacksquare$

## Worked example

$\Phi(x)=0.1\exp(x)$ on $D=[-1,1]$: $\Phi(D)\subset[0.1e^{-1},0.1e]\subset D$;
$|\Phi'(x)|=0.1e^x \le 0.1e<1$ on $D$, so $L=e/10$. Banach applies; from
$x_0=1$, $x_1=0.1e\approx0.2718$, and the a priori bound guarantees
$|x_n-x^*|<10^{-6}$ once $n\ge11$.
