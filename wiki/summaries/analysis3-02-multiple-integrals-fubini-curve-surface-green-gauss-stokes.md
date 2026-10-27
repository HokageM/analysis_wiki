---
title: "Analysis 3 — Lecture Slides 2 (Ch. 19): Multiple Integrals, Fubini, Curve & Surface Integrals, Green/Gauss/Stokes"
module: analysis3
type: summary
sources: [raw/analysis3/analysis_3_2.pdf]
updated: 2026-10-25
---

# Overview

Source: *Analysis III*, Prof. Dr. Armin Iske, TUHH, WS 2019/2020, lecture slides
(4-up), 22 sheets, slides 122–206. Completes **Chapter 19: Integral Calculus of
Several Variables**, covering the entire remainder of the course syllabus
(multiple integrals, curve/surface integrals, and the integral theorems of
vector calculus: Green, Gauss, Stokes).

Related: [[multiple-integrals-and-fubini]], [[curve-and-surface-integrals]],
[[vector-calculus-integral-theorems]], [[curves-and-curve-integrals]],
[[vector-calculus-operators]].

---

## 19.1 Domain (region) integrals — construction

**Construction principle** (analogous to the 1D case, generalized): for a
rectangle/box domain $D=[a_1,b_1]\times[a_2,b_2]\subset\mathbb R^2$ and bounded
$f:D\to\mathbb R$: a **partition** $Z$ of $D$ via
$a_1=x_0<\dots<x_n=b_1$, $a_2=y_0<\dots<y_m=b_2$ gives sub-rectangles $Q_{ij}$
with volume $\mathrm{vol}(Q_{ij})$; **Riemann sum**
$R_f(Z):=\sum_{i,j}f(\xi_{ij})\mathrm{vol}(Q_{ij})$; **upper/lower sums**
$$U_f(Z):=\sum_{i,j}\inf_{x\in Q_{ij}}f(x)\,\mathrm{vol}(Q_{ij}), \qquad O_f(Z):=\sum_{i,j}\sup_{x\in Q_{ij}}f(x)\,\mathrm{vol}(Q_{ij}),$$
with $U_f(Z)\le R_f(Z)\le O_f(Z)$ for any Riemann sum of that partition.
Refining $Z_1\to Z_2$ (adding points): $U_f(Z_2)\ge U_f(Z_1)$,
$O_f(Z_2)\le O_f(Z_1)$ — monotone and bounded as $\|Z\|\to0$, so
$\underline I_f:=\sup_ZU_f(Z)$ (**lower integral**) and
$\overline I_f:=\inf_ZO_f(Z)$ (**upper integral**) exist. $f$ is
**Riemann-integrable** if $\underline I_f=\overline I_f =: \int_Df(x)\,dx$.
Generalizes to $n>2$ with analogous box/partition constructions
($\iint,\iiint,\dots$ notation for $n=2,3,\dots$).

**Elementary properties:** linearity, monotonicity ($f\le g\Rightarrow\int_Df\le\int_Dg$),
positivity ($f\ge0\Rightarrow\int_Df\ge0$). **Additivity over sub-boxes:** if
$D=D_1\cup D_2$, $\mathrm{vol}(D_1\cap D_2)=0$, $f$ integrable over each piece
$\Rightarrow$ integrable over $D$ with additive integrals. **Estimate:**
$|\int_Df\,dx|\le\sup_{x\in D}|f(x)|\cdot\mathrm{vol}(D)$. **Riemann criterion:**
$f$ integrable over $D$ iff $\forall\epsilon\,\exists Z: O_f(Z)-U_f(Z)<\epsilon$.

### Fubini's theorem

