---
title: "Analysis 1 — Lecture Slides 2 (Ch. 4–6): Continuity, Differentiability, Mean Value Theorems, Taylor Series, Fixed-Point Iteration, Uniform Convergence"
module: analysis1
type: summary
sources: [raw/analysis1/analysis_1_2.pdf]
updated: 2026-10-25
---

# Overview

Source: *Analysis I*, Prof. Dr. Armin Iske, TUHH, WS 2018/2019, lecture slides
(4-up printout), 25 sheets, slide numbers 125–224. Continues directly from
[[analysis1-01-logic-sets-functions-numbers-sequences]] (Cauchy-product application
closes Ch. 3), then covers Chapter 4 (Continuity & Differentiability), Chapter 5
(Mean Value Theorems, Extrema, Taylor's Theorem), Chapter 6 start (Power Series,
Uniform Convergence).

Related pages: [[continuity]], [[compactness]], [[differentiability]],
[[mean-value-theorems-and-extrema]], [[taylor-series]], [[fixed-point-iteration]],
[[banach-fixed-point-theorem]], [[function-sequences-and-uniform-convergence]].

---

## Chapter 3 (closing) — Cauchy product application

For the exponential series $\exp(z)=\sum_{k=0}^\infty z^k/k!$ ($z\in\mathbb C$, absolutely
convergent), the Cauchy product directly proves the functional equation
$$\exp(z)\exp(w) = \sum_{n=0}^\infty\frac{1}{n!}\sum_{k=0}^n\binom nk z^k w^{n-k} = \sum_{n=0}^\infty\frac{1}{n!}(z+w)^n = \exp(z+w).$$

## Chapter 4 — Continuity and Differentiability

### 4.1 Continuity and limits of functions

For $f: D \to W$, $D\subset V$ normed, $x_0\in D$: $x_0$ is an **accumulation point**
of $D$ if $\exists (x_n)\subset D\setminus\{x_0\}$ with $x_n\to x_0$. $D'$ = set of
accumulation points; **closure** $\overline D = D\cup D'$; $D$ is **closed** if
$D'\subset D$ (i.e. $\overline D = D$). $D$ is **bounded** if contained in some ball
$K_\epsilon(x_0)$; $x_0\in D$ is an **interior point** if some $K_\epsilon(x_0)\subset D$;
$D^0$ = interior; $D$ is **open** if $D=D^0$.

Example: $D=(0,1)$ open, bounded, $\overline D=[0,1]$; $D=[0,\infty)$ closed, unbounded.

**Limit of a function (sequential definition):** $\lim_{x\to x_0}f(x)=y_0$ iff for
every sequence $(x_n)\subset D$, $x_n\ne x_0$, $x_n\to x_0$: $f(x_n)\to y_0$.
One-sided limits $\lim_{x\to x_0^-}f(x)$, $\lim_{x\to x_0^+}f(x)$ restrict to
$x_n<x_0$ / $x_n>x_0$.

Counterexamples: step function has unequal one-sided limits at $0$; $\sin(1/x)$ has
no limit as $x\to0$; $1/x$ has improper one-sided limits $\pm\infty$.

**Limit laws for functions** carry over from sequences: sum, scalar multiple,
product, and (for vector-valued $f=(f_1,\dots,f_m))$) componentwise limits.

**Continuity.** $f$ is *continuous at $x_0\in D\cap D'$* if $\lim_{x\to x_0}f(x)=f(x_0)$;
*continuous on $D$* if continuous at every $x_0\in D\cap D'$ (points of $D\setminus D'$
— isolated points — are vacuously/"extendably" continuous).

**$\epsilon$-$\delta$ characterization (equivalence theorem):** for $x_0\in D\cap D'$,
(a) $f$ continuous at $x_0$ $\iff$ (b) $\forall\epsilon>0\,\exists\delta>0\,\forall x\in D: \|x-x_0\|<\delta \Rightarrow \|f(x)-f(x_0)\|<\epsilon$.
Proof both directions by contradiction / direct $\delta=1/n$ construction.

**Closure under composition/algebra:** constants, identity, polynomials (uni- and
multivariate), power series on their domain of absolute convergence, $\sqrt[k]{x}$,
$\log,\sin,\cos$ — all continuous; sums/scalar multiples/products/quotients
(denominator $\ne0$) of continuous functions are continuous; composition of
continuous functions is continuous.

