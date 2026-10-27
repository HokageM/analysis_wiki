---
title: "Analysis 1 — Lecture Slides 1 (Ch. 1–3): Logic, Sets, Functions, Number Systems, Sequences & Series"
module: analysis1
type: summary
sources: [raw/analysis1/analysis_1_1.pdf]
updated: 2026-10-25
---

# Overview

Source: *Analysis I für Studierende der Ingenieurwissenschaften*, Prof. Dr. Armin Iske,
Technische Universität Hamburg (TUHH), Winter semester 2018/2019. Lecture slides,
4-up printout, 32 sheets (124 slides). Covers Chapters 1–3 of the course: propositional
logic & sets, functions, number systems (ℕ, ℤ, ℚ, ℝ), and convergence of sequences and series.

Related pages: [[logic-and-sets]], [[functions]], [[real-numbers-and-axioms]],
[[sequences-and-convergence]], [[series-and-convergence-tests]],
[[bolzano-weierstrass-theorem]], [[cauchy-convergence-criterion]].

---

## Chapter 1 — Statements, Sets, Functions (Aussagen, Mengen, Funktionen)

### 1.1 Statements (propositional logic)

A **statement (proposition)** is a linguistic construction for which one can
decide unambiguously whether it is TRUE or FALSE. Truth value notation:
$$w(A) = 0 \iff A \text{ is false}, \qquad w(A) = 1 \iff A \text{ is true}.$$

Connectives of statements $A, B$: negation $\neg A$ ("not $A$"), conjunction
$A \wedge B$ ("$A$ and $B$"), disjunction $A \vee B$ ("$A$ or $B$"), implication
$A \Rightarrow B$ ("$A$ implies $B$"), equivalence $A \Leftrightarrow B$.

A **tautology** is a compound statement that is true for every combination of
truth values of its components; a **contradiction** is one that is always false.
Example tautology, proved via truth table:
$$(A \Rightarrow B) \Leftrightarrow (\neg B \Rightarrow \neg A).$$

Frequently used tautologies: excluded middle $A \vee \neg A$, non-contradiction
$\neg(A \wedge \neg A)$, double negation $\neg\neg A \Leftrightarrow A$, De Morgan's
laws $\neg(A \wedge B) \Leftrightarrow \neg A \vee \neg B$ and
$\neg(A \vee B) \Leftrightarrow \neg A \wedge \neg B$, contraposition
$(A \Rightarrow B) \Leftrightarrow (\neg B \Rightarrow \neg A)$, modus ponens, modus
tollens, modus barbara (syllogism), and the distributive laws of $\wedge$ over $\vee$
and vice versa.

A **statement form (Aussageform)** is a statement depending on free variables,
e.g. $A(x,y) :\Leftrightarrow x^2 + y^2 < 2$. Quantifiers: $\forall$ (universal),
$\exists$ (existential), $\exists_1$ (unique existence). Negation of quantifiers:
$$\neg(\forall x: A(x)) \Leftrightarrow \exists x: \neg A(x), \qquad
\neg(\exists x: A(x)) \Leftrightarrow \forall x: \neg A(x).$$

**Proof techniques.** Standard form of a theorem: $A \Rightarrow B$, where $A$ is the
premise and $B$ the conclusion.
- **Direct proof (chain of implications):** $A = A_0 \Rightarrow A_1 \Rightarrow \dots \Rightarrow A_n = B$.
- **Indirect proof (contraposition / contradiction):** $A \Rightarrow B$ is equivalent to $\neg B \Rightarrow \neg A$.

Worked example (direct + indirect): for $n \in \mathbb{N}$, "$n$ is even $\iff n^2$ is even."
- Direct: $n = 2k \Rightarrow n^2 = 4k^2 = 2(2k^2) \Rightarrow n^2$ even.
- Indirect (proves $n^2$ even $\Rightarrow n$ even, by showing $\neg(n \text{ even}) \Rightarrow \neg(n^2\text{ even})$): assume $n$ odd, $n = 2k-1 \Rightarrow n^2 = 4k^2-4k+1 = 2(2k^2-2k)+1 \Rightarrow n^2$ odd — a contradiction.

