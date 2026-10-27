---
title: "Analysis 2 — Handwritten Formula Sheet"
module: analysis2
type: summary
sources: [raw/analysis2/analysis_2_formulas.pdf]
updated: 2026-10-25
---

# Overview

Two-page handwritten (by the user) condensed formula sheet for Analysis 2:
antiderivative table, substitution rules, partial fractions, improper integrals,
parameter-dependent integrals, Lipschitz/Banach fixed-point recap, uniform
convergence of function series, power series integration, and — notably —
**interpolation formulas (Lagrange, Newton divided differences, cubic splines)**
that are **not present** in either `analysis_2_1.pdf` or `analysis_2_2.pdf`. This
partially fills the "Chapter 9: Interpolation" content gap noted in
[[analysis2-02-integration-curves-fourier-quadrature-fft]] and `wiki/index.md`.

Related: [[integration-techniques]], [[improper-integrals]],
[[fixed-point-iteration]], [[banach-fixed-point-theorem]],
[[function-sequences-and-uniform-convergence]], [[power-series]], [[interpolation]].

---

## Page 1

### Antiderivative table

$$\int 1\,dx=x+C,\quad \int x\,dx=\tfrac{x^2}2+C,\quad \int x^\alpha\,dx=\tfrac{x^{\alpha+1}}{\alpha+1}+C\ (\alpha\ne-1),\quad \int\tfrac1x\,dx=\ln|x|+C$$
$$\int\sin x\,dx=-\cos x+C,\quad \int\cos x\,dx=\sin x+C,\quad \int\tan x\,dx=-\ln|\cos x|+C,\quad \int\tfrac1{\cos^2x}\,dx=\tan x+C$$
$$\int\tfrac1{\sqrt{1-x^2}}\,dx=\arcsin x+C,\quad \int\tfrac1{1+x^2}\,dx=\arctan x+C,\quad \int e^x\,dx=e^x+C$$
$$\int\sinh x\,dx=\cosh x+C,\quad \int\cosh x\,dx=\sinh x+C,\quad \int\tanh x\,dx=\ln(\cosh x)+C$$

### Substitution rules

(a) $\int f(g(t))g'(t)\,dt = F(g(t))+C = \int f(x)\,dx$ (with $x=g(t)$).
(b) $\int_a^b f(g(t))g'(t)\,dt = F(g(b))-F(g(a)) = \int_{g(a)}^{g(b)} f(x)\,dx$.
(c)/(d) The inverse direction: given $\int_a^b f(x)\,dx$ and $c,d$ with
$g(c)=a, g(d)=b$: $\int_a^b f(x)\,dx = \int_c^d f(g(t))g'(t)\,dt$.

### Polynomials and partial fractions

$$P(x)=\sum_{k=0}^n c_kx^k \ \Rightarrow\ \int P(x)\,dx = \sum_{k=0}^n\frac{c_k}{k+1}x^{k+1}+C.$$

Partial fraction building blocks (matches [[integration-techniques]]):
$$\int\frac{dx}{(x-x_j)^k} = \ln|x-x_j|+C\ (k=1)\ \text{ or }\ \frac{(x-x_j)^{1-k}}{1-k}+C\ (k\ge2),$$
$$\frac{\gamma x+\delta}{((x-a)^2+b^2)^\ell} = \frac\gamma2\cdot\frac{2(x-a)}{((x-a)^2+b^2)^\ell} + (\delta+a\gamma)\cdot\frac1{((x-a)^2+b^2)^\ell},$$
with, for $\ell=1$: $\int\frac{2(x-a)}{(x-a)^2+b^2}dx=\ln((x-a)^2+b^2)+C$ and
$\int\frac{dx}{(x-a)^2+b^2}=\frac1b\arctan\frac{x-a}b+C$; for $\ell>1$:
$\int\frac{2(x-a)}{((x-a)^2+b^2)^\ell}dx = \frac{-1}{(\ell-1)((x-a)^2+b^2)^{\ell-1}}+C$,
and the recursion $I_\ell=\int\frac{dx}{(x^2+1)^\ell} = \frac1{2(\ell-1)}\left[(3-2\ell)I_{\ell-1}-\frac{x}{(x^2+1)^{\ell-1}}\right]$
for $\ell\ge2$ (matches [[integration-techniques]] exactly).

