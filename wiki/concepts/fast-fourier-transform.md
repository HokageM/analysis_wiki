---
title: "Fast Fourier Transform (FFT)"
module: general
type: concept
sources: [raw/analysis2/analysis_2_2.pdf]
updated: 2026-10-25
---

# Fast Fourier Transform (FFT)

Related: [[fourier-series]],
[[analysis2-02-integration-curves-fourier-quadrature-fft]].

## Discrete Fourier Transform (DFT)

$$\hat z(m) = \sum_{n=0}^{N-1} z(n)\,\omega_N^{nm}, \quad 0\le m\le N-1, \qquad \omega_N:=e^{-2\pi i/N}.$$
Direct evaluation: $\mathcal O(N^2)$.

## Cooley–Tukey radix-2 algorithm

For $N=2^k$, using $\omega_{2N}^2=\omega_N$, split into even/odd-indexed
subsequences $u(n):=z(2n)$, $v(n):=z(2n+1)$ (each length $N/2$):
$$\hat z(m) = \hat u(m)+\omega_N^m\hat v(m) \ (0\le m< N/2), \qquad \hat z(N/2+\ell) = \hat u(\ell)-\omega_N^\ell\hat v(\ell) \ (0\le\ell<N/2).$$

```
FUNCTION FFT(z[0..N-1]):           # N = 2^k
    IF N == 1: RETURN z            # base case
    u := FFT( z[0], z[2], ..., z[N-2] )   # even-indexed, length N/2
    v := FFT( z[1], z[3], ..., z[N-1] )   # odd-indexed,  length N/2
    FOR m = 0, ..., N/2 - 1:
        twiddle := exp(-2*pi*i*m/N)
        z_hat[m]        := u[m] + twiddle * v[m]
        z_hat[m + N/2]   := u[m] - twiddle * v[m]
    RETURN z_hat
```

**Complexity:** $\mathcal O(N\log N)$ (vs. $\mathcal O(N^2)$ direct DFT) — $k=\log_2N$
recursion levels, each $\mathcal O(N)$ work.

## Inverse DFT

$$z(n) = \frac1N\sum_{m=0}^{N-1}\hat z(m)e^{2\pi imn/N}, \quad 0\le n\le N-1$$
(computable with the same FFT routine up to scaling/conjugation). MATLAB:
`w = fft(z)`, `z = ifft(w)`.

## Relation to Fourier series

The DFT/FFT is the finite, discrete-sampling analogue of the continuous Fourier
series theory in [[fourier-series]] — both decompose a signal into a sum of
complex exponentials $e^{ik\omega t}$.
