---
title: "Analysis 1 — Handwritten Formula Sheet"
module: analysis1
type: summary
sources: [raw/analysis1/Analysis_1_formulas.pdf]
updated: 2026-10-25
---

# Overview

Two-page handwritten (by the user) condensed formula/cheat sheet for Analysis 1,
covering derivative rules, Taylor's theorem, sequences, series, and continuity
criteria. This content is **consistent with** and does not contradict
[[analysis1-01-logic-sets-functions-numbers-sequences]] and
[[analysis1-02-continuity-differentiability-taylor-fixedpoint]] — it is a compressed
personal reference rather than a new source of material. Transcribed faithfully
below; a few entries are condensed shorthand and are expanded/clarified using the
matching lecture material where the handwriting was ambiguous.

Related: [[differentiability]], [[taylor-series]],
[[mean-value-theorems-and-extrema]], [[sequences-and-convergence]],
[[series-and-convergence-tests]], [[continuity]], [[real-numbers-and-axioms]],
[[fixed-point-iteration]].

---

## Page 1

### Difference quotient and derivative at a point

$$\lim_{x\to x_0} \frac{f(x)-f(x_0)}{x-x_0} = f'(x_0), \qquad T(x) = f'(x_0)(x-x_0)+f(x_0)$$

(tangent-line linearization at $x_0$.)

### Differentiation rules

- (I) Linearity: $(af+bg)'(x_0) = af'(x_0)+bf'(x_0)$ *[as written; per the lecture
  this should read $a f'(x_0) + b\, g'(x_0)$ — flagging as a likely shorthand slip
  in the handwritten note, not a contradiction of the source material]*.
- (II) Product rule: $(fg)'(x_0) = f'(x_0)g(x_0)+f(x_0)g'(x_0)$.
- (III) Quotient rule: $\left(\frac fg\right)'(x_0) = \frac{f'(x_0)g(x_0)-g'(x_0)f(x_0)}{g(x_0)^2}$.
- (IV) Reciprocal rule: $\left(\frac1g\right)'(x_0) = -\frac{g'(x_0)}{g(x_0)^2}$.
- (V) Chain rule: $\big(g(f(x))\big)'(x_0) = g'(f(x_0))\cdot f'(x_0)$.
- (VI) Inverse function rule: $g'(y_0) = \dfrac{1}{f'(g(y_0))}$ where $g=f^{-1}$.

### Monotonicity from the derivative

$f'(x)>0 \Rightarrow$ strictly monotone increasing; $f'(x)<0 \Rightarrow$ strictly
monotone decreasing (falling); $f'(x)\ge0 \Rightarrow$ monotone increasing;
$f'(x)\le0 \Rightarrow$ monotone decreasing (falling).

### Convexity / concavity

$f''(x)>0 \Rightarrow$ strictly convex (left curve); $f''(x)<0 \Rightarrow$
strictly concave (right curve); $f''(x)\ge0 \Rightarrow$ convex; $f''(x)\le0
\Rightarrow$ concave.

### Poles and asymptotes

Poles: points where $f$ is undefined; a pole of odd order ("Grad 1") causes a
sign change in $f$ across the pole. Asymptote $y=ax+b$:
$$a = \lim_{x\to\pm\infty}\frac{f(x)}{x}, \qquad b = \lim_{x\to\pm\infty}\big(f(x)-ax\big).$$

### Sequence examples (convergence to 0 and comparisons)

$$\frac1n \to 0 \ (n\to\infty), \qquad \frac{1}{\sqrt n}\to 0, \qquad \sqrt[n]{\tfrac1n}\to1.$$
Comparisons noted: $\frac1{n+1}<\frac1n$; $\sqrt{n+1}>\sqrt n$; and for
$q = \sqrt[n]{a_n}$ type sequences, convergence to a limit $L$: if $L<1$ the
sequence (or associated series, by the root test) converges, if $L>1$ it diverges.

### Majorant criterion (3rd item)