For $f:D\to\mathbb R$ integrable, $D=[a_1,b_1]\times[a_2,b_2]$ a box, if the
one-dimensional integrals $F(x):=\int_{a_2}^{b_2}f(x,y)\,dy$ and
$G(y):=\int_{a_1}^{b_1}f(x,y)\,dx$ exist for all $x,y$ respectively, then
$$\int_D f(\mathbf x)\,d\mathbf x = \int_{a_1}^{b_1}\int_{a_2}^{b_2}f(x,y)\,dy\,dx = \int_{a_2}^{b_2}\int_{a_1}^{b_1}f(x,y)\,dx\,dy.$$
**Significance:** reduces multi-dimensional integration to iterated 1D
integration. **Caution:** existence of the two iterated (1D) integrals alone does
**not** guarantee integrability of $f$ over $D$ — $f$'s integrability must be
established separately (e.g. via continuity). **Proof** via upper/lower-sum
estimates on each sub-rectangle, refining the partition in one variable at a
time, and summing.

**Measurability and null sets.** $\mathrm{vol}(D):=\int_D1\,dx=\int_Q\chi_D(x)\,dx$
(for $D$ compact, $\chi_D$ its characteristic/indicator function, extended by
zero to an enclosing box $Q\supset D$); $D$ is **measurable** if this integral
exists. $D$ is a **null set** if measurable with $\mathrm{vol}(D)=0$.

**Three key theorems:** (a) compact $D$ is measurable iff its boundary $\partial D$
is a null set; (b) $D$ compact and measurable, $f$ continuous $\Rightarrow f$
integrable over $D$; (c) **mean value theorem**: $D$ compact, connected,
measurable, $f$ continuous $\Rightarrow\exists\xi\in D: \int_Df(x)\,dx=f(\xi)\mathrm{vol}(D)$.

### Normal domains (Normalbereiche)

$D\subset\mathbb R^2$ is a **normal domain** if
$D=\{(x,y)\mid a\le x\le b,\ g(x)\le y\le h(x)\}$ for continuous $g,h$ (analogous
3D definition with a permutation of coordinates). **Theorem:** $f$ continuous on
a normal domain $D$ $\Rightarrow$
$$\int_D f(x,y)\,dx\,dy = \int_a^b\int_{g(x)}^{h(x)} f(x,y)\,dy\,dx$$
(proof via embedding $D$ in its enclosing box and applying Fubini). Generalizes
to **projectable sets** in higher dimensions: a set $D\subset\mathbb R^n$
projectable in direction $x_i$, giving
$\int_Df(\mathbf x)\,d\mathbf x = \int_B\left(\int_{\varphi(\tilde{\mathbf x})}^{\psi(\tilde{\mathbf x})}f(\mathbf x)\,dx_i\right)d\tilde{\mathbf x}$.
Any domain decomposable into finitely many normal domains is measurable.

**Worked examples:** volume of a paraboloid-of-revolution solid
$V=\{(x,y,z)\mid x^2+y^2\le1,\ x^2+y^2\le z\le1\}$, computed via a 2D normal
domain representation giving $\mathrm{vol}(V)=\pi/2$; volume of a pyramid
$P=\{(x,y,z)\mid\max(|y|,|z|)\le ax/(2h),\ 0\le x\le h\}$: $\mathrm{vol}(P)=\frac13a^2h$
(matches the general cone/pyramid volume formula); centroid of $P$ at
$(\frac34h,0,0)$.

### General integration domains and applications

General partitions $Z=\{D_1,\dots,D_m\}$ (compact, measurable, connected pieces
covering $D$, pairwise non-overlapping); **theorem:** Riemann sums over
arbitrarily fine general partitions converge to $\int_Df\,dx$ as $\|Z\|\to0$.

**Center of mass** of $D$ with density $\rho(x)$:
$$\mathbf x_s := \frac{\int_D\rho(x)x\,dx}{\int_D\rho(x)\,dx}$$
(computed componentwise). **Moment of inertia** about an axis $A$:
$$\Theta := \int_D\rho(x)r^2(x)\,dx \qquad (r(x)=\text{distance from }x\text{ to }A).$$
**Steiner's theorem (parallel axis theorem):** for total mass $m$,
$\Theta_A = md^2+\Theta_S$, where $\Theta_S$ is the moment about the parallel axis
through the centroid $\mathbf x_s$ and $d$ is the distance between the two axes
(proof via a shift $\mathbf x = \Phi(\mathbf u) = \mathbf x_s+\mathbf u$, using
$\int_D\mathbf u\,d\mathbf u=0$ at the centroid).

