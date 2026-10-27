---
title: "Analysis 2 — Lecture Slides 2 (Ch. 10–14): Integration Techniques, Curves & Curve Integrals, Fourier Analysis, Numerical Quadrature, FFT"
module: analysis2
type: summary
sources: [raw/analysis2/analysis_2_2.pdf]
updated: 2026-10-25
---

# Overview

Source: *Analysis II*, Prof. Dr. Armin Iske, TUHH, SoSe 2019, lecture slides
(4-up), 26 sheets, slide numbers 117–220. **Gap note:** the course table of
contents (see [[analysis2-01-fixedpoint-recap-power-series]]) lists "Chapter 9:
Interpolation" between Power Series (Ch. 8, ending ~slide 28 of
`analysis_2_1.pdf`) and Integration (Ch. 10, starting at slide 117 here) — this
chapter is **missing** from the two Analysis 2 PDFs provided; flagged as a
sourcing gap (see Notes below).

Related: [[integration-techniques]], [[improper-integrals]],
[[curves-and-curve-integrals]], [[fourier-series]], [[numerical-quadrature]],
[[fast-fourier-transform]], [[taylor-series]], [[power-series]].

---

## Chapter 10 — Integration (continued)

### 10.3 (continued from gap) Taylor's theorem via repeated integration

An alternative derivation of Taylor's theorem (cf. [[taylor-series]]) via $n$-fold
partial integration of $f(x)-f(x_0)=\int_{x_0}^x f'(t)\,dt$, successively
integrating by parts to peel off each derivative order, arriving again at
$$f(x) = \sum_{k=0}^n\frac{f^{(k)}(x_0)}{k!}(x-x_0)^k + \frac{1}{n!}\int_{x_0}^x(x-t)^nf^{(n+1)}(t)\,dt,$$
and the Lagrange remainder recovered via the (integral) mean value theorem.

### 10.4 Integration of rational functions (partial fraction decomposition)

For a rational function $R(x)=p(x)/q(x)$ with $\deg p \ge \deg q$: first do
**polynomial division** $p(x) = p_1(x)q(x)+p_2(x)$ with $\deg p_2<\deg q$, so
$R(x)=p_1(x)+p_2(x)/q(x)$. Assume $q$ has real roots $x_j$ (multiplicity $k_j$)
and complex-conjugate root pairs $z_j=a_j+ib_j,\ \bar z_j=a_j-ib_j$
(multiplicity $k_j$). **Partial fraction ansatz:**
$$R(x) = p_1(x) + \sum_j\left[\frac{\alpha_{j1}}{x-x_j}+\frac{\alpha_{j2}}{(x-x_j)^2}+\dots+\frac{\alpha_{jk_j}}{(x-x_j)^{k_j}}\right] + \sum_j\left[\frac{\gamma_{j1}x+\delta_{j1}}{(x-a_j)^2+b_j^2}+\dots+\frac{\gamma_{jk_j}x+\delta_{jk_j}}{\big((x-a_j)^2+b_j^2\big)^{k_j}}\right].$$
Unknown coefficients $\alpha,\gamma,\delta$ found by **comparison of
coefficients** (Koeffizientenvergleich) after clearing denominators.

Worked example: $R(x)=\frac{1-x}{x^2(x^2+1)} = -\frac1x+\frac1{x^2}+\frac{x-1}{x^2+1}$.

**Four basic integral types for partial fractions:**
1. Polynomials: $\int\sum c_kx^k\,dx = \sum\frac{c_k}{k+1}x^{k+1}+C$.
2. Inverse powers: $\int\frac{dx}{(x-x_0)^\ell} = \log|x-x_0|+C$ ($\ell=1$), else
   $\frac{1}{1-\ell}(x-x_0)^{1-\ell}+C$.
