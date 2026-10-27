---
title: "Interpolation"
module: analysis2
type: concept
sources: [raw/analysis2/analysis_2_formulas.pdf]
updated: 2026-10-25
---

# Interpolation

Related: [[analysis2-formulas-handwritten-sheet]], [[numerical-quadrature]]
(Newton–Cotes quadrature is built on interpolation), [[taylor-series]].

**Provenance note:** this page is reconstructed from the user's handwritten
formula sheet only — the corresponding lecture chapter ("Chapter 9:
Interpolation" in the Analysis 2 syllabus) was not present in the provided PDF
sources. See the gap note in `wiki/index.md` and
[[analysis2-02-integration-curves-fourier-quadrature-fft]]. Treat the details
here as a good-faith reconstruction, not a verbatim lecture transcript — flagged
uncertainties are noted inline.

## Lagrange interpolation

Given nodes $x_0,\dots,x_n$ and data $f(x_0),\dots,f(x_n)$, the **Lagrange basis
polynomials**
$$L_k(x) := \prod_{\substack{j=0\\j\ne k}}^n \frac{x-x_j}{x_k-x_j}$$
satisfy $L_k(x_j)=\delta_{kj}$, so
$$p_n(x) := \sum_{k=0}^n f(x_k)\,L_k(x)$$
is the unique polynomial of degree $\le n$ interpolating the data (this is the
same interpolation polynomial used to construct Newton–Cotes quadrature weights
in [[numerical-quadrature]]).

## Newton's divided-difference form

The same polynomial, built incrementally:
$$p_n(x) = \sum_{k=0}^n f[x_0,\dots,x_k]\prod_{j=0}^{k-1}(x-x_j) = c_0+c_1(x-x_0)+c_2(x-x_0)(x-x_1)+\dots$$
with **divided differences** defined recursively: $f[x_i]:=f(x_i)$,
$$f[x_i,\dots,x_{i+k}] := \frac{f[x_{i+1},\dots,x_{i+k}]-f[x_i,\dots,x_{i+k-1}]}{x_{i+k}-x_i}.$$
Advantage over Lagrange form: adding a new data point only appends one more
term, rather than recomputing the whole polynomial.

## Cubic spline interpolation

For nodes $x_0<\dots<x_n$, $h_i=x_{i+1}-x_i$: piecewise cubic
$S_i(x)=a_i+b_i(x-x_i)+c_i(x-x_i)^2+d_i(x-x_i)^3$ on $[x_i,x_{i+1}]$, interpolating
$f$ at the nodes, with $S\in C^2$ and natural boundary conditions
$S''(x_0)=S''(x_n)=0$. Writing $M_i:=S''(x_i)$:
$$a_i=f(x_i), \quad c_i=\frac{M_i}2, \quad d_i=\frac{M_{i+1}-M_i}{6h_i}, \quad b_i = \frac{f(x_{i+1})-f(x_i)}{h_i}-\frac{h_i}6(2M_i+M_{i+1}),$$
with the $M_i$ solved from a tridiagonal system enforcing $C^2$ continuity across
nodes. **Flagged uncertainty:** the exact right-hand side of that tridiagonal
system was not fully legible in the source handwriting — confirm against a
numerical analysis reference (e.g. Stoer–Bulirsch) before relying on it for
computation.

## Why this matters

Interpolation underlies [[numerical-quadrature]] (Newton–Cotes rules integrate
the interpolation polynomial) and is a natural precursor to spline-based
numerical methods not yet covered elsewhere in this wiki.