### The transformation (substitution) theorem

**Goal:** generalize the 1D substitution rule
$\int_{\varphi(a)}^{\varphi(b)}f(x)\,dx = \int_a^bf(\varphi(t))\varphi'(t)\,dt$.
**Theorem:** $\Phi:U\to\mathbb R^n$ a $C^1$-diffeomorphism, $U\subset\mathbb R^n$
open, $D\subset U$ compact measurable with $\Phi(D)$ also compact and measurable.
Then for continuous $f:\Phi(D)\to\mathbb R$:
$$\int_{\Phi(D)} f(\mathbf x)\,d\mathbf x = \int_D f(\Phi(\mathbf u))\,|\det J\Phi(\mathbf u)|\,d\mathbf u.$$
**Caution:** bijectivity of $\Phi$ is only required on the interior $D^0$, not
necessarily on the boundary $\partial D$ (e.g. polar coordinates at $r=0$).

**Worked examples:** centroid of a homogeneous octant of a ball via spherical
coordinates (Jacobian $\det J\Phi(r,\varphi,\psi)=r^2\cos\psi$), giving
$\mathrm{vol}(V)=\pi/6$ and $\mathbf x_s=(3/8,3/8,3/8)$; **the Gaussian integral**
$\int_{-\infty}^\infty e^{-x^2}dx=\sqrt\pi/2$ computed by squaring, converting to a
2D integral, and passing to polar coordinates (sandwiching between inscribed and
circumscribed quarter-disks $K_\rho,K_{R},K_{\sqrt2R}$), i.e.
$$I^2 = \left(\int_0^\infty e^{-x^2}dx\right)^2 = \lim_{R\to\infty}\iint_{[0,R]^2}e^{-(x^2+y^2)}\,dx\,dy = \lim_{R\to\infty}\int_0^{\pi/2}\int_0^Re^{-r^2}r\,dr\,d\varphi = \frac\pi4,$$
hence $\int_0^\infty e^{-x^2}dx=\sqrt\pi/2$.

## 19.2 Curve integrals (recap + extension to "second kind")

**Curve integral of the 1st kind** (recap, matches [[curves-and-curve-integrals]]):
$\int_cf(x)\,ds = \int_a^bf(c(t))\|\dot c(t)\|\,dt$.

**Curve integral of the 2nd kind** (new): for a continuous vector field
$\mathbf f:D\to\mathbb R^n$ and piecewise-$C^1$ curve $c:[a,b]\to D$:
$$\int_c \mathbf f(\mathbf x)\,d\mathbf x := \int_a^b \langle \mathbf f(c(t)),\dot c(t)\rangle\,dt$$
(physical motivation: work done by a force field $\mathbf f$ along path $c$;
derived as the limit of Riemann-sum approximations
$A\approx\sum_i\langle f(c(t_i)),c(t_{i+1})-c(t_i)\rangle$ over polygon
approximations of $c$, mirroring the construction of the 1st-kind integral).
Closed-curve notation $\oint_c\mathbf f\,d\mathbf x$.

**Properties:** (a) linearity; (b) orientation reversal:
$\int_{-c}\mathbf f\,d\mathbf x = -\int_c\mathbf f\,d\mathbf x$; (c) additivity
over concatenated paths $c_1+c_2$; (d) **parametrization-invariant**; (e)
relation to the 1st-kind integral via the unit tangent $\mathbf T(t)=\dot c(t)/\|\dot c(t)\|$:
$\int_c\mathbf f\,d\mathbf x = \int_c\langle\mathbf f,\mathbf T\rangle\,ds$; (f)
componentwise notation $\int_c\mathbf f\,d\mathbf x = \sum_i\int_cf_i(x)\,dx_i$.

