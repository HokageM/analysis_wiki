---
title: "Bolzano–Weierstraß Theorem"
module: general
type: theorem
sources: [raw/analysis1/analysis_1_1.pdf]
updated: 2026-10-25
---

# Bolzano–Weierstraß Theorem

Used in: [[analysis1-01-logic-sets-functions-numbers-sequences]],
[[sequences-and-convergence]], [[cauchy-convergence-criterion]].

## Statement

Every bounded real sequence $(a_n)_{n\in\mathbb N}$ possesses a convergent subsequence.

## Proof (bisection / nested intervals)

Let $(a_n)$ be bounded with all $a_n \in [A,B]$. Construct a nested interval
sequence by repeated bisection:

```
A1 := A;  B1 := B
FOR k = 1, 2, 3, ...
    C := (Ak + Bk) / 2
    IF {n | a_n ∈ [Ak, C]} is infinite THEN
        A(k+1) := Ak;  B(k+1) := C
    ELSE
        A(k+1) := C;   B(k+1) := Bk
```

At each step, one of the two halves contains infinitely many terms of the sequence
(since the whole interval does, and it's split in two), so the construction never
gets stuck. The intervals $[A_k,B_k]$ form a nested-interval sequence (each
containing infinitely many $a_n$), with $A_k \le B_k$ and $(A_k), (B_k)$ converging
to a common limit $\ell = \lim_{k\to\infty}A_k=\lim_{k\to\infty}B_k$
(nested-interval principle).

Now extract a subsequence $(a_{n_k})$ with $a_{n_k}\in[A_k,B_k]$ for all $k$:
set $n_1:=1$; for $k=2,3,\dots$ choose $n_k>n_{k-1}$ with $a_{n_k}\in[A_k,B_k]$
(possible since each interval contains infinitely many terms). Since
$A_k \le a_{n_k} \le B_k$ for all $k$, it follows that $\lim_{k\to\infty}a_{n_k}=\ell$. $\blacksquare$

## Definition: accumulation point

If $(a_{n_k})_{k\in\mathbb N}$ is a convergent subsequence of $(a_n)_{n\in\mathbb N}$,
its limit is called an **accumulation point (Häufungspunkt)** of $(a_n)$.
$\liminf a_n$ / $\limsup a_n$ denote the smallest / largest accumulation point.

## Consequences

- In finite-dimensional normed vector spaces (e.g. $\mathbb R^n$), Bolzano–Weierstraß
  still holds (via componentwise convergence and the norm equivalence theorem).
- Used directly in the proof of the [[cauchy-convergence-criterion]] (completeness of $\mathbb R$).