Worked example (proof by contradiction): **$\sqrt{2}$ is irrational.** Assume
$\sqrt 2 = n/m$ with $n,m\in\mathbb N$ coprime. Then $2m^2 = n^2 \Rightarrow n$ even
$\Rightarrow n = 2k \Rightarrow 2m^2 = 4k^2 \Rightarrow m^2 = 2k^2 \Rightarrow m$ even —
contradicting coprimality. Hence no such $n,m$ exist.

### 1.2 Sets (Mengen)

A **set** is a collection of pairwise distinct objects (its *elements*). Notation:
$a \in M$ ("$a$ is an element of $M$"), $a\notin M :\Leftrightarrow \neg(a\in M)$.
Examples: $\mathbb N=\{1,2,3,\dots\}$, $\mathbb N_0=\{0,1,2,\dots\}$.

A set can be defined by **enumeration** ($M := \{1,2,3,4\}$) or by a
**characteristic property**: $M := \{x\in\Omega \mid A(x)\}$ for a statement form
$A(x)$ over a universe $\Omega$. The **empty set** $\emptyset$ contains no elements.

Subset / equality:
$$M \subset N :\Leftrightarrow \forall x: (x\in M \Rightarrow x\in N), \qquad
M = N :\Leftrightarrow \forall x: (x \in M \Leftrightarrow x\in N).$$

Order properties: $M\subset M$; $(M\subset N)\wedge(N\subset M) \Rightarrow M=N$;
$(M\subset N)\wedge(N\subset P)\Rightarrow M\subset P$ (transitivity).

Set operations: union $M\cup N$, intersection $M\cap N$, difference $M\setminus N$,
Cartesian product $M\times N := \{(a,b)\mid a\in M \wedge b\in N\}$, power set
$\mathcal P(M) := \{X \mid X\subset M\}$ (all subsets of $M$).

$M,N$ are **disjoint** if $M\cap N=\emptyset$. For finitely many sets:
$$\bigcup_{k=1}^n A_k := A_1\cup\dots\cup A_n, \quad \bigcap_{k=1}^n A_k := A_1\cap\dots\cap A_n, \quad \prod_{k=1}^n A_k := A_1\times\dots\times A_n.$$

Ordered tuples: $(a_1,a_2)=(b_1,b_2) \iff a_1=b_1 \wedge a_2=b_2$ (analogous for
$n$-tuples). Important Cartesian products: Euclidean plane
$\mathbb R^2 := \mathbb R\times\mathbb R$, 3-space $\mathbb R^3$, and
$\mathbb R^n := \underbrace{\mathbb R\times\cdots\times\mathbb R}_{n\text{-fold}}$.

**Intervals in $\mathbb R$** for $a<b$: closed $[a,b]=\{x\mid a\le x\le b\}$,
open $(a,b)=\{x\mid a<x<b\}$, half-open $[a,b)=\{x\mid a\le x<b\}$ and
$(a,b]=\{x\mid a<x\le b\}$.

### 1.3 Functions (Funktionen)

A **function** $f: M \to N$ assigns to every $x\in M$ exactly one $y\in N$,
written $y=f(x)$. Equivalently $f: M\to N \iff \forall x\in M\,\exists! y\in N: y=f(x)$.
$M$ is the **domain**, $N$ the **codomain**, and
$\mathrm{graph}(f) = \{(x,f(x)) \mid x\in M\} \subset M\times N$ the graph.

For $A\subset M$: the **image** $f(A) := \{f(a)\mid a\in A\}\subset N$.
For $B\subset N$: the **preimage** $f^{-1}(B) := \{a\in M \mid f(a)\in B\}\subset M$.

**Surjective / injective / bijective.** $f$ is:
- *surjective* iff $\forall y\in N\,\exists x\in M: y=f(x)$;
- *injective* iff $\forall x_1,x_2\in M: f(x_1)=f(x_2) \Rightarrow x_1=x_2$;
- *bijective* iff injective and surjective.

An injective $f:M\to N$ has an **inverse function** $f^{-1}: f(M)\to M$ with
$f^{-1}(y)=x$ for $y=f(x)$. If $f$ is bijective, $f(M)=N$ and $f^{-1}(N)=M$, i.e.
$M \xrightarrow{f} N$ and $N \xrightarrow{f^{-1}} M$. The graph of $f^{-1}$ is the
reflection of the graph of $f$ across the diagonal $y=x$.