**Circulation.** For a velocity field $\mathbf u(x)$ of a flowing medium, the
**circulation** along a closed curve $c$ is $\oint_c\mathbf u(x)\,d\mathbf x$.
Worked example: $\mathbf u(x,y)=(y,1+\sin(t))^T$-style rotational field on the
unit circle gives circulation $=-\pi r^2$ (nonzero — field is "rotating").

**Wirbelfrei (curl-free/irrotational) vector fields:** $\mathbf f$ is curl-free if
$\oint_c\mathbf f\,d\mathbf x=0$ for **every** closed piecewise-$C^1$ curve $c$ in
$D$ — equivalently, line-integral **path-independence** (value depends only on
endpoints, not the path taken). Worked counterexample field
$\mathbf f(x,y)=\frac1{x^2+y^2}(-y,x)^T$ on $D=\mathbb R^2\setminus\{0\}$: although
$\mathrm{rot}\,\mathbf f=0$ pointwise, the circulation around the unit circle is
$2\pi\ne0$ — **this field is NOT curl-free in the path-independence sense**,
because its domain $D$ has a "hole" (is **not simply connected**). Key open
question raised by the lecture: "which criteria guarantee path-independence of
the line integral?" — answered by the next theorems.

## Gradient fields, potentials, and conservative fields

A vector field $\mathbf f=\nabla\varphi$ (for scalar $C^1$-function $\varphi$) is
a **gradient field**; $\varphi$ is its **potential/Stammfunktion**, and
$\mathbf f$ is **conservative**. Physical interpretation: a mass moving in a
conservative force field $\mathbf K(x)=-\nabla U(x)$ (potential energy $U$)
satisfies energy conservation
$\frac{d}{dt}\left(\frac12m\|\dot x\|^2+U(x)\right)=0$.

**Fundamental theorem for curve integrals.** $D\subset\mathbb R^n$ a domain
("Gebiet" — open and connected), $\mathbf f$ continuous vector field on $D$:
(a) If $\mathbf f$ has a potential $\varphi$, then for every piecewise-$C^1$
curve $c:[a,b]\to D$: $\int_c\mathbf f\,d\mathbf x=\varphi(c(b))-\varphi(c(a))$ —
in particular the line integral is **path-independent** and $\mathbf f$ is
curl-free. (b) Conversely, if $\mathbf f$ is curl-free (path-independent), it has
a potential, given explicitly (up to a constant) by
$\varphi(\mathbf x) = \int_{c_{\mathbf x}}\mathbf f\,d\mathbf x$ for any fixed
base point and any path $c_{\mathbf x}$ from it to $\mathbf x$.

**Worked examples:** central force field $\mathbf K(x)=\mathbf x/\|\mathbf x\|^3$
has potential $U(x)=-1/\|\mathbf x\|$; general field
$\mathbf f(x,y,z)=(2xy+z^3, x^2+3z, 3xz^2+3y)$ has potential
$\varphi(x,y,z)=x^2y+xz^3+3yz$, used to compute work along a curve from $P$ to
$Q$ as $\varphi(Q)-\varphi(P)$ directly (no need to parametrize/integrate the curve).

### Conditions for a potential to exist

**Necessary condition:** $\mathbf f=\nabla\varphi \Rightarrow \mathrm{rot}(\mathbf f)=\mathrm{rot}(\nabla\varphi)=\mathbf 0$
(matches [[vector-calculus-operators]]); even in 2D the analogous scalar
condition $\mathrm{rot}(f(x,y)):=\partial_xf_2-\partial_yf_1=0$ is necessary.
**This is NOT sufficient in general** — only sufficient if $D$ is additionally
**simply connected** ("einfach zusammenhängend", i.e. contains no "holes" —
formally: every closed curve in $D$ can be continuously contracted to a point
within $D$, i.e. is **null-homotopic**).