Worked small example: $\int\frac{2x-2}{x^2-2x+2}dx = \ln(x^2-2x+2) + \text{(via the }\ell=1\text{ formulas above)}$,
with $x^2-2x+2=(x-1)^2+1$.

### Volumes and surfaces of revolution (recap, matches lecture)

$$V_{\mathrm{rot}}=\pi\int_a^b f(x)^2\,dx, \qquad O_{\mathrm{rot}}=2\pi\int_a^b f(x)\sqrt{1+f'(x)^2}\,dx.$$
Also noted: ellipse area $A=\pi ab$; sphere volume $V=\frac43\pi r^3$; sphere
surface $O=4\pi r^2$ (all consistent with
[[analysis2-02-integration-curves-fourier-quadrature-fft]]).

### Improper integrals — convergence criteria

$\int f\,dx$ is **absolutely convergent** iff $\int|f|\,dx$ converges.
- **Majorant criterion:** $|f(x)|\le g(x)\ \forall x$, $\int g\,dx$ convergent $\Rightarrow \int f\,dx$ absolutely convergent.
- **Minorant criterion:** $0\le g(x)\le f(x)\ \forall x$, $\int g\,dx$ divergent $\Rightarrow \int f\,dx$ divergent.

(Matches [[improper-integrals]] exactly.)

### Parameter-dependent integrals

$$F(x) := \int f(x,y)\,dy, \qquad F'(x) = \frac{d}{dx}\int f(x,y)\,dy = \int \frac{\partial f}{\partial x}(x,y)\,dy$$
(Leibniz rule — matches [[integration-techniques]]).

---

## Page 2

### Fixed-point iteration / Banach theorem recap (matches existing wiki exactly)

$$\|x_n-x^*\| \le \frac{L^n}{1-L}\|x_1-x_0\| \ \text{(a priori)}, \qquad \|x_n-x^*\|\le\frac{L}{1-L}\|x_n-x_{n-1}\| \ \text{(a posteriori)}.$$
$\Phi$ contracting on $[a,b]$ with $L=\sup_{a\le x\le b}|\Phi'(x)|$; Lipschitz
continuity $|\Phi(x)-\Phi(y)|\le L|x-y|$. (See [[banach-fixed-point-theorem]].)

### Uniform / pointwise convergence of function sequences (recap)

$(f_n)_{n\in\mathbb N}$, $f_n:D\to\mathbb C$: **pointwise** convergent to $f$ iff
$\forall x\in D: \lim_n f_n(x)=f(x)$; **uniformly** convergent iff
$\lim_n \sup_{z\in D}|f_n(z)-f(z)|=0$.

**Weierstraß majorant criterion:** $|f_n(z)|\le b_n\ \forall z$, $\sum b_n$
convergent $\Rightarrow \sum f_n(z)$ uniformly and absolutely convergent (proof
sketch via the Cauchy tail estimate
$|\sum_{k=m+1}^n f_k(z)| \le \sum_{k=m+1}^n|f_k(z)| \le \sum_{k=m+1}^n b_k<\epsilon$).
**Continuity theorem:** $f_n$ continuous $\forall n$, $f_n\to f$ uniformly
$\Rightarrow f$ continuous. (Matches [[function-sequences-and-uniform-convergence]].)

### Integration of power series

For $f(x)=\sum_{k=0}^\infty a_k(x-x_0)^k$, the antiderivative is
$$F(x) = C + \sum_{k=0}^\infty \frac{a_k}{k+1}(x-x_0)^{k+1}, \qquad C\in\mathbb R$$
(same radius of convergence preserved — matches [[power-series]]).

### Interpolation (NEW — fills the Chapter 9 gap)

**Lagrange interpolation.** For nodes $x_0,\dots,x_n$ and data $f(x_0),\dots,f(x_n)$:
$$L_k(x) := \prod_{\substack{j=0\\j\ne k}}^n \frac{x-x_j}{x_k-x_j}, \qquad p_n(x) := \sum_{k=0}^n f(x_k)\,L_k(x)$$
(the unique degree-$\le n$ polynomial interpolating the data; $L_k(x_j)=\delta_{kj}$).

**Newton's divided-difference representation.** The same interpolation polynomial
can be written incrementally as
$$p_n(x) = c_0 + c_1(x-x_0) + c_2(x-x_0)(x-x_1) + \dots + c_n(x-x_0)(x-x_1)\cdots(x-x_{n-1}),$$
with coefficients $c_k = f[x_0,\dots,x_k]$, the **divided differences** of $f$
(defined recursively, $f[x_i]:=f(x_i)$,
$f[x_i,\dots,x_{i+k}] := \frac{f[x_{i+1},\dots,x_{i+k}]-f[x_i,\dots,x_{i+k-1}]}{x_{i+k}-x_i}$).
Advantage over the Lagrange form: adding one more data point only adds one more
term (no need to recompute the whole polynomial).

**Cubic spline interpolation.** For nodes $x_0<x_1<\dots<x_n$ with
$h_i:=x_{i+1}-x_i$, the natural cubic spline $S$ consists of piecewise cubics
$$S_i(x) = a_i + b_i(x-x_i) + c_i(x-x_i)^2 + d_i(x-x_i)^3, \qquad x_i\le x\le x_{i+1},$$
matching function values at the nodes, with $S\in C^2$ (continuous first and
second derivatives across nodes) and natural boundary conditions
$S''(x_0)=S''(x_n)=0$. Writing $M_i := S''(x_i)$ (the "moments"), the standard
relations are (as transcribed from the handwritten sheet, with some symbol
uncertainty flagged):
$$a_i = f(x_i), \qquad c_i = \frac{M_i}2, \qquad d_i = \frac{M_{i+1}-M_i}{6h_i},$$
$$b_i = \frac{f(x_{i+1})-f(x_i)}{h_i} - \frac{h_i}6(2M_i+M_{i+1}),$$
with the $M_i$ determined by solving a tridiagonal linear system coupling
consecutive intervals (continuity of $S''$ across interior nodes) — *the exact
right-hand-side terms of this tridiagonal system were not fully legible in the
handwriting and should be double-checked against a numerical-analysis reference
if used for computation; the general cubic-spline structure above is standard
and consistent with the rest of the course.*

### Weierstraß substitution (recap, matches lecture exactly)

$$\int \frac{P(\sin x,\cos x)}{Q(\sin x,\cos x)}\,dx, \qquad t=\tan\tfrac x2 \implies dx=\frac{2\,dt}{t^2+1}, \quad \sin x = \frac{2t}{t^2+1}, \quad \cos x = \frac{1-t^2}{t^2+1}.$$

---

## Notes for the wiki

- Most of this sheet recaps/confirms lecture material already in the wiki
  (integration techniques, improper integrals, fixed-point iteration, uniform
  convergence, power series) — no contradictions found.
- **New content:** Lagrange interpolation, Newton's divided-difference form, and
  cubic spline interpolation — these were not present in the two Analysis 2
  lecture PDFs. Created [[interpolation]] to capture this and partially close the
  "Chapter 9" gap noted in `wiki/index.md`. The cubic-spline coefficient
  formulas are transcribed with a flagged uncertainty around the exact
  tridiagonal system for the $M_i$ — worth confirming against the original
  lecture material if that chapter's source is later located.