**Composition.** For $f:M\to N$, $g:N\to P$: $(g\circ f)(x) := g(f(x))$. Associative:
$h\circ(g\circ f) = (h\circ g)\circ f$, but **not** commutative in general
(counterexample: $f(x)=x^2+2x$, $g(x)=x+1 \Rightarrow g\circ f \ne f\circ g$).

**The symmetric group.** For a nonempty set $M$, $S(M) := \{f: M\to M \mid f \text{ bijective}\}$
satisfies the group axioms (G1) associativity, (G2) identity $\mathrm{id}_M$, (G3)
inverses $f\circ f^{-1}=f^{-1}\circ f=\mathrm{id}_M$.

**Elementary real functions** introduced: affine-linear $f(x)=a_1x+a_0$; polynomials
$f(x)=a_nx^n+\dots+a_0$ ($a_n\ne0$); the exponential function
$f(x)=\exp(x)=e^x$ with Euler's number $e=\sum_{n=0}^\infty \frac{1}{n!}=2.71828\ldots$
and functional equation $a^{x+y}=a^x\cdot a^y$; the logarithm $\log_a: (0,\infty)\to\mathbb R$
(inverse of $a^x$), natural logarithm $\log=\log_e$, with $\log_a(xy)=\log_a x + \log_a y$;
and the trigonometric functions $\sin,\cos:[0,2\pi]\to[-1,1]$, satisfying
$\sin^2\varphi+\cos^2\varphi=1$, odd/even symmetry $\sin(-\varphi)=-\sin\varphi$,
$\cos(-\varphi)=\cos\varphi$, periodicity with period $2\pi$, and the addition theorems
$\cos(\alpha+\beta)=\cos\alpha\cos\beta-\sin\alpha\sin\beta$,
$\sin(\alpha+\beta)=\sin\alpha\cos\beta+\cos\alpha\sin\beta$.

---

## Chapter 2 — Number Systems (Zahlenbereiche)

### 2.1 Natural numbers & combinatorics

$\mathbb N=\{1,2,3,\dots\}$ is defined formally via the **Peano axioms**: (A1)
$1\in\mathbb N$; (A2) $n\in\mathbb N\Rightarrow n+1\in\mathbb N$; (A3)
$n\ne m \Rightarrow n+1\ne m+1$; (A4) $n+1\ne1$ for all $n$; (A5) completeness
(induction) axiom: $(1\in A)\wedge(\forall n: n\in A\Rightarrow n+1\in A) \Rightarrow A=\mathbb N$.

**Proof by complete induction** — pseudocode of the structure:
```
To prove: ∀n ∈ ℕ: A(n)
(I1) Base case:        show A(1)
(I2) Induction hypothesis: assume A(n) holds
(I3) Induction step:   show A(n) ⇒ A(n+1)
If (I1)-(I3) succeed, then A(n) holds for all n ∈ ℕ.
```