**Integrability condition:** $\mathbf f:D\to\mathbb R^n$ has a potential on $D$
iff $Jf(\mathbf x)=(Jf(\mathbf x))^T$ for all $\mathbf x\in D$ (symmetric Jacobian,
i.e. $\partial f_k/\partial x_j=\partial f_j/\partial x_k$ for all $j,k$) — which
for $n=2,3$ coincides with $\mathrm{rot}(\mathbf f)=\mathbf 0$. **Construction of
the potential:** integrate $f_1$ w.r.t. $x_1$ (introducing an unknown function of
the remaining variables), then match against $f_2$ to pin down that unknown
function, and so on recursively.

## Green's theorem (2D)

**Green's (integral) theorem.** $\mathbf f:D\to\mathbb R^2$ a $C^1$-vector field,
$D\subset\mathbb R^2$ a domain, $K\subset D$ compact with boundary $\partial K$ a
closed, stückweise-$C^1$ curve, parametrized so that $K$ stays to the left of the
direction of travel ("Durchlaufrichtung"). Then:
$$\oint_{\partial K}\mathbf f(\mathbf x)\,d\mathbf x = \int_K\mathrm{rot}(\mathbf f(\mathbf x))\,d\mathbf x.$$
**Interpretation:** relates a circulation (boundary curve integral) to a domain
integral of the (2D scalar) curl — foundational for Green's formulas and (in
$\mathbb R^3$) the divergence/Gauss and Stokes theorems. **Caution** (alternative
formulation): with the outward unit normal
$\mathbf n:=\mathbf T_2,-\mathbf T_1)$ (90° rotation of the tangent),
$\oint_{\partial K}\langle\mathbf f,\mathbf n\rangle\,ds = \int_K\mathrm{div}(\mathbf f)\,d\mathbf x$
— **this is the 2D special case of the divergence/Gauss theorem.** Physical
reading: if $\mathbf f$ is a fluid velocity field, $\mathrm{div}(\mathbf f)=0$
("source-free"/"solenoidal") means the total flux through any closed curve $K$
vanishes — conservation of mass/incompressible flow.

### Simply connected domains and path-independence (revisited)

**Theorem:** on a **simply connected** domain $D\subset\mathbb R^n$, curl-free
($\mathrm{rot}(\mathbf f)=\mathbf 0$) $\Rightarrow \oint_c\mathbf f\,d\mathbf x=0$
for every closed piecewise-$C^1$ curve $c$ in $D$ — i.e. the earlier necessary
condition becomes sufficient once the domain has no "holes" (this resolves the
open question from the counterexample above: $\mathbb R^2\setminus\{0\}$ is
**not** simply connected, which is exactly why that curl-free field still had
nonzero circulation). Formal def. of simply connected: every closed curve
$c:[a,b]\to D$ can be continuously deformed (a **homotopy**
$\Phi:[a,b]\times[0,1]\to D$) to a constant curve within $D$.

## 19.3 Surface integrals

A $C^1$ map $\mathbf p:D\to\mathbb R^3$ ($D\subset\mathbb R^2$ open) with linearly
independent partials $\partial\mathbf p/\partial u_1,\partial\mathbf p/\partial u_2$
everywhere parametrizes a **surface** $F:=\{\mathbf p(\mathbf u):\mathbf u\in D\}$
(examples: cylinder, graph of a scalar function $\varphi(u_1,u_2)$). These
partials span the **tangent plane**
$T_{\mathbf x^0}(F): \mathbf x = \mathbf x^0+\lambda\partial_{u_1}\mathbf p(\mathbf u^0)+\mu\partial_{u_2}\mathbf p(\mathbf u^0)$.