$$\sum_{k} |a_k| \le \sum_k b_k, \qquad \sum b_k \text{ convergent} \Rightarrow \sum a_k \text{ absolutely convergent}$$
(comparison/majorant test — see [[series-and-convergence-tests]]).

### Taylor polynomial and remainder

$$T_n(x;x_0) = f(x_0)+f'(x_0)(x-x_0)+\tfrac{1}{2!}f''(x_0)(x-x_0)^2+\dots+\tfrac1{n!}f^{(n)}(x_0)(x-x_0)^n$$
$$R_n(x;x_0) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}, \qquad \xi \text{ between } x_0 \text{ and } x$$
Note (handwritten remark): "choose $x<\xi<x_0$ so that max is taken" — i.e. when
bounding the remainder, $\xi$ should be chosen to maximize $|f^{(n+1)}(\xi)|$ on the
relevant interval to get a valid upper bound.

### Derivative / inverse-function quick table

$$(e^x)' = e^x, \quad (\ln x)^{-1}\text{-type relation: } e^{\ln x}=x$$
$$\sin(x);\ \cos(x);\ \sin(\arcsin(x))=x;\ \cos(\arccos(x))=x;\ \tan(\arctan(x))=x$$
*(This block records the derivative pairs of trig functions and their inverses —
confirming $\sin,\cos,\tan$ and $\arcsin,\arccos,\arctan$ are mutual inverses on
their respective restricted domains, matching [[differentiability]].)*

### L'Hôpital's rule

$$\frac00: \quad \lim_{x\to x_0}\frac{f(x)}{g(x)} = \lim_{x\to x_0}\frac{f'(x)}{g'(x)}, \qquad \frac\infty\infty: \quad \lim_{x\to x_0}\frac{f(x)}{g(x)} = \lim_{x\to x_0}\frac{f'(x)}{g'(x)}.$$

### Unit circle / trig value table

| Angle (°) | 0 | 30 | 45 | 60 | 90 | 120 | 135 | 150 | 180 |
|---|---|---|---|---|---|---|---|---|---|
| Radians | $0$ | $\pi/6$ | $\pi/4$ | $\pi/3$ | $\pi/2$ | $2\pi/3$ | $3\pi/4$ | $5\pi/6$ | $\pi$ |
| $\sin$ | $0$ | $1/2$ | $\sqrt2/2$ | $\sqrt3/2$ | $1$ | $\sqrt3/2$ | $\sqrt2/2$ | $1/2$ | $0$ |
| $\cos$ | $1$ | $\sqrt3/2$ | $\sqrt2/2$ | $1/2$ | $0$ | $-1/2$ | $-\sqrt2/2$ | $-\sqrt3/2$ | $-1$ |

Also recorded: $\sin^2\varphi+\cos^2\varphi=1$.

---

## Page 2

### Boundedness, monotonicity, supremum/infimum

- Bounded sequence: $f(x)=f(x) \ldots$ *[handwriting unclear at top-left, appears to
  restate boundedness]*; monotone increasing/decreasing definitions as in
  [[sequences-and-convergence]].
- **Supremum** = smallest upper bound; **infimum** = greatest lower bound (matches
  [[real-numbers-and-axioms]]).
- Number-set diagram: $\mathbb N \subset \mathbb Z \subset \mathbb Q \subset \mathbb R$ (sketch of nested number systems).

### Convergence ($\epsilon$–$N$ definition) and bounded sequences

$$\lim_{n\to\infty} a_n = a \iff \forall\epsilon>0\,\exists N\in\mathbb N\,\forall n\ge N: |a_n-a|<\epsilon.$$
Bounded sequence: $\exists K>0: |a_n|\le K\ \forall n$.

### Monotone convergence criterion

A monotone increasing sequence bounded above, or monotone decreasing sequence
bounded below, converges (matches the theorem in [[sequences-and-convergence]]).

### Geometric sequence cases