Worked induction examples:
- Number of subsets of an $n$-element set: $|\mathcal P(A_n)| = 2^n$.
- Number of permutations of an $n$-tuple: $p_n = n!$.
- **Binomial coefficients** $\binom{n}{m} := \dfrac{n!}{m!(n-m)!}$ for $0\le m\le n$, $0!:=1$.
  Recursion (Pascal's rule): $\binom{n+1}{m} = \binom{n}{m}+\binom{n}{m-1}$, with
  $\binom{n}{0}=\binom{n}{n}=1$. **Binomial theorem**:
  $$(a+b)^n = \sum_{k=0}^n \binom{n}{k}a^k b^{n-k}.$$
  Pascal's triangle gives the recursive computation. Direct formula:
  $\binom{n}{m} = \prod_{k=1}^m \frac{n-k+1}{k}$. Example: lottery "6 aus 49" has
  $\binom{49}{6}=13\,983\,816$ combinations.

General sums/products, with empty-sum/product conventions:
$$\sum_{k=m}^n b_k := b_m+\dots+b_n \ (0 \text{ if } m>n), \qquad
\prod_{k=m}^n b_k := b_m\cdots b_n \ (1 \text{ if } m>n).$$

### 2.2 Prime numbers

$m \mid n$ ("$m$ divides $n$") iff $\exists k\in\mathbb N: n=k\cdot m$. $n>1$ with no
divisor other than $1,n$ is **prime**; there are infinitely many primes.

**Fundamental theorem of arithmetic:** every $n\in\mathbb N$ factors uniquely (up to
order) as $n = p_1^{r_1}\cdots p_k^{r_k}$ for primes $p_i$ and $r_i\ge1$.

$\gcd(n,m) := \max\{k \mid k\mid n \wedge k\mid m\}$, $\mathrm{lcm}(n,m) := \min\{k\mid n\mid k \wedge m\mid k\}$.
Via prime factorizations, $\gcd$ uses $\min$ of exponents and $\mathrm{lcm}$ uses $\max$.
Identity: $n\cdot m = \gcd(n,m)\cdot\mathrm{lcm}(n,m)$.

**Euclidean algorithm** for computing $\gcd(n,m)$ ($n\ge m$):
```
INPUT: n, m ∈ ℕ with n ≥ m
r0 := n;  r1 := m;  j := 1
REPEAT
    r(j-1) = q_j * r_j + r(j+1),  with 0 ≤ r(j+1) < r_j
    j := j + 1
UNTIL r(j+1) = 0
OUTPUT: r_j = gcd(n, m)
```
Worked example: $\gcd(3054,1002)=6$, and back-substitution gives the
**Bézout / $\mathbb{Z}$-combination**: $6 = 21\cdot3054 - 64\cdot1002$.

### 2.3 Real numbers

Extending $\mathbb N$: integers $\mathbb Z := -\mathbb N\cup\{0\}\cup\mathbb N$;
rationals $\mathbb Q := \{m/n \mid m\in\mathbb Z, n\in\mathbb N\}$. Note
$\sqrt2\notin\mathbb Q$, but $\sqrt2$ can be approximated arbitrarily well by
rationals ($\forall\epsilon>0\,\exists q\in\mathbb Q: |\sqrt2-q|<\epsilon$) — this
motivates defining $\mathbb R$.

**Axioms for $\mathbb R$:**
- (I) Addition is an abelian group: associativity, commutativity, neutral element 0, inverses $-x$.
- (II) Multiplication: associativity, commutativity, neutral element 1, inverses $1/x$ ($x\ne0$).
- (III) Distributive law.
- (IV) Order axioms: totality, reflexivity, antisymmetry, transitivity, compatibility with $+$ and $\cdot$ (for $z \ge 0$).
- (V) **Completeness (Dedekind, 1872):** for any partition $\mathbb R = L\cup R$ into
  nonempty sets with $\forall x\in L, y\in R: x<y$, there exists a unique cut number
  $s\in\mathbb R$ with $\forall x\in L,y\in R: x\le s\le y$.

A nonempty set with (I) is an abelian group; with (I)–(III) a *field*; a field with
(IV) an *ordered field*. $\mathbb Q$ is an ordered field but **not** complete — e.g.
$L=\{x\in\mathbb Q\mid x^2<2 \vee x<0\}$, $R=\{x\in\mathbb Q\mid x^2>2\wedge x>0\}$ has no
cut number in $\mathbb Q$ (it would have to be $\sqrt2\notin\mathbb Q$).

Rules for inequalities/absolute values (derivable from (IV)): e.g.
$x\le y \Rightarrow -x\ge -y$; $x\le y \wedge z\le 0 \Rightarrow xz \ge yz$; $x^2\ge0$;
monotonicity of $+$ and $\cdot$ for non-negative factors.

**Absolute value** $|a| := a$ if $a\ge0$, else $-a$; $|a-b|$ is the distance between
$a,b$. Properties: $|a|\ge0$; $|a|=0\iff a=0$; $|ab|=|a||b|$; **triangle inequality**
$|a+b|\le|a|+|b|$. $\epsilon$-neighborhood: $U_\epsilon(a) := \{x\in\mathbb R\mid|x-a|<\epsilon\}=(a-\epsilon,a+\epsilon)$.

**Supremum / infimum.** For $M\subset\mathbb R$: $x$ is an *upper (lower) bound* if
$\forall w\in M: w\le x$ (resp. $w\ge x$). $M$ is bounded above/below if such a
bound exists. $s$ is the **supremum** (resp. **infimum**) if it is the least upper
(resp. greatest lower) bound. Theorem: every nonempty bounded-above (bounded-below)
$M\subset\mathbb R$ has a supremum (infimum) — a consequence of completeness (V).
Corollaries: $\mathbb N$ is unbounded above (Archimedean property:
$x>0\Rightarrow\exists n\in\mathbb N: 0<1/n<x$); between any two reals $x<y$ there
are infinitely many rationals.

---

## Chapter 3 — Convergence of Sequences and Series (Konvergenz von Folgen und Reihen)

### 3.1 Normed vector spaces

A **norm** on a vector space $V$ over $\mathbb R$ is $\|\cdot\|: V\to[0,\infty)$ with
(N1) definiteness $\|v\|=0\iff v=0$; (N2) homogeneity $\|\lambda v\|=|\lambda|\|v\|$;
(N3) triangle inequality $\|v+w\|\le\|v\|+\|w\|$. $(V,\|\cdot\|)$ is a **normed
vector space**.

Examples: $(\mathbb R, |\cdot|)$; on $\mathbb R^n$ the **$p$-norm**
$\|x\|_p = \left(\sum_{j=1}^n|x_j|^p\right)^{1/p}$ ($p\ge1$), with Euclidean norm
at $p=2$ and **maximum norm** $\|x\|_\infty = \max_{1\le j\le n}|x_j|$ (as $p\to\infty$);
on function spaces $C[a,b]$, analogously
$\|f\|_p = \left(\int_a^b|f(x)|^p\,dx\right)^{1/p}$ and $\|f\|_\infty=\max_{a\le x\le b}|f(x)|$.

### 3.2 Sequences

A **sequence** in normed space $V$ is a map $\mathbb N\to V$, $n\mapsto a_n$, written
$(a_n)_{n\in\mathbb N}$. Examples: real sequences ($a_n=1/n$), complex ($a_n=i^n$),
vector sequences in $\mathbb R^n$, function sequences in $C[a,b]$ (e.g. $f(x)=x^n$).

Addition/scalar multiplication of sequences is componentwise. Sequences can be
defined **recursively**: $a_{n+1} := \Phi(n,a_n)$ for an iteration map $\Phi$.

**Bisection method** for a root of continuous $f:[a,b]\to\mathbb R$ with $f(a)f(b)<0$:
```
u0 := a; v0 := b
FOR n = 1, 2, ...
    x := (u(n-1) + v(n-1)) / 2
    IF f(x) = 0 THEN RETURN x
    IF f(x)*f(v(n-1)) < 0 THEN
        u_n := x;  v_n := v(n-1)
    ELSE
        u_n := u(n-1);  v_n := x
OUTPUT: x with f(x) = 0 (root of f in [a,b])
```
Converges relatively slowly (example: $f(x)=x^2-2$ on $[1,2]$ approximating $\sqrt2$).

**Newton's method** for differentiable $f$: $x_{n+1} := x_n - f(x_n)/f'(x_n)$,
converges (locally, for $x_0$ near a root) much faster than bisection — e.g. for
$f(x)=x^2-2$, $x_0=1$: $1, 1.5, 1.41\overline6, 1.41421\,56862\ldots \to \sqrt2$.

**Convergence.** $(a_{n_j})_{j\in\mathbb N}$ (with $n_1<n_2<\dots$) is a *subsequence*
of $(a_n)$. $(a_n)$ is:
- **bounded** iff $\exists C>0: \forall n: \|a_n\|\le C$;
- **convergent with limit** $a\in V$ iff $\forall\epsilon>0\,\exists N=N(\epsilon)\in\mathbb N\,\forall n\ge N: \|a_n-a\|<\epsilon$ (otherwise *divergent*);
- a **Cauchy sequence** iff $\forall\epsilon>0\,\exists N\,\forall n,m\ge N: \|a_n-a_m\|<\epsilon$.

**Theorem.** (a) convergent $\Rightarrow$ bounded; (b) convergent $\Rightarrow$ Cauchy;
(c) limits are unique. (Proofs by direct $\epsilon$-estimates / triangle inequality;
uniqueness via contradiction assuming two distinct limits $a\ne\bar a$.)

Notation: $\lim_{n\to\infty}a_n=a$ or $a_n\to a$. *Improper convergence* / divergence
to $\pm\infty$ for real sequences: $\lim a_n=\infty \iff \forall C>0\,\exists N\,\forall n\ge N: a_n>C$ (analogously for $-\infty$).

**Algebra of limits.** For convergent $(a_n)\to a$, $(b_n)\to b$: $(a_n+b_n)\to a+b$,
$(\lambda a_n)\to\lambda a$, $(a_n b_n)\to ab$, and if $b_n\ne0,\,b\ne0$ then
$(a_n/b_n)\to a/b$; also $\sqrt[m]{a_n}\to\sqrt[m]{a}$ (for $a_n\ge0$).

**Convergence speed.** $(a_n)\to a$ is:
- (at least) **linearly convergent** if $\exists C\in(0,1), N: \|a_{n+1}-a\|\le C\|a_n-a\|\ \forall n\ge N$;
- **superlinearly convergent** if $\exists$ null sequence $C_n\ge0$ with $\|a_{n+1}-a\|\le C_n\|a_n-a\|$;
- convergent **of order $p>1$** if $\exists C\ge0: \|a_{n+1}-a\|\le C\|a_n-a\|^p$.

### 4.1 Convergence criteria for real sequences

Monotonicity: increasing/strictly increasing/bounded above; analogous for decreasing.
**Theorem:** a monotone increasing, bounded-above real sequence converges, with
$\lim a_n = \sup\{a_n\mid n\in\mathbb N\}$ (proof uses completeness via supremum).

**Nested-interval principle (Intervallschachtelung):** monotone increasing $(a_n)$,
monotone decreasing $(b_n)$ with $a_n\le b_n$ and $\lim(b_n-a_n)=0$ converge to a
common limit $\xi$, with error bounds $|a_n-\xi|\le|b_n-a_n|$, $|b_n-\xi|\le|b_n-a_n|$.
Example: arithmetic–geometric mean via $a_{n+1}=\sqrt{a_nb_n}$, $b_{n+1}=(a_n+b_n)/2$.

**Bernoulli's inequality:** $\forall x\ge-1, n\in\mathbb N: (1+x)^n \ge 1+nx$ (equality
iff $n=1$ or $x=0$).