3. $I_\ell := \int\frac{dx}{(x^2+1)^\ell}$: $I_1=\arctan(x)+C$; for $\ell>1$,
   recursion (via substitution + integration by parts):
   $$I_\ell = \frac{1}{2(1-\ell)}\left[(3-2\ell)I_{\ell-1} - \frac{x}{(x^2+1)^{\ell-1}}\right].$$
4. $\int\frac{cx+d}{((x-a)^2+b^2)^\ell}dx$: split into $\frac c2\int\frac{2(x-a)}{(\cdot)^\ell}dx$
   (substitute $u=(x-a)^2+b^2$) plus $(d+ca)\int\frac{dx}{(\cdot)^\ell}$ (substitute
   $t=(x-a)/b$, reduces to type 3).

**Substitution tricks for related integrals:** $t=e^x$ turns $\int R(e^x)dx$ into
$\int R(t)/t\,dt$; the **Weierstraß substitution** $t=\tan(x/2)$ gives
$\cos(x)=\frac{1-t^2}{1+t^2}$, $\sin(x)=\frac{2t}{1+t^2}$, turning
$\int R(\cos x,\sin x)\,dx$ into a rational-function integral in $t$.

### 10.5 Improper integrals

$$\int_a^\infty f(x)\,dx := \lim_{b\to\infty}\int_a^b f(x)\,dx, \qquad \int_{-\infty}^b f(x)\,dx := \lim_{a\to-\infty}\int_a^b f(x)\,dx, \qquad \int_{-\infty}^\infty f\,dx := \int_{-\infty}^a f\,dx+\int_a^\infty f\,dx.$$
A function is **locally integrable** on $D$ if integrable on every compact
subinterval. Example: $\int_1^\infty x^{-\alpha}dx$ converges iff $\alpha>1$.

**Convergence criterion:** $\int_a^\infty f\,dx$ exists iff
$\forall\epsilon\,\exists C\,\forall z_1,z_2>C: \left|\int_{z_1}^{z_2}f\,dx\right|<\epsilon$
(Cauchy criterion for integrals). **Absolute convergence:**
$\int|f|\,dx$ convergent $\Rightarrow \int f\,dx$ convergent.

**Majorant criterion:** $|f(x)|\le g(x)$, $\int g\,dx$ convergent $\Rightarrow \int f\,dx$
absolutely convergent (with a **minorant** converse for divergence).

Worked examples: **Dirichlet integral** $\int_0^\infty\frac{\sin x}{x}dx = \pi/2$
— convergent but **not absolutely convergent**. **Exponential integral**
$\mathrm{Ei}(x)=\int_{-\infty}^x e^t\,dt$ ($x<0$) absolutely convergent via a
majorant $|e^t|\le C/t^2$. **Gamma function**
$$\Gamma(x) := \int_0^\infty e^{-t}t^{x-1}\,dt, \qquad x>0,$$
absolutely convergent (majorant criterion at both the $t\to0^+$ singularity for
$0<x<1$ and $t\to\infty$); functional equation $\Gamma(x+1)=x\,\Gamma(x)$,
$\Gamma(1)=1 \Rightarrow \Gamma(n)=(n-1)!$ for $n\in\mathbb N$.

### 10.6 Parameter-dependent integrals

$F(x) := \int_a^b f(x,y)\,dy$. **Continuity:** if $f(x,y)$ continuous on
$I\times[a,b]$ ($I$ compact), then $F$ is continuous on $I$ (proof via uniform
continuity of $f$ on the compact product set). **Differentiability (Leibniz
rule):** if $f,\partial f/\partial x$ continuous on $I\times[a,b]$, then
$$F'(x) = \int_a^b \frac{\partial f}{\partial x}(x,y)\,dy$$
(proof via MVT + uniform continuity of $\partial f/\partial x$). Extends to
**parameter-dependent improper integrals** $F(x)=\int_a^\infty f(x,y)\,dy$,
**uniformly convergent** if $\forall\epsilon\,\exists C\,\forall x\in I, y_1,y_2>C:
|\int_{y_1}^{y_2}f(x,y)dy|<\epsilon$; majorant criterion extends (uniform
majorant $g(y)$ with $|f(x,y)|\le g(y)\ \forall x$, $\int g<\infty$); continuity
and differentiability results carry over to this case. Worked example: the Gamma
function's derivative $\Gamma'(x) = \int_0^\infty e^{-t}t^{x-1}\log(t)\,dt$.