**Surface area / surface element:**
$$O(\mathbf p(K)) := \int_K \left\|\frac{\partial\mathbf p}{\partial u_1}\times\frac{\partial\mathbf p}{\partial u_2}\right\|\,d\mathbf u, \qquad do := \left\|\frac{\partial\mathbf p}{\partial u_1}\times\frac{\partial\mathbf p}{\partial u_2}\right\|d\mathbf u \ (\text{"surface element"}),$$
independent of parametrization (follows from the transformation theorem). For a
function graph $x_3=\varphi(x_1,x_2)$: $do = \sqrt{1+\varphi_{x_1}^2+\varphi_{x_2}^2}\,d(x_1,x_2)$.
**First fundamental form (E,F,G):** $E:=\|\partial_{u_1}\mathbf p\|^2$,
$F:=\langle\partial_{u_1}\mathbf p,\partial_{u_2}\mathbf p\rangle$,
$G:=\|\partial_{u_2}\mathbf p\|^2$: using the Lagrange/Cauchy–Schwarz identity
$\|a\times b\|^2 = \|a\|^2\|b\|^2-\langle a,b\rangle^2$,
$do=\sqrt{EG-F^2}\,d(u_1,u_2)$. Worked example (sphere, spherical-coordinate
parametrization): $E=r^2\cos^2\theta$, $F=0$, $G=r^2 \Rightarrow do=r^2\cos\theta\,d(\varphi,\theta)$,
yielding the total sphere area $O=4\pi r^2$.

**Surface integral of the 1st kind** (scalar $f:F\to\mathbb R$):
$$\int_F f(\mathbf x)\,do := \int_K f(\mathbf p(\mathbf u))\left\|\partial_{u_1}\mathbf p\times\partial_{u_2}\mathbf p\right\|\,d\mathbf u.$$
**Surface integral of the 2nd kind** (vector field $\mathbf f:F\to\mathbb R^3$):
$$\int_F \mathbf f(\mathbf x)\,d\mathbf x := \int_K \left\langle\mathbf f(\mathbf p(\mathbf u)),\ \partial_{u_1}\mathbf p\times\partial_{u_2}\mathbf p\right\rangle\,d\mathbf u.$$
**Alternative form via the unit normal**
$\mathbf n(\mathbf x) := \mathbf n(\mathbf p(\mathbf u)) := \dfrac{\partial_{u_1}\mathbf p\times\partial_{u_2}\mathbf p}{\|\partial_{u_1}\mathbf p\times\partial_{u_2}\mathbf p\|}$:
$\int_F\mathbf f\,d\mathbf x = \int_F\langle\mathbf f,\mathbf n\rangle\,do$ — must
choose the parametrization so that $\mathbf n(\mathbf x)$ is the **outward**
normal when $F$ is a closed surface (boundary of a solid), matching the notation
$\oint_F\mathbf f\,do$ for closed surfaces.

**Physical interpretations:** $\rho(x)$ a mass density on $F\Rightarrow\int_F\rho\,do$
is total mass; $\mathbf f$ a fluid velocity field $\Rightarrow\int_F\mathbf f\,d\mathbf x$
is the volumetric **flux** through $F$ per unit time.

## Gauss's divergence theorem

**Integral theorem of Gauss.** $G\subset\mathbb R^3$ compact w.r.t. coordinate
directions, with $\partial G$ parametrizable by finitely many smooth surface
pieces with outward unit normal $\mathbf n(\mathbf x)$; $\mathbf f:D\to\mathbb R^3$
a $C^1$ vector field on $D\supset G$. Then:
$$\int_G \mathrm{div}(\mathbf f(\mathbf x))\,d\mathbf x = \oint_{\partial G} \mathbf f(\mathbf x)\,do.$$
**Interpretation:** total "source strength" ($\mathrm{div}\,\mathbf f$) inside $G$
equals the net flux of $\mathbf f$ through the boundary $\partial G$. A flow
field $\mathbf f$ is **incompressible** if $\mathrm{div}(\mathbf f)=0$ — then the
flux through any closed surface in the domain vanishes.

**Worked example:** $\mathbf f(\mathbf x)=\mathbf x$ on the unit ball
$K=\{\|\mathbf x\|\le1\}$: $\mathrm{div}\,\mathbf f=3 \Rightarrow \int_K\mathrm{div}(\mathbf f)\,d\mathbf x=3\,\mathrm{vol}(K)=4\pi$,
giving a shortcut to compute $\oint_{\partial K}\mathbf f\,do=4\pi$ **without**
explicit surface-integral parametrization in spherical coordinates.

