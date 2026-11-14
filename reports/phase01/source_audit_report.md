# Phase 01 — Computational workbook source audit

## Evidence boundary and audit status

**Audit status:** `COMPLETED_WITH_REVIEW_ITEMS`. A blocked status indicates structural or scientific data errors that require correction before downstream use.

This document records a read-only, structural audit of the published supplementary workbook. Matching source values does not establish DFT convergence, experimental ceramic synthesis, ferroelectric response or capacitor reliability.

## Source identity

- Workbook: `Supplementary Dataset.xlsx`
- SHA-256: `5d28d5641ea8c564cec38b70d8c12883117efaa3b6bd4309c5400ebd452c95fb`
- Byte size: 27,198,367
- Source modifications: none

## Worksheet inventory

| Sheet | Data rows | Columns | Unique composition keys | Blank cells | Formula cells |
|---|---:|---:|---:|---:|---:|
| S1 | 30,301 | 100 | 30,301 | 0 | 30,301 |
| S2 | 231 | 102 | 231 | 0 | 0 |
| S3 | 231 | 82 | 231 | 0 | 0 |
| S4 | 231 | 10 | 231 | 0 | 0 |

**Interpretation.** S1 is a candidate/descriptors space, not a set of 30,301 independently verified DFT labels. S2 and S4 store reference-energy fields; S3 is the 82-column selected feature representation.

## Keyed linkage comparisons

| Comparison | Check | Matches/comparisons | Missing in right | Missing in left | Value mismatches |
|---|---|---:|---:|---:|---:|
| S2 to S3 | composition key coverage | 231 | 0 | 0 | 0 |
| S2 to S4 | composition key coverage | 231 | 0 | 0 | 0 |
| S3 to S4 | composition key coverage | 231 | 0 | 0 | 0 |
| S2 to S3 | matched values | 18,018 | 0 | 0 | 0 |
| S2 to S4 | matched values | 462 | 0 | 0 | 0 |
| S2 to S1 | labelled key present among S1 candidates | 21 | 210 | 0 | 0 |

Comparisons use Ba/Sr/La/Ti identity keys rather than worksheet row numbers. Numeric equality allows absolute tolerance 1×10⁻⁷ or relative tolerance 1×10⁻⁹, whichever is greater.

## Crystal-chemistry diagnostics

- S2 compositions assessed: 231.
- A-site sum/sign tests: 231; violations: 0.
- Ti coefficient below 1: 210.
- Ti = 1 − La/2 within tolerance: 231 of 231.
- Positive La coefficients: 210.

The nominal A-site formula (Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃ is not a warrant to overwrite the workbook's reported Ti coefficients. Sr²⁺ substitution is isovalent; La³⁺ substitution is aliovalent. The pattern in tabulated Ti values raises a **representation and charge-accounting question**. It cannot, on its own, establish real Ti vacancies; the computational work uses a documented VCA treatment.

## Issues and next actions

Severity meanings: **ERROR** blocks downstream readiness; **WARNING** requires inspection; **REVIEW** records an unresolved scientific interpretation.

- **WARNING — S2_OUTSIDE_S1** (S2/S1, compositions): Labelled compositions absent from candidate sheet. **Follow-up:** Review published candidate domain.
- **REVIEW — TI_LA_REPRESENTATION** (S2, Ti/La coefficients): Ti < 1 for 210 records; Ti=1−La/2 matches 231 of 231. **Follow-up:** Reconcile spreadsheet coefficient convention with VCA and source methods; do not infer vacancies.

## Phase boundaries and open decisions

- Phase 01 validates spreadsheet structure, composition identity and cross-sheet agreement only.
- Formation-energy units and reference states require separate source-method reconciliation.
- DFT convergence, VCA adequacy, defect chemistry, device manufacturing and dielectric performance have not been independently verified.
- Phase 02 will define scientific data semantics; Phase 03 will expand chemical QC and record-level exception review.
- Public GitHub release should omit the original publisher workbook and review any row-level extracts for licensing/redistribution compliance.
