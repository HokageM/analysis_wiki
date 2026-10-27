# Log

Append-only record of ingests, queries, and lint passes.

Format: `## [YYYY-MM-DD] type | Title`

<!-- Example:
## [2026-04-02] ingest | Analysis 1 - Lecture 3 - Sequences and Limits
- Source: raw/analysis1/lecture_03.pdf
- Pages touched: wiki/concepts/limits.md, wiki/theorems/bolzano-weierstrass.md, wiki/index.md
-->

## [2026-10-25] ingest | Analysis 1 — Lecture Slides 1 (analysis_1_1.pdf)
- Source: raw/analysis1/analysis_1_1.pdf (32 scanned pages / 124 slides, typed lecture slides, German, translated to English)
- Pages created: wiki/summaries/analysis1-01-logic-sets-functions-numbers-sequences.md, wiki/concepts/logic-and-sets.md, wiki/concepts/functions.md, wiki/concepts/real-numbers-and-axioms.md, wiki/concepts/sequences-and-convergence.md, wiki/concepts/series-and-convergence-tests.md, wiki/theorems/bolzano-weierstrass-theorem.md, wiki/theorems/cauchy-convergence-criterion.md
- Pages updated: wiki/index.md

## [2026-10-25] ingest | Analysis 1 — Lecture Slides 2 (analysis_1_2.pdf)
- Source: raw/analysis1/analysis_1_2.pdf (25 scanned pages / slides 125-224, typed lecture slides, German, translated to English)
- Pages created: wiki/summaries/analysis1-02-continuity-differentiability-taylor-fixedpoint.md, wiki/concepts/continuity.md, wiki/concepts/compactness.md, wiki/concepts/differentiability.md, wiki/concepts/mean-value-theorems-and-extrema.md, wiki/concepts/taylor-series.md, wiki/concepts/fixed-point-iteration.md, wiki/concepts/function-sequences-and-uniform-convergence.md, wiki/theorems/banach-fixed-point-theorem.md
- Pages updated: wiki/concepts/functions.md (added continuity/differentiability/Taylor-series facts for elementary functions), wiki/index.md

## [2026-10-25] ingest | Analysis 1 — Handwritten Formula Sheet (Analysis_1_formulas.pdf)
- Source: raw/analysis1/Analysis_1_formulas.pdf (2 pages, handwritten by user, German)
- Pages created: wiki/summaries/analysis1-formulas-handwritten-sheet.md
- Pages updated: wiki/index.md
- Findings: no contradictions with existing lecture-derived pages; one likely
  shorthand transcription slip flagged inline (linearity rule), a few ambiguous
  handwriting fragments flagged inline for the user to double-check.

## [2026-10-25] lint | After Analysis 1 ingests
- Checked all 18 wiki pages (excl. index/log) for inbound-link orphaning: found 1
  orphan, [[analysis1-formulas-handwritten-sheet]] (only linked from index.md).
  Fixed by adding backlinks from wiki/concepts/taylor-series.md,
  wiki/concepts/continuity.md, wiki/concepts/sequences-and-convergence.md.
- No contradictions found between the two lecture-slide sources and the
  handwritten formula sheet.
- Gaps noted for future ingests: complex numbers ($\mathbb C$) are used in
  examples (e.g. $a_n=i^n$, $\exp(z)$ for $z\in\mathbb C$) but have no dedicated
  concept page yet — likely worth creating once Analysis 2/3 sources introduce
  complex analysis formally. "Landau symbols" ($o(\cdot), \mathcal O(\cdot)$) are
  currently only described inline in
  wiki/concepts/mean-value-theorems-and-extrema.md / wiki/concepts/taylor-series.md
  — consider a dedicated page if they recur heavily in later modules.