### Green's formulas (from Gauss's theorem)

Setting $\mathbf F(\mathbf x):=f(\mathbf x)\nabla g(\mathbf x)$ in Gauss's theorem
and using $\mathrm{div}(f\nabla g)=f\Delta g+\langle\nabla f,\nabla g\rangle$
gives, for $C^2$ functions $f,g:D\to\mathbb R$, $G\subset D$ as above:
$$\int_G(f\Delta g+\langle\nabla f,\nabla g\rangle)\,d\mathbf x = \oint_{\partial G}f\frac{\partial g}{\partial\mathbf n}\,do \quad \text{(1st Green formula)},$$
$$\int_G(f\Delta g-g\Delta f)\,d\mathbf x = \oint_{\partial G}\left(f\frac{\partial g}{\partial\mathbf n}-g\frac{\partial f}{\partial\mathbf n}\right)do \quad \text{(2nd Green formula, by subtracting the swapped version)},$$
where $\partial f/\partial\mathbf n := D_{\mathbf n}f$ is the directional
derivative along the outward normal.

## Stokes' theorem

**Integral theorem of Stokes.** $\mathbf f:D\to\mathbb R^3$ a $C^1$ vector field
on a domain $D\subset\mathbb R^3$; $F=\mathbf p(K)$ a parametrized surface in
$D$, $K\subset\mathbb R^2$ a Green region (i.e. Green's theorem applies on it)
with boundary $\partial K$ parametrized by a piecewise-smooth closed curve;
$\partial F := \mathbf p(\partial K)$ the induced boundary curve on $F$, oriented
so that $\mathbf n(c(t))\times\dot c(t)$ points into $F$. Then:
$$\int_F \mathrm{rot}(\mathbf f(\mathbf x))\,do = \oint_{\partial F=c} \mathbf f(\mathbf x)\,d\mathbf x.$$
(Proof: convert the surface integral of $\mathrm{rot}\,\mathbf f$ to a domain
integral over $K$ via the surface-integral definition, then apply Green's theorem
on $K$ to turn it into the curve integral over $\partial K$, which maps to
$\partial F$ under $\mathbf p$.)

**Worked example:** $\mathbf f(x,y,z)=(-y,x,-z)$, $F$ = upper hemisphere of the
unit sphere (parametrized via $\varphi\in[0,2\pi],\psi\in[0,\pi/2]$), boundary
curve $c(t)=(\cos t,\sin t,0)$: directly computing
$\oint_c\mathbf f\,d\mathbf x = \int_0^{2\pi}(\sin^2t+\cos^2t)\,dt=2\pi$ matches
the surface-integral computation
$\int_F\mathrm{rot}(\mathbf f)\,do = \int_0^{\pi/2}\int_0^{2\pi}2\sin(\psi)\cos(\psi)\,d\varphi\,d\psi = 2\pi\int_0^{\pi/2}\sin(2\psi)\,d\psi=2\pi$ —
**confirming Stokes' theorem numerically** on a concrete example.

---

## Notes for the wiki

- This source completes the Analysis 3 course content per the original
  syllabus (through "Stokes' formulas / Stokes' theorem").
- New concept/theorem pages created: [[multiple-integrals-and-fubini]],
  [[curve-and-surface-integrals]], [[vector-calculus-integral-theorems]].
- No contradictions with prior material; directly builds on
  [[curves-and-curve-integrals]] (1st-kind curve integrals, Analysis 2) and
  [[vector-calculus-operators]] (div/curl, Analysis 3 part 1).
- Course completeness check: all topics from the Analysis 2/3 syllabi referenced
  in earlier summaries are now covered **except** the still-missing Chapter 9
  (Interpolation) gap noted in `wiki/index.md` (partially filled by handwritten
  notes) — otherwise the wiki's lecture-derived coverage is complete through the
  end of Analysis 3.