## Chapter 11 — Applications of Integral Calculus

### 11.1 Solids of revolution (Rotationskörper)

For $f:[a,b]\to\mathbb R$, rotating the graph $y=f(x)$ about the $x$-axis gives a
cross-sectional area $Q(x)=\pi f(x)^2$, hence **volume**
$$V_{\mathrm{rot}} = \pi\int_a^b f(x)^2\,dx.$$
**Cavalieri's principle:** equal cross-sectional areas $\Rightarrow$ equal volumes.
**Surface area (Mantelfläche):** $O_{\mathrm{rot}}=2\pi\int_a^b y(t)\sqrt{1+(y'(t))^2}\,dt$.
Worked examples: ellipsoid of revolution $V=\frac43\pi a b^2$ (reduces to sphere
$V=\frac43\pi r^3$ for $a=b=r$); sphere surface $O=4\pi r^2$ (from
$y=\sqrt{r^2-x^2}$).

### 11.2 Curves and arc length

A **curve** $c=(c_1,\dots,c_n):[a,b]\to\mathbb R^n$ is continuous; $c(a)$/$c(b)$
are start/end points; $c$ is a **$C^1$-curve** if each $c_i$ is continuously
differentiable; **piecewise $C^1$** if $[a,b]$ splits into finitely many
sub-intervals on which $c$ is $C^1$; **smooth** if $\dot c(t)\ne0$ for all $t$.
Example curves: circle, cycloid ($c(t)=(r(t-\sin t), r(1-\cos t))$, not smooth at
$t=2k\pi$), helix $c(t)=(r\cos(2\pi t), r\sin(2\pi t), ht)$.

**Reparametrization:** $h:[\alpha,\beta]\to[a,b]$ continuous, bijective,
monotone increasing $\Rightarrow c\circ h$ traces "the same curve." $C^1$-curves
only reparametrized via $C^1$ maps $h$.

**Arc length.** For a partition $Z=\{a=t_0<\dots<t_m=b\}$: polygon length
$L(Z):=\sum_j\|c(t_{j+1})-c(t_j)\|$ is a lower bound on arc length; $c$ is
**rectifiable** if $\sup_Z L(Z)<\infty$, and then
$L(c):=\sup_Z L(Z) = \lim_{|Z|\to0}L(Z)$.

**Theorem (arc length formula for $C^1$-curves):** every $C^1$-curve is
rectifiable, with $L(c)=\int_a^b\|\dot c(t)\|\,dt$ (proof via MVT applied
componentwise + Riemann-sum limit). **Arc-length is reparametrization-invariant**
(substitution rule). Worked example: cycloid arc, $L=8r$ for $0\le t\le2\pi$.

**Arc-length parametrization.** $S(t):=\int_a^t\|\dot c(\tau)\|\,d\tau$ (arc-length
function); if $c$ smooth, $S:[a,b]\to[0,L(c)]$ is a $C^1$-reparametrization
(bijective). $\tilde c(s):=c(S^{-1}(s))$ is the arc-length parametrization, with
unit-speed property $\|\tilde c'(s)\|=1$ (unit tangent vector), and
$\langle\tilde c'(s),\tilde c''(s)\rangle=0$ — acceleration perpendicular to velocity.

**Curvature.** Principal normal vector $\mathbf n(s):=\tilde c''(s)/\|\tilde c''(s)\|$;
curvature $\kappa(s):=\|\tilde c''(s)\|$. For general parametrizations of function
graphs $y=y(x)$:
$$L(c) = \int_a^b\sqrt{1+y'(x)^2}\,dx, \qquad \kappa(x) = \frac{|y''(x)|}{(1+y'(x)^2)^{3/2}}.$$
Analogous 3D formula with $z(x)$ included. **Polar coordinates**
$c(t)=(r\cos\varphi,r\sin\varphi)$: $L(c)=\int_a^b\sqrt{\dot r^2+r^2\dot\varphi^2}\,dt$;
spherical coordinates analogous in 3D. Worked example: cardioid
$r=a(1+\cos\varphi)$, arc length $L=8a$.

**Enclosed area (shoelace-type formula):** for a $C^1$-curve $c=(x,y)$,
$$F(c) = \frac12\int_a^b\big(x(t)\dot y(t)-\dot x(t)y(t)\big)\,dt$$
(proof via summing signed triangle areas over a partition, limiting). Worked
example: Archimedean spiral, enclosed area of the innermost loop
$\approx1.292a^2$, arc length $\approx4.158a$.

### 11.3 Curve (line) integrals

$$\int_c f\,ds := \int_a^b f(c(t))\,\|\dot c(t)\|\,dt$$
for continuous $f:D\to\mathbb R$, $D\subset\mathbb R^n$, piecewise-$C^1$ curve $c$.
Closed-curve notation $\oint_c f\,ds$. **Parametrization invariance** (proof via the
substitution rule, mirroring the arc-length proof). Application: mass of a wire
with density $\rho(x)$: $\int_c\rho(x)\,ds$; center of mass
$x_S=\int_c\rho(x)x\,ds / \int_c\rho(x)\,ds$; moment of inertia
$\Theta=\int_c\rho(x)r(x)^2\,ds$.

## Chapter 12 — Fourier Analysis

### 12.1 Basic concepts

$f:\mathbb R\to\mathbb R$ (or $\mathbb C$) is **periodic with period $T$** if
$f(t+T)=f(t)\ \forall t$. If $T_1,T_2$ are periods, so is $k_1T_1+k_2T_2$
($k_1,k_2\in\mathbb Z$); a nonconstant continuous periodic function has a smallest
positive period. **Periodic extensions** of $g$ on $[0,T]$: direct extension
$f(t):=g(t-kT)$; **even extension** (mirror at $t=0$, i.e. $g(t):=g(-t)$ for
$-T/2\le t<0$, then periodize); **odd extension** ($g(t):=-g(-t)$).

**Fourier series / trigonometric polynomial:**
$$f(t) = \frac{a_0}2+\sum_{k=1}^\infty\big[a_k\cos(k\omega t)+b_k\sin(k\omega t)\big], \qquad \omega=\frac{2\pi}T.$$
**Complex form** (via Euler's formula $e^{ix}=\cos x+i\sin x$):
$$f(t) = \sum_{k=-\infty}^\infty \gamma_k e^{ik\omega t}, \qquad \gamma_0=\tfrac12a_0,\ \gamma_k=\tfrac12(a_k-ib_k),\ \gamma_{-k}=\tfrac12(a_k+ib_k)\ (k>0).$$

**Orthonormality:** $\{e^{ik\omega t}\}_{k\in\mathbb Z}$ is an orthonormal system
w.r.t. $\langle u,v\rangle := \frac1T\int_0^T\overline{u(t)}v(t)\,dt$ (proof via
direct integration, using $\int_0^T e^{i(\ell-k)\omega t}dt=0$ for $k\ne\ell$).

**Fourier coefficients** (piecewise continuous $f:[a,b]\to\mathbb C$):
$$\gamma_k := \frac1T\int_0^T f(t)e^{-ik\omega t}\,dt \ (k\in\mathbb Z), \qquad a_k=\frac2T\int_0^T f(t)\cos(k\omega t)\,dt,\ b_k=\frac2T\int_0^T f(t)\sin(k\omega t)\,dt\ (k>0).$$
**Theorem:** if the partial sums $f_n(t)=\sum_{k=-n}^n\gamma_ke^{ik\omega t}$
converge uniformly on $[0,T]$ to a continuous $f$, those $\gamma_k$ are exactly
$f$'s Fourier coefficients.

**Even/odd function simplification:** $f$ even $\Rightarrow b_k=0$, $a_k=\frac4T\int_0^{T/2}f(t)\cos(k\omega t)\,dt$;
$f$ odd $\Rightarrow a_k=0$, $b_k=\frac4T\int_0^{T/2}f(t)\sin(k\omega t)\,dt$.

Worked examples: **sawtooth function** $S(t)$ (odd), $b_k=1/k$, $a_k=0$:
$S(t)\sim\sin t+\frac{\sin2t}2+\frac{\sin3t}3+\dots$; **square wave** $R(t)$ (odd):
$R(t)\sim\frac4\pi\left(\sin t+\frac{\sin3t}3+\frac{\sin5t}5+\dots\right)$;
$f(t)=t^2$ on $(-\pi,\pi)$ (even, direct $2\pi$-periodic extension):
$f(t)\sim\frac{\pi^2}3-4\cos t+\cos2t-\dots$ (coefficients
$a_k=(-1)^k 4/k^2$ for $k\ge1$).

**Calculation rules for Fourier series:** linearity; conjugation
$\overline{f(t)}\sim\sum\overline{\gamma_{-k}}e^{ik\omega t}$; time-reversal
$f(-t)\sim\sum\gamma_{-k}e^{ik\omega t}$; scaling $f(ct)\sim\sum\gamma_ke^{ik(c\omega)t}$;
shift $f(t+a)\sim\sum\gamma_ke^{ik\omega a}e^{ik\omega t}$,
$e^{in\omega t}f(t)\sim\sum\gamma_{k-n}e^{ik\omega t}$; term-by-term
differentiation $f'(t)\sim\sum(ik\omega\gamma_k)e^{ik\omega t}$ (if $f$
continuous & piecewise differentiable); term-by-term integration (requires
$a_0=\gamma_0=0$, i.e. zero mean).

### Convergence theorems

**Pointwise convergence theorem:** $f$ $T$-periodic, piecewise continuously
differentiable $\Rightarrow$ its Fourier series converges **pointwise everywhere**
to $\frac12(f(t^+)+f(t^-))$ (the average of the one-sided limits — equals $f(t)$
at continuity points), and **uniformly** on compact intervals where $f$ is
continuous. **Continuity of $f$ alone does not suffice for convergence**
(important caveat).

Worked error analysis for the sawtooth function's partial sum $R_n$: derives
$|R_n(t)| \le \frac{2}{(2n+1)\sin(t/2)} \to 0$ as $n\to\infty$ (for fixed $t\in(0,2\pi)$),
via a clever telescoping/integration trick.

**Best approximation in the mean (quadratic/$L^2$) sense:** the Fourier partial
sum $S_n$ is the **orthogonal projection** of $f$ onto
$T_n:=\mathrm{span}\{1/\sqrt2,\cos(\omega t),\dots,\cos(n\omega t),\sin(\omega t),\dots,\sin(n\omega t)\}\subset C(\mathbb R)$,
and is therefore the **best approximation**: $\|f-S_n\|\le\|f-\varphi\|\ \forall\varphi\in T_n$.

**Bessel's inequality:** $\|S_n\|^2\le\|f\|^2$, i.e.
$\frac{|a_0|^2}2+\sum_{k=1}^n(|a_k|^2+|b_k|^2) \le \frac2T\int_0^T|f(t)|^2dt$.
**Riemann–Lebesgue lemma** (corollary): $\lim_{k\to\infty}a_k=\lim_{k\to\infty}b_k=0$.
**Convergence speed:** $f$ is $(m+1)$-times piecewise continuously differentiable
$\Rightarrow |\gamma_k|\le C/|k|^{m+1}$ — the smoother $f$, the faster its Fourier
coefficients decay (faster convergence).

**Parseval's equation:** $\lim_{n\to\infty}\|S_n\|^2=\|f\|^2$, i.e.
$$\frac{|a_0|^2}2+\sum_{k=1}^\infty(|a_k|^2+|b_k|^2) = \frac2T\int_0^T|f(t)|^2\,dt.$$
Worked example (square wave): recovers the classical identity
$\sum_{k=0}^\infty\frac1{(2k+1)^2}=\frac{\pi^2}8$.

**Uniqueness theorem:** two $T$-periodic piecewise-continuous functions $f,g$ with
the same Fourier coefficients satisfy $\frac12(f(t^-)+f(t^+)) = \frac12(g(t^-)+g(t^+))$
for all $t$ — in particular $f\equiv g$ wherever both are continuous.

## Chapter 13 — Numerical Quadrature

**Setup:** approximate $I=I[f]=\int_a^b f(x)\,dx$ by a quadrature formula
$I_n[f]=\sum_{i=0}^n g_i f(x_i)$ with nodes $x_i$ and weights $g_i$.

### 13.1 Newton–Cotes formulas

Construct via the interpolation polynomial $p_n$ through
$(x_i,f(x_i))_{i=0}^n$ (Lagrange form $p_n(x)=\sum_i L_i(x)f(x_i)$,
$L_i(x)=\prod_{j\ne i}\frac{x-x_j}{x_i-x_j}$), and integrate the interpolant:
$I_n[f]:=\int_a^b p_n(x)\,dx = \sum_i g_i f(x_i)$ with $g_i=\int_a^b L_i(x)\,dx$.
For **equidistant nodes** $x_i=a+ih$, $h=(b-a)/n$: weights
$\alpha_{in}=\frac1{b-a}\int_0^n\prod_{j\ne i}\frac{s-j}{i-j}\,ds$.

| $n$ | Rule | Weights $\alpha_{in}$ |
|---|---|---|
| 1 | **Trapezoidal rule** | $\tfrac12,\tfrac12$ |
| 2 | **Simpson's rule** | $\tfrac16,\tfrac46,\tfrac16$ |
| 3 | **3/8-rule** | $\tfrac38,\tfrac98,\tfrac98,\tfrac38$ |
| 4 | **Milne's rule** | $\tfrac{7}{90},\tfrac{32}{90},\tfrac{12}{90},\tfrac{32}{90},\tfrac{7}{90}$ |

Explicit forms: $I_1[f]=(b-a)\frac{f(a)+f(b)}2$ (trapezoidal);
$I_2[f]=\frac{b-a}6\big(f(a)+4f(\tfrac{a+b}2)+f(b)\big)$ (Simpson).

**Exactness:** Newton–Cotes $I_n$ integrates polynomials of degree $\le n$ exactly
(since the interpolation polynomial reconstructs $f$ exactly when $f\in\mathcal P_n$).

**Quadrature error** $R_n[f]:=I_n[f]-I[f]$, using the interpolation-error formula
$f(x)-p_n(x)=\frac{f^{(n+1)}(\xi)}{(n+1)!}\prod_i(x-x_i)$:

| $n$ | Rule | $R_n[f]$ |
|---|---|---|
| 1 | Trapezoidal | $\frac{h^3}{12}f^{(2)}(\xi)$ |
| 2 | Simpson | $\frac{h^5}{90}f^{(4)}(\xi)$ |
| 3 | 3/8 | $\frac{h^5}{80}f^{(4)}(\xi)$ |
| 4 | Milne | $\frac{h^7}{945}f^{(6)}(\xi)$ |

(with $h=(b-a)/n$). Worked error bound (trapezoidal, $n=1$):
$|R_1[f]| \le \frac1{12}\|f^{(2)}\|_\infty h^3$.

**Composite rules.** Subdivide $[a,b]$ into $N$ equal panels
$t_i=a+ih$, $h=(b-a)/N$, apply a fixed-order rule on each panel:
$$\text{Composite trapezoidal: } T(h) = h\left(\frac{f(a)}2+f(a+h)+\dots+f(b-h)+\frac{f(b)}2\right),$$
with error bound $\left|\int_a^bf\,dx-T(h)\right| \le \frac{h^2}{12}(b-a)\|f^{(2)}\|_\infty$
(derived by summing panel-wise trapezoidal errors). Analogously, **composite
Simpson's rule** (for even $N$) with error bound $\le \frac{h^4}{180}(b-a)\|f^{(4)}\|_\infty$.

### 13.2 Gauss quadrature

**Idea:** instead of fixing equidistant nodes (Newton–Cotes), **vary** the nodes
$x_0,\dots,x_n$ (and weights) to integrate polynomials of the **highest possible
degree** exactly, for integrals of the form $I[f]=\int_a^b f(x)w(x)\,dx$ with a
positive weight function $w$. **Result:** Gaussian quadrature with $n+1$ nodes
integrates polynomials up to degree $2n+1$ exactly (vs. degree $n$ for Newton–Cotes
with the same number of nodes) — a major efficiency gain.

**Construction:** nodes = zeros of the degree-$(n+1)$ orthogonal polynomial
(w.r.t. weighted inner product $(f,g)_w=\int_a^bf(x)g(x)w(x)\,dx$) for the chosen
weight $w$; weights computed to make the rule exact for $\mathcal P_n$, then
automatic exactness up to $\mathcal P_{2n+1}$ follows from the orthogonality.

**Chebyshev polynomials** ($w(x)=1/\sqrt{1-x^2}$ on $[-1,1]$):
$T_n(x)=\cos(n\arccos x)$, orthogonal with $(T_k,T_j)_w = \pi$ if $k=j=0$, $\pi/2$
if $k=j>0$, $0$ if $k\ne j$; recursion $T_{k+1}=2xT_k-T_{k-1}$, $T_0=1,T_1=x$.
**Gauss–Chebyshev quadrature:** nodes $x_i=\cos\big(\frac{(2i+1)\pi}{2n+2}\big)$,
**constant weights** $w_i\equiv\pi/(n+1)$.

**Legendre polynomials** ($w\equiv1$ on $[-1,1]$):
$L_n(x) = \frac1{2^nn!}\frac{d^n}{dx^n}(x^2-1)^n$, orthogonal
$(L_n,L_m)=\frac{2}{2n+1}\delta_{nm}$; recursion
$L_{n+1}=\frac{2n+1}{n+1}xL_n-\frac n{n+1}L_{n-1}$, $L_0=1,L_1=x$. First few:
$L_2=\tfrac12(3x^2-1)$, $L_3=\tfrac12(5x^3-3x)$, $L_4=\tfrac18(35x^4-30x^2+3)$.
**Gauss–Legendre quadrature:** nodes = zeros of $L_{n+1}$, weights
$w_i=\int_{-1}^1\prod_{j\ne i}\frac{x-x_j}{x_i-x_j}\,dx > 0$.

**General construction recipe:** build orthogonal polynomials $p_0,\dots,p_{n+1}$
for the given $(a,b,w)$; take the $n+1$ zeros of $p_{n+1}$ as nodes; compute
positive weights via $w_i=\int_a^b\prod_{j\ne i}\frac{x-x_j}{x_i-x_j}\,dx$;
resulting rule is exact for all $p\in\mathcal P_{2n+1}$.

| Name | Interval | Weight $w(x)$ |
|---|---|---|
| Gauss–Legendre | $[-1,1]$ | $1$ |
| Gauss–Chebyshev | $[-1,1]$ | $1/\sqrt{1-x^2}$ |
| Gauss–Jacobi | $[-1,1]$ | $(1-x)(1+x)$ |
| Gauss–Laguerre | $[0,\infty)$ | $e^{-x}$ |
| Gauss–Hermite | $(-\infty,\infty)$ | $e^{-x^2}$ |

## Chapter 14 — The Fast Fourier Transform (FFT)

**Goal:** efficient computation of the **Discrete Fourier Transform (DFT)**:
$$\hat z(m) = \sum_{n=0}^{N-1} z(n)\,\omega_N^{nm}, \quad 0\le m\le N-1, \qquad \omega_N := e^{-2\pi i/N}.$$
Direct evaluation costs $\mathcal O(N^2)$. **Method (Cooley & Tukey, 1965):**
divide-and-conquer, assuming $N=2^k$.

**Key observation:** $\omega_{2N}^2=\omega_N$. For $N=2^k$, split the DFT sum into
even/odd indices:
$$\hat z(m) = \sum_{n=0}^{N/2-1} z(2n)\,\omega_N^{2nm} + \omega_N^m\sum_{n=0}^{N/2-1} z(2n+1)\,\omega_N^{2nm} = \hat u(m) + \omega_N^m\,\hat v(m)$$
where $u(n):=z(2n)$, $v(n):=z(2n+1)$ are the even/odd-indexed subsequences of
length $N/2$, and $\hat u,\hat v$ are their ($N/2$-point) DFTs. Using periodicity
$\hat u(m+N/2)=\hat u(m)$:
$$\hat z(m)=\hat u(m)+\omega_N^m\hat v(m) \ (m=0,\dots,M-1), \qquad \hat z(M+\ell)=\hat u(\ell)-\omega_N^\ell\hat v(\ell) \ (\ell=0,\dots,M-1), \quad M=N/2.$$

**Pseudocode (recursive, radix-2 Cooley–Tukey FFT):**
```
FUNCTION FFT(z[0..N-1]):           # N = 2^k
    IF N == 1: RETURN z            # base case: DFT of length 1 is identity
    u := FFT( z[0], z[2], z[4], ..., z[N-2] )   # even-indexed, length N/2
    v := FFT( z[1], z[3], z[5], ..., z[N-1] )   # odd-indexed,  length N/2
    FOR m = 0, 1, ..., N/2 - 1:
        twiddle := exp(-2*pi*i*m/N)
        z_hat[m]         := u[m] + twiddle * v[m]
        z_hat[m + N/2]    := u[m] - twiddle * v[m]
    RETURN z_hat
```

**Complexity theorem:** the FFT computes the DFT of $z\in\mathbb C^N$ ($N=2^k$) in
$\mathcal O(N\log N)$ steps (vs. $\mathcal O(N^2)$ direct). Proof: recursive
halving gives $k=\log_2N$ levels, each doing $\mathcal O(N)$ work, total
$\mathcal O(N\log N)$; base case $N=1$ costs $\mathcal O(1)$.

**Inverse DFT (IFFT):**
$$z(n) = \frac1N\sum_{m=0}^{N-1}\hat z(m)\,e^{2\pi imn/N}, \qquad 0\le n\le N-1$$
(computable with the same FFT algorithm, up to conjugation/scaling — e.g. MATLAB
`w = fft(z)`, `z = ifft(w)`).

---

## Notes for the wiki

- **Sourcing gap:** "Chapter 9: Interpolation" (per the Analysis 2 table of
  contents) is absent from both `analysis_2_1.pdf` and `analysis_2_2.pdf` — there
  is a slide-number jump from the high-20s to slide 117. If a source for this
  chapter exists, it should be added to `raw/analysis2/` and ingested; otherwise
  this is a known gap in the wiki's Analysis 2 coverage.
- No contradictions found between this source and prior material; new concept
  pages created: [[integration-techniques]], [[improper-integrals]],
  [[curves-and-curve-integrals]], [[fourier-series]], [[numerical-quadrature]],
  [[fast-fourier-transform]].