## [2026-10-25] ingest | Analysis 2 — Lecture Slides 1 (analysis_2_1.pdf)
- Source: raw/analysis2/analysis_2_1.pdf (28 scanned pages, typed lecture slides, German, translated to English)
- Pages created: wiki/summaries/analysis2-01-fixedpoint-recap-power-series.md, wiki/concepts/power-series.md
- Pages updated: wiki/concepts/fixed-point-iteration.md (cross-module confirmation note), wiki/concepts/function-sequences-and-uniform-convergence.md (link to power-series), wiki/index.md
- Findings: Ch. 7 (fixed-point iteration) and §8.1 (uniform convergence) are a
  verbatim recap of analysis_1_2.pdf — no contradictions, confirmed consistent.
  New material: §8.2 power series (radius of convergence, Cauchy–Hadamard
  formula, termwise differentiation, log series expansion).

## [2026-10-25] ingest | Analysis 2 — Lecture Slides 2 (analysis_2_2.pdf)
- Source: raw/analysis2/analysis_2_2.pdf (26 scanned pages / slides 117-220, typed lecture slides, German, translated to English)
- Pages created: wiki/summaries/analysis2-02-integration-curves-fourier-quadrature-fft.md, wiki/concepts/integration-techniques.md, wiki/concepts/improper-integrals.md, wiki/concepts/curves-and-curve-integrals.md, wiki/concepts/fourier-series.md, wiki/concepts/numerical-quadrature.md, wiki/concepts/fast-fourier-transform.md
- Pages updated: wiki/index.md (added new concepts, noted a known content gap)
- Findings: **Content gap** — Chapter 9 (Interpolation) is in the course TOC but
  missing from both Analysis 2 source files provided (slide-number jump from
  high-20s to 117); flagged in wiki/index.md "Known Gaps" section for the user
  to decide whether to source separately. No contradictions found in the
  material that is present (Ch. 10 Integration, Ch. 11 Applications/Curves,
  Ch. 12 Fourier Analysis, Ch. 13 Numerical Quadrature, Ch. 14 FFT).

## [2026-10-25] ingest | Analysis 2 — Handwritten Formula Sheet (analysis_2_formulas.pdf)
- Source: raw/analysis2/analysis_2_formulas.pdf (2 pages, handwritten by user, German)
- Pages created: wiki/summaries/analysis2-formulas-handwritten-sheet.md, wiki/concepts/interpolation.md
- Pages updated: wiki/concepts/numerical-quadrature.md (link to interpolation), wiki/index.md (gap note updated)
- Findings: mostly confirms existing Analysis 2 lecture material (integration
  techniques, improper integrals, fixed-point/Banach recap, uniform convergence,
  power series) with no contradictions. Contains **new** interpolation content
  (Lagrange, Newton divided differences, cubic splines) not found in either
  lecture PDF — partially fills the Chapter 9 gap, with one flagged uncertainty
  exact cubic-spline tridiagonal system) worth double-checking later.

## [2026-10-25] lint | After Analysis 2 ingests
- Checked all 29 wiki pages (excl. index/log) for inbound-link orphaning: none
  found — every page has at least one inbound link from another wiki page.
- No contradictions found across the four Analysis 2 sources and the existing
  Analysis 1 material (the Ch. 7/§8.1 recap in analysis_2_1.pdf was verbatim
  consistent; the handwritten formula sheet matched lecture content exactly
  except for new interpolation content, now captured in [[interpolation]]).
- Open gap carried forward: Chapter 9 (Interpolation) lecture source still
  missing; [[interpolation]] is reconstructed from handwritten notes only, with
  one flagged uncertainty (cubic spline tridiagonal system).
- Other gaps noted previously (complex numbers page, Landau symbols page) still
  open — not yet urgent given current source coverage.

