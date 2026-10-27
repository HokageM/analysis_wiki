---
title: "Analysis 3 — Lecture Slides 1 (Ch. 17–19 start): Multivariable Differential Calculus, Extrema, Implicit Functions, Lagrange Multipliers, Newton's Method"
module: analysis3
type: summary
sources: [raw/analysis3/analysis_3_1.pdf]
updated: 2026-10-25
---

# Overview

Source: *Mathematik III / Analysis III für Studierende der Ingenieurwissenschaften*,
Prof. Dr. Armin Iske, TUHH, Wintersemester 2019/2020, lecture slides (4-up), 32
sheets, slides 1–124. Course table of contents: partial derivatives/differential
operators, vector fields/total differential/directional derivatives, mean value
theorems/Taylor's theorem (multivariable), extrema/implicit function theorem,
implicit curves/surfaces, constrained extrema, Newton's method/nonlinear
equations/least-squares fitting, multiple integrals/Fubini/transformation
theorem, potentials/Green's theorem/Gauss's theorem, Stokes' formulas.

This source covers **Chapter 17** (multivariable differential calculus) and
**Chapter 18** (applications: extrema, implicit functions, Lagrange multipliers,
Newton's method) in full, plus the very start of **Chapter 19** (multiple integrals).

Related: [[partial-derivatives-and-gradient]], [[vector-calculus-operators]],
[[multivariable-chain-rule-and-jacobian]], [[multivariable-taylor-and-extrema]],
[[implicit-function-theorem]], [[lagrange-multipliers]],
[[multivariable-newton-method]].

---

## Chapter 17 — Differential Calculus of Several Variables

### 17.1 Partial derivatives

For $f:D\to\mathbb R$, $D\subset\mathbb R^n$ open, $x^0\in D$: $f$ is **partially
differentiable** at $x^0$ w.r.t. $x_i$ if
$$\frac{\partial f}{\partial x_i}(x^0) := \lim_{t\to0}\frac{f(x^0+te_i)-f(x^0)}{t}$$
exists ($e_i$ = $i$-th unit vector). If this holds at every point of $D$ for every
$i$ and the resulting functions are continuous, $f$ is **continuously partially
differentiable**, or a $C^1$-function.

**Critical warning:** partial differentiability does **not** imply continuity.
Counterexample: $f(x,y)=\frac{xy}{x^2+y^2}$ for $(x,y)\ne(0,0)$, $f(0,0)=0$: both
partials exist at every point (even at the origin, $f_x(0,0)=f_y(0,0)=0$), but $f$
is **not continuous** at $(0,0)$ (approaching along $y=x$: $f(1/n,1/n)=1/2\ne0$).

**Differentiation rules** (sums, products, quotients) carry over componentwise
from the single-variable case: $\partial_{x_i}(\alpha f+\beta g) = \alpha\partial_{x_i}f+\beta\partial_{x_i}g$,
$\partial_{x_i}(fg)=\partial_{x_i}f\cdot g+f\cdot\partial_{x_i}g$,
$\partial_{x_i}(f/g) = \frac{\partial_{x_i}f\cdot g-f\cdot\partial_{x_i}g}{g^2}$.

### Gradient and nabla operator

$$\mathrm{grad}\,f(x^0) := \left(\frac{\partial f}{\partial x_1}(x^0),\dots,\frac{\partial f}{\partial x_n}(x^0)\right) \ (\text{row vector}), \qquad \nabla := \left(\frac{\partial}{\partial x_1},\dots,\frac{\partial}{\partial x_n}\right)^T \ (\text{column, "nabla operator"}).$$
Rules: $\mathrm{grad}(\alpha f+\beta g)=\alpha\,\mathrm{grad}\,f+\beta\,\mathrm{grad}\,g$;
$\mathrm{grad}(f\cdot g)=g\cdot\mathrm{grad}\,f+f\cdot\mathrm{grad}\,g$;
$\mathrm{grad}(f/g)=\frac1{g^2}(g\,\mathrm{grad}\,f-f\,\mathrm{grad}\,g)$ ($g\ne0$).

### Higher-order derivatives & Schwarz's theorem

$\partial^2f/\partial x_i\partial x_j$, etc. **Schwarz's theorem (symmetry of
mixed partials):** if $f\in C^2(D)$, $D$ open, then
$$\frac{\partial^2f}{\partial x_j\partial x_i}(x) = \frac{\partial^2f}{\partial x_i\partial x_j}(x) \qquad \forall x\in D.$$
(Proof: double application of the single-variable MVT.) **Corollary:** for
$f\in C^k$, the order of differentiation in any mixed partial of order $\le k$ can
be freely permuted. **Counterexample without $C^2$:**
$f(x,y)=xy\frac{x^2-y^2}{x^2+y^2}$ ($f(0,0)=0$) has $f_{xy}(0,0)=-1\ne+1=f_{yx}(0,0)$
— mixed partials can disagree if $f\notin C^2$.