$$q^n \to \begin{cases} +\infty, & q>1\\ 1, & q=1\\ 0, & 0\le|q|<1\\ \text{bounded, divergent}, & q=-1\\ \text{divergent}, & q<-1\end{cases}$$

### Newton's method

$$T(x) = f(x_n)+f'(x_n)(x-x_n) = 0 \ \Rightarrow\ x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}.$$

### Convergence speed

Linear convergence ($2.$ "Pseudoordnung" / order-2, i.e. quadratic, for Newton's
method) — matches [[sequences-and-convergence]]/[[taylor-series]] (Newton
converges quadratically near a simple root).

### Sequences in vector spaces / norms

$$\|x\|_1 = |x_1|+|x_2|+\dots+|x_n|, \qquad \|x\|_2=\sqrt{x_1^2+x_2^2+\dots+x_n^2}, \qquad \|x\|_\infty = \max\{|x_1|,\dots,|x_n|\}.$$
A sequence in $\mathbb R^n$ converges iff it converges componentwise (matches
norm-equivalence discussion in [[sequences-and-convergence]]).

### Continuity at a point — three equivalent characterizations

(a) **Sequential:** $f$ continuous at $x_0$ iff for all sequences $x_n\to x_0$: $f(x_n)\to f(x_0)$.
(b) **Limit form:** $f$ continuous in $x_0$ iff $\lim_{x\to x_0}f(x)=f(x_0)$.
(c) **Continuous extension form:** $\lim_{x\to x_0}g(x) = g(x_0)$ — i.e. $g$ agrees
with its limit, so it can be continuously extended/is already continuous there.

### $\epsilon$-$\delta$ criterion worked micro-example

$$|x-x_0|<\delta \Rightarrow |f(x)-f(x_0)| < \epsilon, \qquad g(x)=x^2 : \quad |g(x)-g(x_0)| = |x-x_0|\cdot|x+x_0| \le \delta(2|x_0|+\delta)=:\epsilon.$$
(Standard $\epsilon$-$\delta$ proof sketch that $f(x)=x^2$ is continuous, by
bounding $|x+x_0|$ near $x_0$ and solving for a suitable $\delta$ — matches the
general $\epsilon$-$\delta$ equivalence theorem in [[continuity]].)

### Series: necessary condition and basic examples

- Necessary condition: $\sum a_n$ convergent $\Rightarrow a_n\to0$.
- **Leibniz criterion** for alternating series $\sum(-1)^n a_n$, $a_n\searrow0$.
- **Geometric series** $\sum q^n$; **harmonic series** $\sum 1/n$ (divergent).
- Convergence tests: majorant/minorant (comparison), ratio (quotient), root — with
  limit $<1$ convergent, $>1$ divergent, matching [[series-and-convergence-tests]].
- Absolute convergence: $\sum|a_n|<\infty \Rightarrow \sum a_n$ convergent.
- Known convergent series: $\sum 1/n^2 = \pi^2/6$; alternating harmonic series
  $\sum(-1)^n/n = -\ln2$ *(sign convention depends on starting index — matches
  $\sum_{k\ge0}(-1)^k/(k+1)=\ln2$ from the lecture, just shifted indexing)*.

### Accumulation points and closure

$M'$ = set of accumulation points of $M$; $M$ is **closed** iff $M'\subset M$ (i.e.
$M\cup M' = M$); $M^0$ = set of interior points of $M$; $M$ is **open** iff
$M=M^0$. Matches definitions in [[continuity]].

---

## Notes for the wiki

- This source is the user's own handwritten condensation of the lecture material
  already in [[analysis1-01-logic-sets-functions-numbers-sequences]] and
  [[analysis1-02-continuity-differentiability-taylor-fixedpoint]]; no new or
  contradictory claims were found. One likely shorthand slip was flagged inline
  (linearity-of-derivative rule) but does not indicate an actual error in the
  underlying lecture content.
- A few handwriting fragments were too compressed/ambiguous to transcribe with full
  confidence (flagged inline with "*[...]*" notes above) — worth double-checking
  against the original scan if precision matters for exam prep.