**Geometric sequence** $a_n=q^n$: $\to+\infty$ for $q>1$; $\to1$ for $q=1$; $\to0$ for
$|q|<1$; bounded but not convergent for $q=-1$; divergent (no improper limit) for $q<-1$.

Worked limit example: $a_n = \sqrt{n^2+5n+1}-n \to \dfrac52$ (via rationalizing by
the conjugate).

**Bolzano–Weierstraß theorem:** every bounded real sequence has a convergent
subsequence. See [[bolzano-weierstrass-theorem]] for the full statement/proof.
**$\liminf$/$\limsup$** := smallest/largest accumulation point (limit of a
convergent subsequence).

**Cauchy convergence criterion:** $\mathbb R$ is complete, i.e. every real Cauchy
sequence converges. See [[cauchy-convergence-criterion]].

### 4.2 Convergence in normed vector spaces

Counterexample showing norm-dependence of convergence: the "tent" functions
$f_n\in C[0,1]$ ($f_n(0)=f_n(2/n)=0$, peak $f_n(1/n)=1$) satisfy $\|f_n\|_2\to0$
(converges to $0$ in the $L^2$-type norm) but $\|f_n\|_\infty=1$ for all $n$
(does **not** converge in the maximum norm) — convergence of a sequence depends on
the norm used, in infinite-dimensional spaces.

