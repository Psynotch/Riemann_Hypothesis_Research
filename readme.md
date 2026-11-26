# Riemann Hypothesis — Computational Research

A step-by-step computational investigation of the **Riemann Hypothesis (RH)** using Python, rigorous numerical methods, zero isolation, and reproducibility checks.

This repository documents the progression of the research, from exploring the non-trivial zeros of the Riemann zeta function to conducting large-scale, computer-assisted verification using FLINT and Arb ball arithmetic.

> **Current computational milestone:** Verified 10,142 zero enclosures up to height 10,000, with all 10,142 Hardy Z-function interval sign checks passing.

**Important:** These computations verify a finite region. They do not constitute a proof of the Riemann Hypothesis.

---

## Research objective

The Riemann Hypothesis states that every non-trivial zero of the Riemann zeta function has real part equal to one half:

ζ(s) = 0 ⇒ Re(s) = 1/2

The project investigates the non-trivial zeros numerically and uses rigorous computational techniques to verify increasingly large finite regions of the critical strip.

The computational region covered by the latest session is:

**0 < Re(s) < 1, 10 < |Im(s)| < 10,000**

---

## Repository navigation

The notebooks are arranged in chronological order. Each session builds on the methods and results of earlier sessions.

| Session | Notebook | Main objective |
|---|---|---|
| 01 | `Session1.ipynb` | Initial exploration of the non-trivial zeros |
| 02 | `Session2.ipynb` | Numerical root searches and zero refinement |
| 03 | `Session3_Argument_Principle.ipynb` | Argument principle and contour winding |
| 04 | `Session4_Rigorous_Zero_Counting.ipynb` | Rigorous contour-based zero counting |
| 06 | `Session6_Full_Critical_Strip_Verification.ipynb` | Verification across the full critical strip |
| 05 | `Session5_Individual_Zero_verification.ipynb` | Individual zero verification |
| 07 | `Session7_Extended_Zero_Verification.ipynb` | Extension of verification to height 100 |
| 08 | `Session8_Automated_verification_of_649_zeros.ipynb` | Automated verification up to height 1,000 |
| 09 | `Session9_Automated_Turing_Verification.ipynb` | Automated Turing-method zero isolation |
| 10 | `Session10_Extended_Turing_Verification.ipynb` | Extension of Turing verification to height 5,000 |
| 11 | `Session11_Independent_Reproducibility_Audit.ipynb` | Precision comparisons and reproducibility audit |
| 12 | `Session12_Height_10000_Verification.ipynb` | Extended verification up to height 10,000 |

*Session numbering reflects the development history. A session number not listed here is not currently represented by a notebook in this navigation table.*

---

## Session-by-session guide

### Phase 1 — Initial exploration

**Session 01 — Exploring the zeros**

Introduces the Riemann zeta function and investigates its non-trivial zeros using numerical computation.

**Session 02 — Numerical root searches**

Explores two-dimensional numerical root searches in the complex plane, followed by high-precision refinement of candidate roots.

**Session 03 — The argument principle**

Introduces contour integration and the argument principle to investigate how many zeros lie inside a selected region.

**Session 04 — Rigorous zero counting**

Moves beyond ordinary numerical contour sampling by using Arb ball arithmetic to obtain rigorous enclosures and certify the contour calculation.

**Session 05 - Individual_Zero_verification.ipynb**

Focuses on the verification of individual non-trivial zeros, building on the earlier numerical and zero-counting investigations.

### Phase 2 — Expanding the verification region

**Session 06 — Full critical-strip verification**

Extends the zero-counting region to the full critical strip and compares the total zero count with Hardy Z-function sign changes.

**Session 07 — Extension to height 100**

Expands the verification region and checks the corresponding zero count and Hardy Z-function intervals.

### Phase 3 — Automated verification

**Session 08 — Verification up to height 1,000**

Introduces an automated workflow for zero verification.

Reported result:
- 649 zeros counted.
- 649 zero enclosures generated.
- 649 Hardy Z-function interval sign checks passed.
- No unresolved contour subdivisions.