### Compactness

$D\subset\mathbb R^n$ is **compact** iff every sequence in $D$ has a subsequence
converging to a point in $D$. **Criteria for compactness (equivalence theorem):**
(a) $D$ compact $\iff$ (b) $D$ closed and bounded $\iff$ (c) Heine–Borel: every open
cover of $D$ has a finite subcover.

**Extreme value / min-max theorem:** continuous $f:[a,b]\to\mathbb R$ on a compact
interval attains both a maximum and minimum. Proof uses $\sup f$, Bolzano–Weierstraß
to extract a convergent subsequence $x_{k_j}\to x_0\in[a,b]$, and continuity of $f$.
**Important warning:** the min-max property fails without compactness — e.g.
$f(x)=1/x$ on $(0,\infty)$ is continuous but attains neither max nor min.

Generalization to $\mathbb R^n$: $D\subset\mathbb R^n$ compact, $f:D\to\mathbb R$
continuous $\Rightarrow$ $f$ attains min and max on $D$ (same B-W argument).

**Other theorems for continuous $f:[a,b]\to\mathbb R$:** existence of a zero
(if $f(a)\cdot f(b)<0$); **intermediate value theorem** (if $f(a)<c<f(b)$ then
$\exists x_0: f(x_0)=c$); continuity of the inverse function (if $f$ strictly
monotone).

**Uniform continuity:** $f:D\to\mathbb R^m$ is uniformly continuous on $D$ if
$\forall\epsilon>0\,\exists\delta>0\,\forall x,y\in D: \|x-y\|<\delta \Rightarrow \|f(x)-f(y)\|<\epsilon$
($\delta$ independent of the point, unlike ordinary continuity). **Theorem:** every
continuous function on a compact set is uniformly continuous. Converse-direction
remark: uniform continuity $\Rightarrow$ continuity (but not conversely in general —
e.g. $f(x)=1/x$, $\exp(x)$ on $\mathbb R$ are continuous but not uniformly continuous
on their full domains; $\sin(x)$ is uniformly continuous on all of $\mathbb R$).
Worked counterexample for $f(x)=1/x$ on $(0,1)$: no single $\delta$ works uniformly
near $0$ (shown via $x=1/n$, $y=1/(2n)$).

### 5.1 Differential calculus of one variable