**Norm equivalence theorem:** on a finite-dimensional vector space $V$, any two
norms $\|\cdot\|,\|\cdot\|'$ are equivalent: $\exists C,C'>0: \|v\|\le\|v\|'\le C'\|v\|$.
Consequently, in finite dimensions convergence does not depend on the chosen norm
(unlike the counterexample above in $C[0,1]$, which is infinite-dimensional).
A sequence in $\mathbb R^n$ converges iff every coordinate sequence converges in $\mathbb R$
(componentwise convergence, w.r.t. $\|\cdot\|_\infty$).

### 4.3 Convergence criteria for series

A **series** $\sum a_k$ is the sequence of partial sums $s_n=\sum_{k=0}^n a_k$; it
*converges* with sum $s=\sum_{k=0}^\infty a_k$ iff $(s_n)$ converges.

**Basic criteria:** Cauchy criterion for series
($\sum a_k$ convergent $\iff \forall\epsilon\exists N\forall m,n\ge N: |\sum_{k=n}^m a_k|<\epsilon$);
necessary condition $\sum a_k$ convergent $\Rightarrow a_k\to0$; linearity of
convergent series; **Leibniz criterion**: an alternating series $\sum(-1)^k a_k$
with $a_k\ge0$ monotonically decreasing to $0$ converges, with partial-sum sandwich
$\sum_{k=0}^{2n-1}(-1)^ka_k \le \sum_{k=0}^\infty(-1)^ka_k \le \sum_{k=0}^{2n}(-1)^ka_k$.