## [2026-10-25] ingest | Analysis 3 — Lecture Slides 1 (analysis_3_1.pdf)
- Source: raw/analysis3/analysis_3_1.pdf (32 scanned pages / slides 1-124, typed lecture slides, German, translated to English)
- Pages created: wiki/summaries/analysis3-01-multivariable-calculus-extrema-implicit-lagrange-newton.md, wiki/concepts/partial-derivatives-and-gradient.md, wiki/concepts/vector-calculus-operators.md, wiki/concepts/multivariable-chain-rule-and-jacobian.md, wiki/concepts/multivariable-taylor-and-extrema.md, wiki/theorems/implicit-function-theorem.md, wiki/concepts/lagrange-multipliers.md, wiki/concepts/multivariable-newton-method.md
- Pages updated: wiki/concepts/fixed-point-iteration.md (link to multivariable extension), wiki/index.md
- Findings: new module (Analysis 3 = multivariable calculus), builds directly on
  Analysis 1 differentiability/Taylor concepts and Analysis 1/2 fixed-point
  iteration. No contradictions found. Covers Ch. 17 (partial derivatives,
  gradient, div/curl/Laplacian, Jacobian, chain rule, multivariable MVT/Taylor,
  Hessian), Ch. 18 (extrema classification, implicit function theorem, Lagrange
  multipliers, multivariable/damped Newton's method, Gauss–Newton), and the very
  start of Ch. 19 (multiple integrals — continues in the next source).

## [2026-10-25] ingest | Analysis 3 — Lecture Slides 2 (analysis_3_2.pdf)
- Source: raw/analysis3/analysis_3_2.pdf (22 scanned pages / slides 122-206, typed lecture slides, German, translated to English)
- Pages created: wiki/summaries/analysis3-02-multiple-integrals-fubini-curve-surface-green-gauss-stokes.md, wiki/concepts/multiple-integrals-and-fubini.md, wiki/concepts/curve-and-surface-integrals.md, wiki/theorems/vector-calculus-integral-theorems.md
- Pages updated: wiki/concepts/curves-and-curve-integrals.md (link to 2nd-kind extension), wiki/index.md
- Findings: completes Chapter 19 and the entire Analysis 3 lecture syllabus
  (multiple integrals, Fubini, transformation theorem, curve/surface integrals,
  Green/Gauss/Stokes theorems). No contradictions found; builds directly on
  Analysis 2's curve-integral material and Analysis 3 part 1's div/curl
  concepts. Course lecture coverage is now complete except for the still-open
  Chapter 9 (Interpolation) gap in Analysis 2.

## [2026-10-25] ingest | Analysis 3 — Handwritten Formula Sheet (analysis_3_formulas.pdf)
- Source: raw/analysis3/analysis_3_formulas.pdf (2 pages, handwritten by user, German)
- Pages created: wiki/summaries/analysis3-formulas-handwritten-sheet.md
- Pages updated: wiki/concepts/multivariable-taylor-and-extrema.md, wiki/concepts/lagrange-multipliers.md, wiki/theorems/vector-calculus-integral-theorems.md (backlinks), wiki/index.md
- Findings: entirely a condensed recap of both Analysis 3 lecture sources
  (extrema/Hessian, implicit functions, Lagrange multipliers, curvilinear
  coordinates, Steiner's theorem, Green's theorem, potentials/integrability
  condition) — no contradictions, no new theorems. Two passages flagged as
  illegible/ambiguous rather than guessed ("Stromlinie" entry, one
  "Hesse"/"Masse"-labeled integral).

## [2026-10-25] lint | After Analysis 3 ingests (final pass)
- Checked all 42 wiki pages (excl. index/log) for inbound-link orphaning: none
  found. Checked for broken `[[links]]` pointing to nonexistent pages: none
  found. Checked `wiki/index.md` lists every page: confirmed complete.
- No contradictions found anywhere across all 11 ingested sources (3 Analysis 1,
  4 Analysis 2, 4 Analysis 3 — lecture slides + handwritten formula sheets).
- Remaining known gap: Chapter 9 (Interpolation) in Analysis 2 — lecture source
  still not provided; [[interpolation]] exists but is reconstructed from
  handwritten notes only, with one flagged uncertainty (cubic spline
  tridiagonal system).
- Other minor gaps noted earlier (no dedicated page for complex numbers or
  Landau symbols) remain open but low-priority given current source coverage.
- The wiki is now a complete, cross-referenced knowledge base spanning
  Analysis 1 (logic/sets/functions through Taylor series and fixed-point
  iteration), Analysis 2 (power series, integration techniques, Fourier
  analysis, numerical quadrature, FFT), and Analysis 3 (multivariable calculus,
  extrema, implicit functions, Lagrange multipliers, multivariable Newton's
  method, multiple integrals, and the full vector calculus integral theorem
  hierarchy: Green, Gauss, Stokes).