### The Laplace operator

$$\Delta u := \sum_{i=1}^n\frac{\partial^2u}{\partial x_i^2} = u_{x_1x_1}+\dots+u_{x_nx_n}.$$
Relevant PDEs: wave equation $\Delta u - \frac1{c^2}u_{tt}=0$; heat equation
$\Delta u - \frac1k u_t = 0$; Laplace/potential equation $\Delta u=0$
("$u$ is **harmonic**"). Worked radial example: for $u(x)=u(r(x))$, $r=\|x\|_2$:
$\Delta u = u''(r) + \frac{n-1}r u'(r)$.

### Vector fields, divergence, curl

$\mathbf f:D\to\mathbb R^m$ ($D\subset\mathbb R^n$ open) is a **vector field** if
$m=n$ and each component $f_i$ is $C^k$. **Divergence** (for $\mathbf f:D\to\mathbb R^n$):
$$\mathrm{div}\,\mathbf f(x) := \sum_{i=1}^n\frac{\partial f_i}{\partial x_i}(x) = \langle\nabla,\mathbf f(x)\rangle.$$
Rules: $\mathrm{div}(\alpha\mathbf f+\beta\mathbf g)=\alpha\,\mathrm{div}\,\mathbf f+\beta\,\mathrm{div}\,\mathbf g$;
$\mathrm{div}(\varphi\mathbf f)=\nabla\varphi\cdot\mathbf f+\varphi\,\mathrm{div}\,\mathbf f$;
and $\Delta f = \mathrm{div}(\mathrm{grad}\,f)$. **Curl** (for $\mathbf f:D\to\mathbb R^3$):
$$\mathrm{rot}\,\mathbf f(x) := \left(\frac{\partial f_3}{\partial x_2}-\frac{\partial f_2}{\partial x_3},\ \frac{\partial f_1}{\partial x_3}-\frac{\partial f_3}{\partial x_1},\ \frac{\partial f_2}{\partial x_1}-\frac{\partial f_1}{\partial x_2}\right) = \nabla\times\mathbf f(x).$$
Rules: linearity; $\mathrm{rot}(\varphi\mathbf f)=\nabla\varphi\times\mathbf f+\varphi\,\mathrm{rot}\,\mathbf f$;
and (via Schwarz's theorem) $\mathrm{rot}(\mathrm{grad}\,f)=\mathbf 0$ — **every
gradient field is curl-free (irrotational)**.

### 17.2 The total differential

$f:D\to\mathbb R^m$ ($D\subset\mathbb R^n$ open) is **(totally) differentiable**
at $x^0$ if there is a linear map $\mathbf l(x):=A\cdot(x-x^0)$ ($A\in\mathbb R^{m\times n}$)
with $f(x)=f(x^0)+A(x-x^0)+o(\|x-x^0\|)$, i.e.
$$\lim_{x\to x^0}\frac{f(x)-f(x^0)-A(x-x^0)}{\|x-x^0\|}=\mathbf 0.$$
The matrix $A$ is uniquely determined — the **Jacobi matrix** $Jf(x^0)$ (also
$Df(x^0)$ or $f'(x^0)$):
$$Jf(x^0) = \begin{pmatrix}\mathrm{grad}\,f_1(x^0)\\ \vdots\\ \mathrm{grad}\,f_m(x^0)\end{pmatrix} \in \mathbb R^{m\times n}.$$

**Theorem (complete vs. partial differentiability):** (a) differentiable at
$x^0 \Rightarrow$ continuous at $x^0$; (b) differentiable at $x^0 \Rightarrow$ all
partials exist and $Jf(x^0)$ is as above; (c) $f\in C^1(D) \Rightarrow f$
differentiable on $D$ (continuity of partials upgrades mere partial
differentiability to full differentiability).

Worked Jacobi-matrix examples: $f(x_1,x_2)=x_1e^{2x_2} \Rightarrow Jf=e^{2x_2}(1,2x_1)$;
for $f(x)=Ax$ ($A\in\mathbb R^{m\times n}$): $Jf(x)=A$ (constant); for
$f(x)=x^TAx$ ($A\in\mathbb R^{n\times n}$): $\mathrm{grad}\,f(x)=x^T(A^T+A)$.

### 17.2 (cont.) Differentiation rules for total derivatives

**Linearity:** $d(\alpha f+\beta g)(x^0)=\alpha\,df(x^0)+\beta\,dg(x^0)$,
$J(\alpha f+\beta g)=\alpha Jf+\beta Jg$. **Chain rule:** for $f:D\to\mathbb R^m$
differentiable at $x^0$, $g:E\to\mathbb R^k$ differentiable at $y^0=f(x^0)$:
$$J(g\circ f)(x^0) = Jg(y^0)\cdot Jf(x^0).$$
Worked chain-rule example (curve composition): for a curve $h:I\to\mathbb R^n$
differentiable at $t_0$ and $f:D\to\mathbb R$ differentiable at $x^0=h(t_0)$:
$$(f\circ h)'(t_0) = Jf(h(t_0))\cdot h'(t_0) = \mathrm{grad}\,f(h(t_0))\cdot h'(t_0) = \sum_{k=1}^n\frac{\partial f}{\partial x_k}(h(t_0))\,h_k'(t_0).$$

### Directional derivatives and gradient properties

$$D_{\mathbf v}f(x^0) := \lim_{t\to0}\frac{f(x^0+t\mathbf v)-f(x^0)}{t}, \qquad \mathbf v\ne\mathbf 0 \ \text{("Gateaux derivative in direction } \mathbf v\text{")}.$$
For $\|\mathbf v\|=1$, $D_{\mathbf v}f(x^0) = \mathrm{grad}\,f(x^0)\cdot\mathbf v$ (if
$f$ differentiable at $x^0$) — follows from the chain rule applied to
$h(t)=x^0+t\mathbf v$.

**Gradient properties theorem.** (a) $\mathrm{grad}\,f(x^0)$ is perpendicular to
the level set $N_{x^0}:=\{x\in D\mid f(x)=f(x^0)\}$ through $x^0$ (in $n=2$:
perpendicular to contour/"Höhenlinien"; $n=3$: perpendicular to
equipotential/"Äquipotentialflächen"). (b) By the **Cauchy–Schwarz inequality**,
$|D_{\mathbf v}f(x^0)| = |\langle\mathrm{grad}\,f(x^0),\mathbf v\rangle| \le \|\mathrm{grad}\,f(x^0)\|_2\|\mathbf v\|_2$,
with equality iff $\mathbf v=\mathrm{grad}\,f(x^0)/\|\mathrm{grad}\,f(x^0)\|_2$ —
**the gradient points in the direction of steepest ascent.**

### Curvilinear coordinates

For a $C^1$ coordinate transformation $\Phi:U\to V$ ($\mathbf x=\Phi(\mathbf u)$,
Jacobi matrix regular, $C^1$ inverse $\Phi^{-1}$): chain rule for Jacobians of a
composed function $\tilde f(\mathbf u):=f(\Phi(\mathbf u))$:
$$\mathbf G(\mathbf u) := (g^{ij}(\mathbf u)) = (J\Phi(\mathbf u))^T, \qquad \frac{\partial f}{\partial u_i} = \sum_j g^{ij}\frac{\partial f}{\partial x_j}, \qquad (g_{ij}) := (g^{ij})^{-1} = (J\Phi)^{-1}.$$

**Polar coordinates** $\mathbf x=\Phi(r,\varphi)=(r\cos\varphi,r\sin\varphi)$:
$$J\Phi = \begin{pmatrix}\cos\varphi & -r\sin\varphi\\ \sin\varphi & r\cos\varphi\end{pmatrix}, \qquad \frac{\partial}{\partial x}=\cos\varphi\frac\partial{\partial r}-\frac{\sin\varphi}r\frac\partial{\partial\varphi}, \qquad \frac\partial{\partial y}=\sin\varphi\frac\partial{\partial r}+\frac{\cos\varphi}r\frac\partial{\partial\varphi}.$$
**Laplacian in polar coordinates:**
$$\Delta = \frac{\partial^2}{\partial r^2}+\frac1{r^2}\frac{\partial^2}{\partial\varphi^2}+\frac1r\frac\partial{\partial r}.$$
**Spherical coordinates** $\mathbf x=\Phi(r,\varphi,\theta)=(r\cos\varphi\cos\theta, r\sin\varphi\cos\theta, r\sin\theta)$,
with Jacobian given explicitly in the source, and
$$\Delta = \frac{\partial^2}{\partial r^2}+\frac1{r^2\cos^2\theta}\frac{\partial^2}{\partial\varphi^2}+\frac1{r^2}\frac{\partial^2}{\partial\theta^2}+\frac2r\frac\partial{\partial r}-\frac{\tan\theta}{r^2}\frac\partial{\partial\theta}.$$

### 17.3 Mean value theorems and Taylor expansions (multivariable)

**Multivariable MVT (scalar-valued):** $f:D\to\mathbb R$ differentiable, $D$ open,
$[a,b]\subset D$ (the connecting segment), $\Rightarrow \exists\theta\in(0,1)$:
$$f(b)-f(a) = \mathrm{grad}\,f(a+\theta(b-a))\cdot(b-a)$$
(proof via single-variable MVT applied to $h(t):=f(a+t(b-a))$, $h'(t)=\mathrm{grad}\,f(a+t(b-a))\cdot(b-a)$).
**Critical warning:** this MVT holds **only for scalar-valued** $f$, not
vector-valued (counterexample: $f(t)=(\cos t,\sin t)^T$ on $[0,\pi/2]$ — no
single $\theta$ reproduces $f(b)-f(a)$ via $f'(\theta)\cdot(b-a)$, since the
secant and tangent vectors have different lengths/directions along the arc).

**Mean value estimate theorem (scalar):** $\|f(b)-f(a)\|\le\|\mathrm{grad}\,f(\xi)\|_2\|b-a\|_2$
for some $\xi$ on the segment (via Cauchy–Schwarz). **General mean value
estimate (vector-valued):** $f:D\to\mathbb R^m$ differentiable,
$$\|f(b)-f(a)\|_2 \le \sup_{t\in[0,1]}\|Jf(a+t(b-a))\|_2\cdot\|b-a\|_2$$
(proved via the integral representation $f(b)-f(a) = \left(\int_0^1Jf(a+t(b-a))\,dt\right)(b-a)$).

**Multivariable Taylor's theorem.** Multi-index notation:
$\alpha=(\alpha_1,\dots,\alpha_n)\in\mathbb N_0^n$, $|\alpha|:=\alpha_1+\dots+\alpha_n$,
$\alpha!:=\alpha_1!\cdots\alpha_n!$, $D^\alpha:=D_1^{\alpha_1}\cdots D_n^{\alpha_n}$
(where $D_i^{\alpha_i}$ means differentiating $\alpha_i$ times w.r.t. $x_i$),
$\mathbf x^\alpha := x_1^{\alpha_1}\cdots x_n^{\alpha_n}$. For
$f\in C^{m+1}(D)$, $D\subset\mathbb R^n$ open and convex, $x^0\in D$:
$$f(x) = T_m(x;x^0) + R_m(x;x^0), \qquad T_m(x;x^0) := \sum_{|\alpha|\le m}\frac{D^\alpha f(x^0)}{\alpha!}(x-x^0)^\alpha, \qquad R_m(x;x^0) := \sum_{|\alpha|=m+1}\frac{D^\alpha f(x^0+\theta(x-x^0))}{\alpha!}(x-x^0)^\alpha$$
for some $\theta\in(0,1)$. **Proof** via the auxiliary single-variable function
$g(t):=f(x^0+t(x-x^0))$ and repeated application of the chain rule + Schwarz's
theorem + single-variable Taylor's theorem (by induction on $k$ for $g^{(k)}(0)$).

**Remainder estimate:** if all order-$(m+1)$ partials are bounded by $C$ on a
neighborhood of $x^0$, $|R_m(x;x^0)| \le \binom{n+m}{m}C\|x-x^0\|_\infty^{m+1}$
(so $R_m(x;x^0) = \mathcal O(\|x-x^0\|_\infty^{m+1})$, and
$f(x) = T_m(x;x^0) + \mathcal O(\|x-x^0\|^{m+1})$).

**Special case $m=1$:** $f(x) = f(x^0) + \mathrm{grad}\,f(x^0)\cdot(x-x^0) + \mathcal O(\|x-x^0\|^2)$.
Worked degree-2 Taylor polynomial: $f(x,y,z)=xy^2\sin z$ at $(1,2,0)$:
$T_2(x;x^0) = 4z(x+y-2)$ *(as transcribed — matches a linearization dominated by
the $z$-direction near this particular expansion point, since $\sin z\approx z$ there)*.

### The Hesse (Hessian) matrix

$$H_f(x^0) := \begin{pmatrix}f_{x_1x_1}(x^0) & \cdots & f_{x_1x_n}(x^0)\\ \vdots & & \vdots\\ f_{x_nx_1}(x^0) & \cdots & f_{x_nx_n}(x^0)\end{pmatrix} = \text{Jacobi matrix of } \mathrm{grad}\,f \text{ at } x^0.$$
Degree-2 Taylor expansion of a $C^3$ function:
$$f(x) = f(x^0) + \mathrm{grad}\,f(x^0)(x-x^0) + \tfrac12(x-x^0)^TH_f(x^0)(x-x^0) + \mathcal O(\|x-x^0\|^3).$$
**The Hessian of a $C^2$ function is symmetric** (by Schwarz's theorem).

## Chapter 18 — Applications of Multivariable Differential Calculus

### 18.1 Extrema of multivariable functions

Global/local (strict) max/min — standard definitions, analogous to the
single-variable case. **Necessary condition:** local extremum at interior
$x^0\in D^0 \Rightarrow \mathrm{grad}\,f(x^0)=\mathbf 0$ (**stationary point**).
(Proof: restrict to each coordinate direction, apply the 1D necessary condition.)
**Remark:** $\mathrm{grad}\,f(x^0)=\mathbf 0$ is $n$ equations in $n$ unknowns —
generally a nonlinear system. Not every stationary point is an extremum (e.g.
$f(x,y)=x^2-y^2$ has a stationary, non-extremal **saddle point** at the origin).
**Saddle point:** every neighborhood of $x^0$ contains points $x^1,x^2$ with
$f(x^1)<f(x^0)<f(x^2)$.

**Sufficient condition (via the Hessian):**
(a) $x^0$ stationary, $H_f(x^0)$ **positive (negative) semidefinite** is
**necessary** for a local min (max).
(b) $x^0$ stationary, $H_f(x^0)$ **positive (negative) definite** is **sufficient**
for a strict local min (max). (Proof via the degree-2 Taylor expansion:
$f(x^0+\epsilon v)-f(x^0) = \tfrac12\epsilon^2v^TH_f(x^0+\theta\epsilon v)v$, letting
$\epsilon\to0$ and using continuity of $H_f$.)
(c) $x^0$ stationary, $H_f(x^0)$ **indefinite** (mixed-sign eigenvalues)
$\Rightarrow x^0$ is a **saddle point**.

**Geometric interpretation:** eigenvectors of $H_f(x^0)$ with positive eigenvalues
point in directions where $f$ grows; negative eigenvalues, directions where $f$
falls.

**Classification via $\det H_f(x^0)=0$ (degenerate/"ausgeartete" case, $n=2$):**
if the stationary point is not degenerate ($\det H_f(x^0)\ne0$), exactly 3 cases:
all eigenvalues positive $\Rightarrow$ strict local min; all negative
$\Rightarrow$ strict local max; mixed sign $\Rightarrow$ saddle point. Logical
implications (not reversible in general):
$$x^0 \text{ local min} \Leftarrow x^0 \text{ strict local min} \Leftarrow H_f(x^0) \text{ pos. definite} \Rightarrow H_f(x^0)\text{ pos. semidefinite}.$$

**Estimate theorem:** if $H_f(x^0)$ positive definite with smallest eigenvalue
$\lambda_{\min}>0$, then $f(x)-f(x^0) \ge \|x-x^0\|^2\left(\frac{\lambda_{\min}}2-C\|x-x^0\|\right)$
for a suitable constant $C$ and $x$ near $x^0$ — i.e. $f$ grows at least
quadratically away from $x^0$.

### 18.2 Implicitly defined functions

**Setup:** solve $\mathbf g(\mathbf x)=\mathbf 0$ for $m$ of the $n$ unknowns in
terms of the remaining $n-m$ ("underdetermined" system, generally with infinitely
many solutions forming a solution set $G\subset\mathbb R^n$). **Resolvability
question:** can the last $m$ variables $x_{n-m+1},\dots,x_n$ be written as
functions of the first $n-m$? I.e. does
$$\mathbf g(\mathbf x) = \mathbf 0 \iff (x_{n-m+1},\dots,x_n)^T = \mathbf f(x_1,\dots,x_{n-m})$$
hold, globally on $D$ or only locally near a point $\tilde D\subset D$?

Worked linear example: $\mathbf g(\mathbf x)=C\mathbf x+\mathbf b$ (affine),
splitting $\mathbf x=(\mathbf x^{(1)},\mathbf x^{(2)})$ and $C=[B,A]$:
$\mathbf g(\mathbf x)=0$ is uniquely solvable for $\mathbf x^{(2)}$ iff $A$ is
regular, giving $\mathbf x^{(2)} = -A^{-1}(B\mathbf x^{(1)}+\mathbf b) =: \mathbf f(\mathbf x^{(1)})$.

**Implicit function theorem.** $\mathbf g:D\to\mathbb R^m$ ($D\subset\mathbb R^{n-m}\times\mathbb R^m$
open) a $C^1$-function, $(\mathbf x^0,\mathbf y^0)\in D$ with $\mathbf g(\mathbf x^0,\mathbf y^0)=\mathbf 0$
and $\partial\mathbf g/\partial\mathbf y(\mathbf x^0,\mathbf y^0)$ **regular**
($m\times m$ Jacobian w.r.t. the $\mathbf y$-block). Then there exist
neighborhoods $U$ of $\mathbf x^0$, $V$ of $\mathbf y^0$, $U\times V\subset D$,
and a **unique** continuously differentiable $\mathbf f:U\to V$ with
$\mathbf f(\mathbf x^0)=\mathbf y^0$ and
$$\mathbf g(\mathbf x,\mathbf f(\mathbf x))=\mathbf 0 \quad\forall \mathbf x\in U, \qquad J\mathbf f(\mathbf x) = -\left(\frac{\partial\mathbf g}{\partial\mathbf y}(\mathbf x,\mathbf f(\mathbf x))\right)^{-1}\left(\frac{\partial\mathbf g}{\partial\mathbf x}(\mathbf x,\mathbf f(\mathbf x))\right).$$

Worked examples: circle $g(x,y)=x^2+y^2-r^2=0$, solvable near $(x^0,r)$ as
$y=f(x)=\sqrt{r^2-x^2}$, since $g_y(x^0,r)=2r\ne0$. Transcendental example:
$g(x,y)=e^{y-x}+3y+x^2-1=0$ — not explicitly solvable, but implicit
differentiation (via the chain rule on $g(x,f(x))=0$, i.e.
$g_x+g_yf'=0 \Rightarrow f'=-g_x/g_y$) gives $y'=-g_x/g_y$,
$y''=\frac{-g_{xx}g_y^2-2g_{xy}g_xg_y-g_{yy}g_x^2}{g_y^3}$ (general formula).
**Local extrema of implicit functions:** $x^0$ a stationary point of $f$ iff
$g_x(x^0,y^0)=0 \wedge g_y(x^0,y^0)\ne0$, with local min/max determined by the
sign of $g_{xx}(x^0,y^0)/g_y(x^0,y^0)$.

### Implicit curves and surfaces

**Implicit representation of plane curves:** $\{(x,y): g(x,y)=0\}$. If
$\mathrm{grad}\,g\ne\mathbf 0$ at $(x^0,y^0)$, the solution set is **locally** the
graph of a function near that point. $(x^0,y^0)$ is a **regular point** if
$\mathrm{grad}\,g(x^0,y^0)\ne\mathbf 0$, else **singular**. Horizontal tangent at
regular points where $g_y\ne0,\ g_x=0$; vertical tangent where $g_x\ne0,\ g_y=0$.

**Classification of singular points** via the Hessian $H_g(x^0,y^0)$ (where
$g_{xx},g_{xy},g_{yy}\ne0$): $\det H_g>0 \Rightarrow$ **isolated point**;
$\det H_g<0 \Rightarrow$ **double point** (self-intersection); $\det H_g=0
\Rightarrow$ **cusp/"Rückkehrpunkt"** ("spitze"). Near a singular point, the
curve is approximated (2nd order) by $g_{xx}(x-x^0)^2+2g_{xy}(x-x^0)(y-y^0)+g_{yy}(y-y^0)^2=0$.

**Implicit representation of surfaces** in $\mathbb R^3$: $g(x,y,z)=0$ with
$\mathrm{grad}\,g\ne0$ is locally a surface; the tangent plane satisfies
$\mathrm{grad}\,g(x^0)\cdot\Delta x=0$; if $g_z\ne0$, locally $z=f(x,y)$ with
$\mathrm{grad}\,f(x,y) = -\frac1{g_z}(g_x,g_y)$.

**Inverse function theorem:** $\mathbf f:D\to\mathbb R^n$ ($D\subset\mathbb R^n$
open) $C^1$; if $J\mathbf f(x^0)$ is regular at some $x^0$, there are
neighborhoods $U\ni x^0$, $V\ni\mathbf f(x^0)$ such that
$\mathbf f|_U:U\to V$ is bijective with $C^1$ inverse
$\mathbf f^{-1}:V\to U$ ($\mathbf f$ is locally a **$C^1$-diffeomorphism**), and
$J\mathbf f^{-1}(y) = (J\mathbf f(\mathbf f^{-1}(y)))^{-1}$. (Proved by applying
the implicit function theorem to $\mathbf g(\mathbf x,\mathbf y):=\mathbf y-\mathbf f(\mathbf x)$.)

### 18.3 Constrained extrema (Lagrange multipliers)

**Setup:** find extrema of $f:\mathbb R^n\to\mathbb R$ subject to constraints
$\mathbf g(\mathbf x)=\mathbf 0$, $\mathbf g:\mathbb R^n\to\mathbb R^m$ ($m<n$),
i.e. on the constraint set $G:=\{x\in\mathbb R^n\mid\mathbf g(x)=\mathbf 0\}$.

**Necessary condition:** if $f,g_1,\dots,g_m$ are $C^1$ and $x^0\in F(x)$ is a
local extremum with the **regularity condition** $\mathrm{rank}(J\mathbf g(x^0))=m$,
then $\exists\lambda_1,\dots,\lambda_m\in\mathbb R$ (**Lagrange multipliers**):
$$\mathrm{grad}\,f(x^0) + \sum_{i=1}^m\lambda_i\,\mathrm{grad}\,g_i(x^0) = \mathbf 0.$$
Equivalently, with the **Lagrange function** $F(\mathbf x,\boldsymbol\lambda) := f(\mathbf x)+\sum_i\lambda_ig_i(\mathbf x)$:
$\mathrm{grad}\,F(\mathbf x^0,\boldsymbol\lambda)=\mathbf 0$ at the extremum.

**Lagrange's lemma** (used in the proof): the constrained minimizer/maximizer of
$f$ over $G$ is also an unconstrained minimizer/maximizer of
$F(\mathbf x):=f(\mathbf x)+\boldsymbol\lambda^T\mathbf g(\mathbf x)$ over $D$, for
a suitable fixed $\boldsymbol\lambda$.

**Sufficient condition:** if additionally the Hessian $H_F(x^0)$ (of the Lagrange
function) is positive (negative) definite on the **tangent space**
$TG(x^0):=\{y\in\mathbb R^n \mid \mathrm{grad}\,g_i(x^0)\cdot y=0\ \forall i\}$ —
i.e. $y^TH_F(x^0)y>0\ (<0)\ \forall y\in TG(x^0)\setminus\{0\}$ — then $x^0$ is a
strict local min (max) of $f$ under the constraint $\mathbf g=\mathbf 0$.
**Caution:** the sufficient condition is rarely checked in practice, though a
strict extremum does not require it — but it cannot rule out non-extremal
stationary points either (same caveat as the unconstrained Hessian test).

**Worked example (circle constraint):** extrema of $f(x,y)=xy$ on
$g(x,y)=x^2+y^2-1=0$: Lagrange function $F=xy+\lambda(x^2+y^2-1)$, system
$y+2\lambda x=0,\ x+2\lambda y=0,\ x^2+y^2=1$ gives $\lambda=\pm1/2$ with four
critical points $(\pm1/\sqrt2,\pm1/\sqrt2)$; minima at
$(1/\sqrt2,-1/\sqrt2),(-1/\sqrt2,1/\sqrt2)$ (value $-1/2$), maxima at the other two
(value $1/2$).

**Worked example (can-minimization with constraint):** minimize
$f(r,h)=2\pi r^2+2\pi rh$ subject to $g(r,h)=\pi r^2h-c=0$ (fixed volume $c$):
Lagrange function $F=2\pi r^2+2\pi rh+\lambda(\pi r^2h-c)$.

**Worked example (quadric surface + plane):** local extrema of
$f(x,y,z)=2x+3y+2z$ on the intersection of the cylinder $x^2+y^2=2$ and the plane
$x+z=1$: solved via two Lagrange multipliers $\lambda_1,\lambda_2$ (one per
constraint), yielding critical points $(0,\pm\sqrt2,1)$, a max at $(0,\sqrt2,1)$
and min at $(0,-\sqrt2,1)$.

### 18.4 Newton's method (multivariable)

**Setup:** find a zero of $\mathbf f:D\to\mathbb R^n$ ($D\subset\mathbb R^n$),
i.e. $\mathbf f(\mathbf x)=\mathbf 0$. The fixed-point iteration
$x^{k+1}=\Phi(x^k)$ (see [[fixed-point-iteration]]) is available with Banach
convergence guarantees, but is only linearly convergent and the iteration
function $\Phi$ is not unique — motivating **Newton's method**.

**Construction (via linearization/Taylor):** $f(x) = f(x^k)+Jf(x^k)(x-x^k)+o(\|x-x^k\|)$;
setting $x=x^{k+1}$ and dropping $f(x^{k+1})\approx0$ gives the **Newton
correction** $\Delta x^k$ solving the linear system
$$Jf(x^k)\Delta x^k = -f(x^k), \qquad x^{k+1} := x^k+\Delta x^k.$$

**Algorithm (Newton's method):**
```
FOR k = 0, 1, 2, ...:
    (1) Solve  Jf(x^k) * dx^k = -f(x^k)     # linear system for the correction
    (2) Set    x^(k+1) := x^k + dx^k
```
One linear system per step; Newton's method is **invariant under linear
transformations** $f(x)\to g(x):=Af(x)$ ($A$ regular) — the iterates of $f$ and
$g$ coincide for the same starting point (proof: $\Delta x^k$ for $g$ equals
$\Delta x^k$ for $f$, since $Jg=AJf$).

**Local quadratic convergence theorem:** $f\in C^1$ on convex open $D$, $x^*\in D$
a zero of $f$ with $Jf(x^*)$ regular, and $(Jf)^{-1}$ Lipschitz with constant $L$
near $x^*$. Then for $x^0\in K_r(x^*)$, $r$ sufficiently small (specifically
$d:=\|(Jf(x^*))^{-1}\|\cdot L\cdot r <1/2$), Newton's method is well-defined,
stays in $K_r(x^*)$, and converges **quadratically**:
$$\|x^{k+1}-x^*\| \le \tfrac12\|x^k-x^*\|^2 / r \quad(\text{roughly}),\qquad\text{more precisely } \|x^{k+1}-x^*\|\le d\cdot\|x^k-x^*\|^2/r.$$
(Full proof via an auxiliary function $\varphi(t):=(Jf(x^k))^{-1}(f(x^k+t(y-x))-\dots)$
and Lipschitz estimates, mirroring the structure of the Banach fixed-point proof.)
$x^*$ is the **unique** zero of $f$ within $K_r(x^*)$.

**Damped Newton's method.** Pure Newton converges only **locally**; global
convergence can be achieved with a damping factor $\lambda_k\in(0,1]$:
$x^{k+1}:=x^k+\lambda_k\Delta x^k$. **Strategy:** use the test function
$T(x):=\|f(x)\|_2^2\ge0$ ($T(x)=0\iff f(x)=0$); choose $\lambda_k$ so that
$T(x^{k+1})<T(x^k)$ (strictly decreasing test function). **Existence theorem:**
for $f\in C^1$ on convex open $D$ and $x^k\in D$ with $f(x^k)\ne0$, there exists
$\mu_k>0$ such that $\|f(x^k+\lambda\Delta x^k)\|_2^2 < \|f(x^k)\|_2^2$ for all
$\lambda\in(0,\mu_k)$ (proved via $\varphi(\lambda):=\|f(x^k+\lambda\Delta x^k)\|_2^2$,
$\varphi'(0)<0$).

**Damping strategy (pseudocode):**
```
# Initial iteration (k = 0): choose λ0 ∈ {1, 1/2, 1/4, ..., λ_min} as large as possible with
#   ||f(x^0)||_2 > ||f(x^0 + λ0 * Δx^0)||_2

FOR k = 1, 2, 3, ...:
    λ_k := λ_(k-1)
    IF ||f(x^k)||_2 > ||f(x^k + λ_k * Δx^k)||_2 THEN
        x^(k+1) := x^k + λ_k * Δx^k
        λ_k := 2 * λ_k   (if λ_k < 1, try growing it back toward 1 next time)
    ELSE
        μ := max{ λ_k/2, λ_k/4, ..., λ_min } such that ||f(x^k)||_2 > ||f(x^k + μ*Δx^k)||_2
        λ_k := μ
```

### Nonlinear least squares (Gauss–Newton method)

**Problem setting:** fit a parametric model $y=f(t;\mathbf x)$ to measured data
$(t_i,y_i)_{i=1}^m$ ($m\gg n$, overdetermined) by minimizing
$$g(\mathbf x) := \|\mathbf F(\mathbf x)-\mathbf y\|_2^2, \qquad \mathbf F(\mathbf x) := (f(t_1;\mathbf x),\dots,f(t_m;\mathbf x))^T,$$
over the parameter vector $\mathbf x\in\mathbb R^n$.

**Gauss–Newton algorithm:** linearize $\mathbf F$ around the current iterate
$x^k$: $\mathbf F(\mathbf x)\approx\mathbf F(x^k)+J\mathbf F(x^k)(\mathbf x-x^k)$,
then:
```
FOR k = 0, 1, 2, ...:
    (2a) Solve the LINEAR least-squares problem:
           minimize_{Δx}  || JF(x^k) * Δx - (y - F(x^k)) ||_2^2
    (2b) Set x^(k+1) := x^k + Δx
```
Worked example: $y=f(t,\mathbf x)=x_1+x_2\exp(tx_3)$ fit to 5 data points; from a
starting guess, Gauss–Newton converges after 13 iterations to
$x_1^*\approx523.306,\ x_2^*\approx-156.948,\ x_3^*\approx-0.199665$.

## Chapter 19 — Integral Calculus of Several Variables (start)

### 19.1 Domain integrals (Bereichsintegrale)

**Goal:** compute the volume under the graph of $f:D\to\mathbb R$,
$D\subset\mathbb R^n$: $V=\int_D f(x)\,dx$, generalizing the 1D Riemann integral
$I=\int_a^bf(x)\,dx$ (defined via the common limit of Riemann upper/lower sums).
*(Chapter continues in the next source with the precise construction, Fubini's
theorem, and the transformation/substitution theorem for multiple integrals.)*

---

## Notes for the wiki

- This is the first Analysis 3 source — new module, substantial new content
  across multivariable differential calculus and its applications.
- Hand-annotated highlights (yellow/green marker, underlines) in the scanned
  slides were used only to identify emphasis; no separate handwritten content
  beyond the typed slides was present on these pages.
- New concept pages created: [[partial-derivatives-and-gradient]],
  [[vector-calculus-operators]], [[multivariable-chain-rule-and-jacobian]],
  [[multivariable-taylor-and-extrema]], [[implicit-function-theorem]],
  [[lagrange-multipliers]], [[multivariable-newton-method]].
- No contradictions with Analysis 1/2 material; this content builds directly on
  single-variable differentiability, Taylor's theorem, and fixed-point/Newton
  concepts already in the wiki.