**Session 09 — Automated Turing verification**

Introduces an automated Turing-method workflow using FLINT for zero counting and zero isolation.

**Session 10 — Extension to height 5,000**

Extends the automated verification process.

Reported result:
- 4,520 zero enclosures.
- 4,520 Hardy Z-function interval checks passed.
- No failed checks.

### Phase 4 — Reproducibility and extended verification

**Session 11 — Independent reproducibility audit**

Investigates whether the results remain consistent under different working precisions.

The audit includes:
- Comparison of zero enclosures at 192-bit and 256-bit precision.
- Hardy Z-function sign verification.
- Selected cross-checks using mpmath.
- Certificate CSV reload and integrity checks.

**Session 12 — Verification up to height 10,000**

The latest computational milestone.

Reported results:

| Measurement | Result |
|---|---:|
| Zero count at height 1,000 | 649 |
| Zero count at height 5,000 | 4,520 |
| Zero count at height 10,000 | 10,142 |
| Zero enclosures generated | 10,142 |
| Enclosures consistent across precisions | 10,142 / 10,142 |
| Hardy Z interval checks passed | 10,142 / 10,142 |
| Selected mpmath sign cross-checks | 18 / 18 |
| Failed Hardy Z checks | 0 |

The session also exports a CSV certificate containing the zero-enclosure data.

---

## Technologies and mathematical methods

| Technology / method | Purpose |
|---|---|
| Python | Research implementation and automation |
| Google Colab | Interactive computational environment |
| python-flint / FLINT | Arbitrary-precision numerical computation and zero isolation |
| Arb ball arithmetic | Rigorous numerical enclosures |
| Hardy Z-function | Real-valued checks for zeros on the critical line |
| Turing's method | Counting zeros up to a given height |
| Argument principle | Contour-based zero counting |
| mpmath | Selected numerical cross-checks |

---

## Understanding the verification

The project combines several computational techniques:

1. **Zero counting:** Turing's method is used through FLINT to determine the number of zeros up to a given height.
2. **Zero isolation:** FLINT generates rigorous enclosures for individual zeros.
3. **Hardy Z-function checks:** Opposite signs at the endpoints of an interval establish the existence of a zero on the critical line within that interval.
4. **Precision comparison:** Results are compared at different working precisions to test numerical consistency.
5. **Reproducibility:** Exported data is reloaded and checked to ensure the recorded results remain consistent.

These techniques provide strong computational evidence within the tested finite region. The reliability of the conclusions also depends on the correctness of the underlying library implementations and the verification procedures.

In particular, using multiple functions from the same FLINT library should not be mistaken for fully independent verification by separate implementations.

---

## Current research direction

The research is now moving beyond simply increasing the number of verified zeros.

A recently announced formal proof claim by **Levent Alpöge, developed with assistance from Claude and formalized in Lean**, has introduced a new direction for investigation.

The next stage is to study:

- The mathematical structure of the claimed proof.
- The role of Lean theorem proving and formal verification.
- The main inequalities and intermediate theorems.
- The relationship between the formal proof and the classical theory of the zeta and Dirichlet L-functions.
- Whether individual components can be independently understood and reconstructed.

The objective is to understand the mathematics behind the claim rather than simply rely on the fact that a formal proof compiles.

This is an ongoing investigation. Formal verification, independent mathematical understanding, and wider peer review are distinct parts of the process.

---

## Important distinction

The results in this repository should be interpreted as **finite computational verification**, not as a proof of the Riemann Hypothesis.

Verifying zeros up to a finite height cannot establish that every non-trivial zero, at every possible height, lies on the critical line.

The project aims to maintain transparent calculations, reproducible results, and mathematically responsible conclusions.

---

## Author

Mohammed Owais
mohammedowaisshaik@gmail.com

Contributions, mathematical discussions, and constructive feedback are welcome.

---

*An ongoing computational exploration of one of mathematics' most important unsolved problems.*
