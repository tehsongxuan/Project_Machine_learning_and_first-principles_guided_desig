# Phase 00 — Scientific scope and provenance

**Research domain:** BaTiO₃-based perovskite dielectrics for capacitor applications  
**Status:** `COMPLETE_FILE_REGISTRATION`  
**Evidence boundary:** File-level source registration; no independently reproduced calculations or measurements.

## 1. Scientific research problem

The study combines first-principles calculations with machine learning to examine how nominal Sr/La A-site substitution changes computed formation energies in BaTiO₃-related composition space. The reported screening space comprises 30,301 candidates. File registration establishes which published documents and workbook bytes are available before composition-level quality control.

**Chemistry:** BaTiO₃ is an ABO₃ perovskite: Ba at the A site, Ti at the B site and O in the oxide framework. The reported nominal composition is `(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`. Nonnegative A-site fractions require `x ≥ 0`, `y ≥ 0`, and `x + y ≤ 1`. These are compositional bookkeeping conditions, not proof of phase stability or synthesizability.

**Charge and defects:** Sr²⁺ replacing Ba²⁺ is isovalent; La³⁺ replacing Ba²⁺ is aliovalent. The article describes VCA electronic averaging and supercell electron-counting treatments, without explicitly adding ionic vacancy defects in these calculations. Real defects cannot be inferred from the nominal formula alone. The Ti–La coefficient interpretation remains an open chemistry-QC item until the workbook and method are reconciled.

## 2. Computational evidence and units

- **DFT/VCA reference data:** derived from electronic-structure approximations and calculation settings, not direct capacitor measurements.
- **Formation energy:** evaluated using explicit reference states and stoichiometric coefficients described in supplementary Text S1. Reported units must remain attached to each quantity (e.g., eV/atom); lower numerical energies are not, by themselves, a demonstration of equilibrium phase stability against every competing phase.
- **ML screening:** published model estimates are statistical surrogates, not additional independent DFT calculations. Method validation and grouping logic belong to later phases.
- **Experiment:** dielectric permittivity, loss tangent, frequency response and temperature dependence require measured specimens and protocols. They cannot be asserted from the workbook checksum.

## 3. Scientific metadata and descriptor lineage

Source roles are classified separately as research article, supporting method description, computational workbook and optional planning documents. The supplement reports an initial 100-feature set with 16 constant features removed, plus removal of a final-energy descriptor and the formation-energy target, leaving 82 model input descriptors. This is **reported feature selection**, not an independent reproduction of the calculation. Leakage audits must check that the energy target and proxy quantities do not enter the model input.

## 4. Provenance and reproducibility

- `SHA-256` identifies file bytes, not scientific truth or publisher authenticity.
- Container validation checks a PDF signature or required Office package member, not full scientific readability or cell integrity.
- Exact bytes and observed filenames are recorded; download suffixes such as `(1)` or `(2)` do not redefine chemical evidence.
- Generated CSV, JSON and Markdown use stable ordering, fixed schema and no execution timestamps or absolute account paths.
- Acquisition dates and supplementary reuse conditions remain unverified where source evidence is unavailable.

## 5. Transferable data-science logic

Data lineage in polymer glass-transition prediction, rheology and formulation studies illustrates the broader need to connect material identity, conditions and a labelled target. The **physical models do not transfer** from polymers to ferroelectric ceramics: glass-transition behaviour and viscoelastic moduli are distinct from perovskite lattice distortions, polarization and computational formation energies. The transferable method is preserving original evidence, units, material identity, model assumptions and applicability limits.

## 6. Scope boundaries and Phase 01 priorities

**Established at Phase 00:** Source-file locations, observed names, file sizes, SHA-256 identifiers, basic container checks and evidence classifications.

**Not established:** Correct S1–S4 row counts; unique composition keys; Ti/La occupancy interpretation; missingness; chemical constraints; descriptor leakage; DFT convergence; reliable ML generalisation; experimental dielectric performance.

**Next scientific checks:** Workbook worksheet structure; composition normalization and A-site balance; energy units and reference states; 231-record linkage reported in source documentation; features and target provenance; unresolved stoichiometric discrepancies. Any anomaly remains flagged until supported by source evidence.

## References (document identifiers, no personal attribution)

- Primary article: https://doi.org/10.1063/5.0314819
- Supplementary collection: https://doi.org/10.60893/figshare.jap.c.8234602