Worked examples: **geometric series** $\sum q^k = \frac{1}{1-q}$ for $|q|<1$,
diverges for $|q|\ge1$; **harmonic series** $\sum 1/k$ diverges; **alternating
harmonic series** $\sum(-1)^k\frac{1}{k+1} = \ln2$ (conditionally convergent).

**Absolute convergence:** $\sum a_k$ is absolutely convergent iff $\sum|a_k|$
converges. The alternating harmonic series is convergent but not absolutely
convergent (since $\sum|(-1)^k/(k+1)| = $ harmonic series, divergent).

**Convergence tests for absolute convergence:**
(a) $\sum a_k$ absolutely convergent $\iff \left(\sum_{k=0}^n|a_k|\right)_{n\ge0}$ bounded;
(b) **Comparison (majorant) test**: $|a_k|\le b_k \wedge \sum b_k$ convergent $\Rightarrow \sum a_k$ abs. convergent;
(c) **Ratio (quotient) test**: $|a_{k+1}/a_k|\le q<1$ for $k\ge k_0 \Rightarrow \sum a_k$ abs. convergent (divergent if the limit of $|a_{k+1}/a_k| > 1$);
(d) **Root test**: $\sqrt[k]{|a_k|}\le q<1$ for $k\ge k_0 \Rightarrow \sum a_k$ abs. convergent (divergent if $\lim\sqrt[k]{|a_k|}>1$).

Worked examples: $\sum 1/k(k+1) = 1$ (telescoping); $\sum 1/k^r$ ($r\ge2$) converges
(comparison with telescoping majorant); known values (without proof)
$\sum 1/k^2=\pi^2/6$, $\sum1/k^4=\pi^4/90$, $\sum1/k^6=\pi^6/945$; the **exponential
series** $\sum z^k/k!$ converges absolutely for all $z\in\mathbb C$ (ratio test),
defining $\exp(z) := \sum_{k=0}^\infty z^k/k!$.

**Rearrangement theorem:** if $\sum a_k$ is absolutely convergent, every
rearrangement $\sum a_{\sigma(k)}$ (for bijection $\sigma:\mathbb N_0\to\mathbb N_0$)
is also absolutely convergent with the **same** sum.

**Multiplication of series / Cauchy product.** For absolutely convergent
$\sum a_\ell$, $\sum b_m$, and any bijection $\sigma:\mathbb N_0\to\mathbb N_0\times\mathbb N_0$,
$$\sum_{k=0}^\infty a_{\sigma_1(k)}b_{\sigma_2(k)} = \left(\sum_{\ell=0}^\infty a_\ell\right)\left(\sum_{m=0}^\infty b_m\right),$$
independent of the chosen enumeration $\sigma$ (by the rearrangement theorem). The
**Cauchy product**, using diagonal numbering, gives
$$\left(\sum_{\ell=0}^\infty a_\ell\right)\left(\sum_{m=0}^\infty b_m\right) = \sum_{n=0}^\infty\left(\sum_{k=0}^n a_k b_{n-k}\right).$$

---

## Notes for the wiki

- All content above is typed lecture slides (not handwritten), with occasional
  handwritten annotations (underlines, side remarks) by the user in blue pen —
  these were used only to confirm emphasis, not transcribed verbatim.
- Numbering follows the original German slide sections (1.1–1.3, 2.1–2.3, 3.1–3.2, 4.1–4.3).
- No contradictions with later sources yet (first source ingested).
