---
title: "Analysis 3 — Handwritten Formula Sheet"
module: analysis3
type: summary
sources: [raw/analysis3/analysis_3_formulas.pdf]
updated: 2026-10-25
---

# Overview

Two pages of genuinely handwritten (blue ink, grid paper) condensed formulas for
Analysis 3, covering partial derivatives/extrema, the Hessian test, tangent
planes/total differential, curvilinear coordinates, implicit functions/curves,
constrained extrema (Lagrange multipliers), normal domains, the transformation
theorem, curve integrals of the 2nd kind, Green's theorem, moments of inertia /
Steiner's theorem, and potentials. This sheet is **denser and harder to
transcribe with full confidence** than the typed lecture slides — several
entries are abbreviated shorthand. Everything legible matches the lecture
content already ingested; no contradictions found. Ambiguous passages are
flagged explicitly rather than guessed.

Related: [[multivariable-taylor-and-extrema]],
[[multivariable-chain-rule-and-jacobian]], [[implicit-function-theorem]],
[[lagrange-multipliers]], [[multiple-integrals-and-fubini]],
[[curve-and-surface-integrals]], [[vector-calculus-integral-theorems]].

---

## Page 1

### Partial derivatives and extrema (recap, matches lecture)

$$\frac{\partial f}{\partial x_i}(x^0) = \lim_{t\to0}\frac{f(x^0+te_i)-f(x^0)}t.$$
Extrema: local extremum $\Rightarrow \mathrm{grad}\,f(x^0)=0$; Hessian test:
$H_f(x^0)$ positive definite $\Rightarrow$ strict local min; negative definite
$\Rightarrow$ strict local max; indefinite $\Rightarrow$ saddle point. (Matches
[[multivariable-taylor-and-extrema]] exactly.)

### Tangent plane / total differential / chain rule (recap)

Tangent-plane linearization $z \approx f(x^0)+\mathrm{grad}\,f(x^0)\cdot(x-x^0,y-y^0)$;
total differential $df=\sum_i\partial_{x_i}f\,dx_i$; chain rule for composed
functions. Coordinate transformations $\mathbf x=\Phi(\mathbf u)$ with Jacobi
matrices recorded for polar $(r,\varphi)$ and spherical $(r,\varphi,\theta)$
coordinates — matches
[[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]].

### Nabla / divergence / harmonic functions (recap)

$\nabla f=\mathrm{grad}\,f$; $\mathrm{div}\,\mathbf g(x)=\dots$; "harmonic" noted
as $\Delta g=0$. One entry labeled "Stromlinie" (streamline) with a relation
$g(x)=c(t)$-style condition — **not fully legible**; likely a note that a flow's
streamlines are level curves of some associated function, but this should be
double-checked against the original scan or a numerical-methods/fluid-dynamics
reference if needed.

### Implicit functions and implicit curves (recap, matches lecture)

$g(x,y)=0$, $\mathrm{grad}\,g\ne0 \Rightarrow$ regular point (else singular);
singular-point classification via $\det H_g$: $>0$ isolated point, $<0$ double
point, $=0$ cusp ("Rückkehrpunkt"). Horizontal tangent: $g=0,\ g_y\ne0$; vertical
tangent: $g=0,\ g_x\ne0$. Implicit surfaces: $g(x,y,z)=0$, $\mathrm{grad}\,g\ne0
\Rightarrow$ locally $z=f(x,y)$ with $\mathrm{grad}\,f=-\frac1{g_z}(g_x,g_y)$.
All consistent with [[implicit-function-theorem]].

### Constrained extrema / Lagrange multipliers (recap, matches lecture)

$$G=\{x\in D\mid g(x)=0\}, \qquad \mathrm{rang}(Jg(x^0))=m, \qquad F(x,\lambda)=f(x)+\sum_i\lambda_ig_i(x), \qquad \mathrm{grad}\,F(x^0,\lambda)=0.$$
Sufficient condition: $H_F(x^0)$ positive definite on
$TG(x^0)=\{y\in\mathbb R^n\mid\mathrm{grad}\,g_i(x^0)\cdot y=0\} \Rightarrow$
strict local minimum. Matches [[lagrange-multipliers]] exactly.

### Normal domains and the transformation theorem (recap)

$$D=\{(x,y)\mid a\le x\le b,\ g(x)\le y\le h(x)\}, \qquad \int_{\Phi(D)}f(x)\,dx = \int_Df(\Phi(u))\,|\det J\Phi(u)|\,du$$
(matches [[multiple-integrals-and-fubini]]). One bottom-left formula (labeled
something like "Hesse" or possibly "Masse"/mass, written
$\int\!\!\int f(x,y)\cdot d(x,y)$) was **not legible enough to transcribe with
confidence** — likely either a repeat of the mass/center-of-mass integral
$\int_D\rho(x,y)\,d(x,y)$ or an unrelated shorthand; flagged for the user to
double check against the original page if needed.

### Curve integral (2nd kind) and Green's integral theorem (recap)

$$\int_c f(x)\,dx = \int_a^b\langle f(c(t)),\dot c(t)\rangle\,dt, \qquad \int_D \mathrm{rot}\,f(x)\,dx = \oint_{\partial D}f(x)\,dx \quad (\partial D \text{ a normal-domain boundary}).$$
Matches [[curve-and-surface-integrals]] and
[[vector-calculus-integral-theorems]] exactly.

---

## Page 2

### Moment of inertia and Steiner's theorem (recap, matches lecture)

$$\Theta_A = \int_D\rho(x,y)\,r(x,y)^2\,d(x,y), \qquad r(x,y) = \text{distance to axis } A, \qquad \Theta_A = Md^2+\Theta_S$$
($M$ total mass, $d$ = distance from centroid $S$ to axis $A$). Matches
[[multiple-integrals-and-fubini]] (Steiner's theorem section) exactly.

### Curve integral (2nd kind) / Green's theorem (repeated, consistent)

Same formulas as on page 1, repeated for emphasis.

### Potentials and the integrability condition (recap, matches lecture)

$$f \text{ has a potential } \varphi(x): \quad \mathrm{grad}\,\varphi(x)=f(x), \qquad \text{integrability condition: } \mathrm{rot}\,f(x)=0\ !$$
(a) $\int_c f(x)\,dx = \varphi(c(b))-\varphi(c(a))$.
(b) $\varphi(x) = \int_{c_x}f(x)\,dx + C$, where $c_x$ is any path from a fixed
base point $x_0\in D$ to $x$.

The exclamation mark after "$\mathrm{rot}\,f(x)=0$" in the handwriting appears to
be the user's own note-to-self flagging the **simple-connectedness caveat**
discussed in [[vector-calculus-integral-theorems]] (curl-free is necessary but
only sufficient for a potential on a simply connected domain) — consistent with,
and a nice personal confirmation of, that subtlety from the lecture.

---

## Notes for the wiki

- This sheet is almost entirely a condensed recap of
  [[analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton]] and
  [[analysis3-02-multiple-integrals-fubini-curve-surface-green-gauss-stokes]] —
  no contradictions, no new theorems. No new wiki pages were created from this
  source; existing pages already cover everything legible here.
- Two passages were too compressed/ambiguous to transcribe with confidence
  ("Stromlinie" entry, one "Hesse"/"Masse"-labeled double integral on page 1) —
  flagged inline above. Worth a manual check against the original handwritten
  page if precision matters for exam prep.