**Difference quotient**: $\Delta f/\Delta x = \frac{f(x)-f(x_0)}{x-x_0}$ (secant slope).
$f$ is **differentiable at $x_0$** if
$f'(x_0) = \frac{df}{dx}(x_0) := \lim_{x\to x_0}\frac{f(x)-f(x_0)}{x-x_0}$ exists
(the *derivative*/*differential quotient*). One-sided derivatives
$f'(x_0^\pm)$; differentiable $\iff$ both one-sided derivatives exist and agree.

Physical interpretation: for position $c(t)$, $\dot c(t_0)=\lim_{t\to t_0}\frac{c(t)-c(t_0)}{t-t_0}$
is instantaneous velocity (mean velocity $\Delta c/\Delta t$ in the limit).

Example: monomial $f(x)=x^n \Rightarrow f'(x)=nx^{n-1}$ (via factoring
$x^n-x_0^n=(x-x_0)\sum_{j=0}^{n-1}x^{n-1-j}x_0^j$).

**Linearity, product, quotient rules:** $(f+g)'=f'+g'$, $(\lambda f)'=\lambda f'$;
**product rule** $(fg)'=f'g+fg'$; **quotient rule** $(f/g)'=\frac{f'g-fg'}{g^2}$
(for $g\ne0$). Derivative table: $x^\alpha\to\alpha x^{\alpha-1}$, $e^x\to e^x$,
$\log x\to1/x$, $\sin x\to\cos x$, $\cos x\to-\sin x$, $\tan x\to1/\cos^2x$.
Derivative of vector-valued $f=(f_1,\dots,f_m)$ is componentwise.

**Differentiability $\Rightarrow$ continuity** (not conversely — $f(x)=|x|$ is
continuous but not differentiable at $0$). Proof via
$\lim_{x\to x_0}(f(x)-f(x_0)) = \lim(x-x_0)f'(x_0) \cdot [\text{+ correction}] = 0$.

**Chain rule:** $(g\circ f)'(x_0) = g'(f(x_0))\cdot f'(x_0)$ (proved via auxiliary
functions $\eta_1,\eta_2\to0$ encoding the differentiability remainder — a Landau/
little-o style argument). **Inverse function rule:** if $f$ strictly monotone and
differentiable with $f'\ne0$, then $(f^{-1})'(y_0) = 1/f'(f^{-1}(y_0))$.
**Generalized product rule** for bilinear forms $(\cdot,\cdot):\mathbb R^n\times\mathbb R^n\to\mathbb R$
and differentiable $f,g:D\to\mathbb R^n$: $\frac{d}{dx}(f(x),g(x)) = (f'(x_0),g(x_0))+(f(x_0),g'(x_0))$.

Worked chain-rule/inverse-rule examples: $\frac{d}{dx}\cos(\exp(x))=-\sin(\exp(x))\exp(x)$;
$\frac{d}{dy}\arctan(y)=\frac{1}{1+y^2}$; $\frac{d}{dy}\log(y)=1/y$;
$\frac{d}{dx}\tan(x) = 1/\cos^2(x)$ (via quotient rule); $\frac{d}{dy}\sqrt[n]{y}=\frac1n y^{\frac1n-1}$;
$\frac{d}{dx}a^x = a^x\log a$ (for $a>0$, via $a^x=\exp(x\log a)$).

**Higher-order derivatives:** $f',f'',f''',f^{(n)}$. Smoothness classes:
$f\in C^0([a,b])$ (continuous), $C^n([a,b])$ ($n$-times continuously
differentiable), $C^\infty([a,b])$ (arbitrarily often differentiable).

## Chapter 5 — Mean Value Theorems, Extrema, Taylor's Theorem

**Motivating example (optimization):** minimize surface area $f(r,h)=2\pi r^2+2\pi r h$
of a can of fixed volume $V=\pi r^2 h$; eliminate $h=V/(\pi r^2)$, reduce to a
one-variable extremum problem $f(r)=2\pi r^2+2V/r$.

### 6.1 Extrema

**Global/local (strict) maximum/minimum** of $f:D\to\mathbb R$ at $x_0$ — standard
$\epsilon$-neighborhood definitions. "Extremum" = maximum or minimum.

**Necessary condition for local extrema:** if $f$ has a local extremum at an
interior point $x_0\in(a,b)$, then $f'(x_0)=0$ (*stationary point*). At boundary
points $x_0\in\{a,b\}$, only a one-sided sign condition on $f'$ is required.
(Converse false: $f(x)=x^3$ has $f'(0)=0$ but no extremum at $0$ — inflection point.)

Worked can-minimization example: $f'(r)=4\pi r - 2V/r^2=0 \Rightarrow r_0=\sqrt[3]{V/2\pi}$
gives the unique global minimum (using $\lim_{r\to0^+}f=\lim_{r\to\infty}f=\infty$ and
continuity on $(0,\infty)$).

**Rolle's theorem:** continuous $f:[a,b]\to\mathbb R$, differentiable on $(a,b)$,
$f(a)=f(b)$ $\Rightarrow$ $\exists x_0\in(a,b): f'(x_0)=0$. Proof via compactness
(attains max/min) — either constant (done) or an interior extremum (apply necessary
condition).

**First mean value theorem (MVT):** $f$ continuous on $[a,b]$, differentiable on
$(a,b)$ $\Rightarrow \exists x_0\in(a,b): f'(x_0) = \frac{f(b)-f(a)}{b-a}$ (proof:
apply Rolle to $h(x)=f(x)-\frac{x-a}{b-a}(f(b)-f(a))$).

**Second (Cauchy's) MVT:** $f,g$ continuous on $[a,b]$, differentiable on $(a,b)$,
$g'\ne0$ on $(a,b)$ $\Rightarrow \exists x_0: \frac{f'(x_0)}{g'(x_0)}=\frac{f(b)-f(a)}{g(b)-g(a)}$.

**Corollaries (monotonicity from the derivative's sign):** $f'\equiv0$ on $[a,b]$
$\Rightarrow f$ constant; $f'\ge0$ (resp. $>0,\le0,<0$) $\Rightarrow f$ monotone
(strictly) increasing/decreasing on $[a,b]$.

**Landau symbols:** $\varphi(h)=o(h^k) :\iff \lim_{h\to0}\varphi(h)/h^k=0$
("converges to 0 faster than $h^k$"); $\varphi(h)=\mathcal O(h^k) :\iff \exists C,\epsilon>0\,\forall|h|<\epsilon: |\varphi(h)/h^k|\le C$
("at least as fast as $h^k$"). If $f$ differentiable at $x_0$:
$f(x_0+h)-f'(x_0)h = o(x-x_0)$, i.e. the tangent-line approximation error is $o(\cdot)$.

### Taylor's theorem

Successive polynomial approximations: $f(x)\approx f(x_0)$ (degree 0);
$f(x)\approx f(x_0)+f'(x_0)(x-x_0)+o(x-x_0)$ (degree 1, if differentiable);
$f(x)\approx f(x_0)+f'(x_0)(x-x_0)+\frac{f''(x_0)}2(x-x_0)^2+o((x-x_0)^2)$
(degree 2, if twice differentiable).

**Taylor's theorem (general form):** for $f\in C^{n+1}$,
$$f(x) = T_n(x;x_0) + R_n(x;x_0), \qquad T_n(x;x_0) := \sum_{k=0}^n \frac{f^{(k)}(x_0)}{k!}(x-x_0)^k$$
(the degree-$n$ **Taylor polynomial**), with remainder forms:
- **Lagrange:** $R_n(x;x_0) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}$ for some $\xi=x_0+\theta(x-x_0)$, $\theta\in(0,1)$.
- **Integral form:** $R_n(x;x_0) = \frac{1}{n!}\int_{x_0}^x (x-t)^n f^{(n+1)}(t)\,dt$.
- **Cauchy form:** $R_n(x;x_0)=\frac{f^{(n+1)}(\xi)}{n!}(x-x_0)^{n+1}(1-\theta)^n$.
- **Schlömilch form (generalizes both):** $R_n(x;x_0)=\frac{f^{(n+1)}(\xi)}{p\cdot n!}(x-x_0)^{n+1-p}(1-\theta)^{n+1-p}$ for $p\in\{1,\dots,n+1\}$.

The Taylor polynomial $T_n$ is the unique degree-$n$ polynomial matching $f$'s
derivatives up to order $n$ at $x_0$ (uniqueness shown by matching coefficients of
$T(x)=\sum a_k(x-x_0)^k$ to $T^{(j)}(x_0)=f^{(j)}(x_0)$).

**Worked Taylor expansions (around $x_0=0$):**
$$\exp(x) = 1+x+\tfrac{x^2}{2}+\dots+\tfrac{x^n}{n!}+R_n(x;0), \quad |R_n(x;0)| \le \frac{\exp(\xi)}{(n+1)!}|x|^{n+1} \le \frac{e}{(n+1)!}.$$
$$\sin(x) = x - \tfrac{x^3}{3!}+\tfrac{x^5}{5!}-\dots+(-1)^n\tfrac{x^{2n+1}}{(2n+1)!}+R_{2n+2}(x;0).$$
(Error bound example: for $|x|\le\pi/6$, $n=3$: $|R_8(x;0)|\le8.15\times10^{-9}$.)

**Taylor series** $T_\infty(x;x_0)=\sum_{k=0}^\infty\frac{f^{(k)}(x_0)}{k!}(x-x_0)^k$ of a
$C^\infty$ function is, in general, **not convergent**, and even if convergent need
**not** converge to $f$ itself. If it does, $f$ is called **real analytic**:
$$\exp(x)=\sum\frac{x^k}{k!}, \qquad \cos(x)=\sum(-1)^k\frac{x^{2k}}{(2k)!}, \qquad \sin(x)=\sum(-1)^k\frac{x^{2k+1}}{(2k+1)!}.$$

**Corollary:** if $f\in C^{n+1}([a,b])$ has $f^{(n+1)}\equiv0$, then $f$ is a
polynomial of degree $\le n$ (follows from the Lagrange remainder vanishing).

**Taylor expansion for polynomials:** a degree-$n$ polynomial equals its own
degree-$n$ Taylor polynomial around *any* point $x_0$: $f\equiv T_n(\cdot;x_0)$.

**Horner's scheme** (efficient/stable polynomial evaluation) — nested form
$p(x)=a_0+(x-x_0)(a_1+(x-x_0)(\dots))$:
```
y := a_n
for k = n-1, n-2, ..., 0:
    y := a_k + (x - x0) * y
# result: y = p(x)
```

**Newton's method convergence (quadratic):** for $f\in C^2$ with simple root $x^*$
($f'(x^*)\ne0$), Newton iteration converges quadratically near $x^*$:
$$(x_{n+1}-x^*) = \frac{f''(\xi_n)}{2f'(x_n)}(x_n-x^*)^2.$$
(Proof via second-order Taylor expansion of $f$ around $x_n$ evaluated at $x^*$.)

**Sufficient conditions for local extrema (second-derivative test):** $f''(x_0)>0
\Rightarrow$ strict local min; $f''(x_0)<0 \Rightarrow$ strict local max (at a
stationary point $x_0$). **Generalization when $f'(x_0)=f''(x_0)=\dots=f^{(2n-1)}(x_0)=0$:**
if $f^{(2n)}(x_0)>0$ ($<0$), strict local min (max) — the first *even* nonvanishing
derivative decides; odd-order vanishing derivatives give inflection points instead.

### Convexity, concavity, inflection points

$f$ is **convex** on $[a,b]$ if secants lie above the graph:
$f(x) \le f(x_1)+\frac{x-x_1}{x_2-x_1}(f(x_2)-f(x_1))$ for $a\le x_1<x<x_2\le b$
(strict convex/concave: $<,>$ analogously). **Criterion:** $f\in C^2 \Rightarrow$
convex $\iff f''\ge0$; concave $\iff f''\le0$. For $C^1$ functions: convex
$\Rightarrow$ graph lies above every tangent line (concave: below).

**Inflection point** $x_0\in(a,b)$: $f$ changes from convex to concave (or vice
versa) across $x_0$. **Criteria:** necessary $f''(x_0)=0$; sufficient (for
$f\in C^3$): $f''(x_0)=0 \wedge f'''(x_0)\ne0$ determines left–right vs right–left
curvature change.

### 6.2 L'Hôpital's rule

For $\frac00$ or $\frac\infty\infty$ indeterminate forms, $f,g$ continuously
differentiable near $x_0$, $g(x_0)=0$ (or $\to\infty$), $g'\ne0$ near $x_0$:
$$\lim_{x\to x_0}\frac{f(x)}{g(x)} = \lim_{x\to x_0}\frac{f'(x)}{g'(x)}$$
(if the right-hand limit exists), proved via the Cauchy MVT. Variants hold for
one-sided limits and $x\to\pm\infty$ (via substitution $y=1/x$). Worked examples:
$\lim_{x\to0}\mathrm{sinc}(x)=1$; $\lim_{x\to\infty}x\log\frac{x+1}{x-1}=2$;
$\lim_{x\to0}\left(\frac1{\log(1+x)}-\frac1x\right) = \tfrac12$.

### 6.3 Curve sketching (Kurvendiskussion)

Checklist for analyzing $f$: (1) domain, range; (2) symmetry (even
$f(-x)=f(x)$ / odd $f(-x)=-f(x)$); (3) poles/singularities (order $k$: sign change
if $k$ odd, no sign change if $k$ even); (4) asymptotic behavior (asymptote
$y=\alpha x+\beta$ with $\alpha=\lim_{x\to\pm\infty}f(x)/x$, $\beta=\lim(f(x)-\alpha x)$);
(5) zeros; (6) local extrema; (7) monotonicity/sign behavior; (8) inflection
points; (9) sketch. Fully worked example: $f(x)=\frac{2x^2+3x-4}{x^2}$ (pole at
0, horizontal asymptote $y=2$, two zeros, one max, one inflection point).

### 6.4 Fixed-point iteration

**Fixed-point problem:** solve $x=\Phi(x)$ via iteration $x_{k+1}=\Phi(x_k)$, limit
$x^* = \Phi(x^*)$ (if it converges) — Newton's method is the special case
$\Phi(x)=x-f(x)/f'(x)$. Caution: $\Phi$ with a given fixed point is not unique
(e.g. $2x=\tan x$ can be rewritten as $x=\frac12\tan x$ or $x=\arctan(2x)$ — different
iterations, different convergence behavior/speed).

**Lipschitz continuity:** $\Phi:D\to V$ is Lipschitz on $D$ with constant $L$ if
$\|\Phi(x)-\Phi(y)\|\le L\|x-y\|\ \forall x,y\in D$; **contraction** if additionally
$L<1$. Lipschitz $\Rightarrow$ continuous (not conversely necessarily). Examples:
$\sin,\log|_{[1,\infty)},\exp|_{(-\infty,0]}$ are Lipschitz with $L=1$;
$\exp|_{[0,\infty)}$ is **not** Lipschitz.

**Theorem:** every $C^1$ function $\Phi:[a,b]\to[a,b]$ is Lipschitz with constant
$L=\sup_{a\le\xi\le b}|\Phi'(\xi)|$ (via MVT).

**Banach fixed-point theorem.** See [[banach-fixed-point-theorem]] for full
statement/proof: existence/uniqueness of a fixed point, global convergence of the
iteration from any starting point, and a priori/a posteriori error estimates.

Worked example: $\Phi(x)=0.1\exp(x)$ on $D=[-1,1]$: $\Phi(D)\subset D$, Lipschitz
constant $L=e/10<1$ $\Rightarrow$ Banach applies; iterate from $x_0=1$ converges to
the fixed point with $|x_n - x^*| < 10^{-6}$ by $n\ge11$ (via the a priori bound).

## Chapter 7 — Power Series and Elementary Functions (start)

### 7.1 Uniform convergence

For a sequence of functions $(f_n)_{n\in\mathbb N_0}$, $f_n:D\to\mathbb C$:
- **pointwise convergence** to $f$: $\forall z\in D: \lim_n f_n(z)=f(z)$;
- **uniform convergence** to $f$: $\lim_n \|f_n-f\|_\infty = 0$ (i.e.
  $\sup_{z\in D}|f_n(z)-f(z)|\to0$).

Uniform $\Rightarrow$ pointwise, **not conversely** — counterexample: "tent"
functions $f_n(x)=1-nx$ on $[0,1/n]$, $0$ elsewhere, converge pointwise to the
*discontinuous* step function $\mathbb 1_{\{0\}}$, but $\|f_n-f\|_\infty=1\ \forall n$
(no uniform convergence). This links to the next theorem.

**Theorem:** if $(f_n)$ are continuous on $D$ and converge uniformly to $f$, then
$f$ is continuous on $D$ (proof: standard $\epsilon/3$ argument). **Corollary:** a
uniformly (and absolutely) convergent series of continuous functions
$f(z)=\sum_{n=0}^\infty f_n(z)$ is continuous on $D$.

**Weierstraß M-test (majorant criterion):** if $|f_n(z)|\le b_n\ \forall z\in D$ and
$\sum b_n<\infty$ (convergent majorant), then $\sum f_n(z)$ converges uniformly and
absolutely on $D$ (proof: pointwise/absolute convergence from the comparison test;
uniform convergence from the tail estimate $\left|\sum_{n=m+1}^\infty f_n(z)\right| \le \sum_{n=m+1}^\infty b_n \to 0$).

**Interchanging differentiation and summation:** if $(f_n)$ are differentiable on
$(a,b)$ and both $f(x):=\sum f_n(x)$ (pointwise) and $g(x):=\sum f_n'(x)$ (uniformly)
converge on $(a,b)$, then $f$ is differentiable with $f'=g$, i.e.
$\frac{d}{dx}\sum_n f_n(x) = \sum_n \frac{d}{dx}f_n(x)$.

---

## Notes for the wiki

- Typed lecture slides (not handwritten), minor handwritten annotations by the
  user (confirmed consistent with the typed content, not transcribed separately).
- No contradictions with [[analysis1-01-logic-sets-functions-numbers-sequences]];
  this source directly continues it (same module/course, consecutive slide numbers).
