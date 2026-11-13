# BaTiO₃ Materials Data Curation and AI-Ready Workflow Engineering

## Quick navigation — completed Phases 00 and 01

Phase 00 source-registration artefacts are published in this repository. **The Phase 01 S1–S4 computational-workbook audit has also completed successfully** (`COMPLETED_WITH_REVIEW_ITEMS`); its publication files are prepared for upload. Links are relative to this README and become live as the corresponding files are committed to the `main` branch.

- [Repository home](./)
- [Phase 00 — executable Jupyter notebook](./BaTiO3_Phase00.ipynb)
- [Phase 00 — scientific HTML report](./BaTiO3_Phase00.html)
- [View Phase 00 HTML report in a browser (external preview)](https://htmlpreview.github.io/?https://github.com/tehsongxuan/Project_Machine_learning_and_first-principles_guided_desig/blob/main/BaTiO3_Phase00.html)
- [Phase 00 — research scope](./docs/research_scope.md)
- [Phase 00 — source registry (CSV)](./manifests/source_registry.csv)
- [Phase 00 — source manifest (JSON)](./manifests/source_manifest.json)
- [Phase 00 — registration findings](./reports/registration_findings.md)

### Phase 01 — Computational workbook audit (completed; publication prepared)

- [Phase 01 — executed Jupyter notebook](./BaTiO3_Phase01.ipynb)
- [Phase 01 — executed scientific HTML report](./BaTiO3_Phase01.html)
- [View Phase 01 HTML report in a browser (external preview)](https://htmlpreview.github.io/?https://github.com/tehsongxuan/Project_Machine_learning_and_first-principles_guided_desig/blob/main/BaTiO3_Phase01.html)
- [Phase 01 — source audit findings and scientific review priorities](./reports/phase01/source_audit_report.md)
- [Phase 01 — worksheet inventory (CSV)](./reports/phase01/workbook_inventory.csv)
- [Phase 01 — column inventory and source headings (CSV)](./reports/phase01/column_inventory.csv)
- [Phase 01 — Excel-formula inventory (CSV)](./reports/phase01/formula_inventory.csv)
- [Phase 01 — cross-sheet checks (CSV)](./reports/phase01/cross_sheet_checks.csv)
- [Phase 01 — quality-control findings (CSV)](./reports/phase01/qc_findings.csv)

The CSV/Markdown reports above are *generated audit metadata*, not the underlying spreadsheet. Verify their specific contents and source-data reuse terms before public upload, especially the column-heading inventory. **The linked Phase 01 files have not been assumed to be on GitHub until they are actually uploaded.**

- [Project implementation roadmap — Phases 00–09](#7-implementation-roadmap--phases-0009)

**Publication scope:** Phase 00 documents source registration and evidence boundaries; Phase 01 provides a read-only, reproducible audit of the published S1–S4 workbook. Neither phase independently reproduces the DFT calculations, establishes a physical vacancy mechanism, trains a new predictive model or demonstrates experimental capacitor performance. The original research PDF, supplementary DOCX and source XLSX are **not re-hosted**: readers should obtain them from the official publisher (links below). The external Phase 00 HTML preview is hosted by a third-party service; visit it only if comfortable with the service's terms and privacy practices.

---

**An independent research-data engineering project for reproducible, chemistry-aware materials informatics**

**Material system:** Sr/La-substituted barium titanate, nominally `(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`  
**Research methods:** Solid-state chemistry · First-principles calculations · Scientific data curation · Data engineering · Machine-learning validation · Reproducible Python workflows  
**Project status:** Phase 00 source registration, integrity checks and research-scope documentation are complete and published. **Phase 01 workbook auditing and automated source-data QC have been completed** with open scientific review items; GitHub publication files are prepared. The comprehensive scientific schema, independent DFT reproduction, model development and experimental validation remain outside the completed scope.

## Phase 01 — Verified workbook audit and actionable findings

### Audit scope and execution

The Phase 01 Python workflow audits the publisher's `S1`–`S4` Excel worksheets **without modifying the workbook**. It checks file discovery and integrity, inventories worksheet/column/formula structure, matches compositions across sheets, compares declared shared descriptors and energies, and records scientific exceptions with actions. It uses explicit composition identifiers rather than assuming that identical row positions mean identical materials.

The notebook applies eight practical workflow principles: **clarity**, **simplicity**, **reproducibility**, **user-friendly instructions**, **error handling**, **scientific transparency**, **validation/testing**, and **actionable outputs**. Each issue is recorded as evidence for review, not silently rewritten.

The successful local run reported **`COMPLETED_WITH_REVIEW_ITEMS`** and **23 passing engineering checks**. This means the requested structural checks ran successfully; it does **not** mean that the source paper's DFT models, ferroelectric properties or experiments have been independently validated.

| Audit item | Verified Phase 01 result |
|---|---:|
| `S1` candidate-composition rows | 30,301 (100 columns) |
| `S2` DFT-labelled records | 231 (102 columns) |
| `S3` retained-feature records | 231 (82 columns) |
| `S4` computational method/energy records | 231 (10 columns) |
| Composition identity discrepancies across `S2`, `S3`, `S4` | 0 |
| Declared `S2`–`S3` descriptor-value mismatches | 0 of 18,018 comparisons (78 shared fields × 231 records) |
| Declared `S2`–`S4` energy-value mismatches | 0 of 462 comparisons (2 fields × 231 records) |
| `S2` labelled compositions exactly appearing in `S1` | 21 of 231 |
| Labelled compositions with tabulated `Ti < 1` | 210 of 231 |
| Records following the tabulated `Ti = 1 − La/2` relationship | 231 of 231 |
| A-site sum (`Ba + Sr + La ≈ 1`) violations in `S2` | 0 of 231 |

### Scientific interpretation and review decisions

**Open item 1 — Design-space coverage.** Under exact Ba/Sr/La/Ti-key matching, **210 of the 231 labelled `S2` compositions are absent from `S1`**. This may reflect the design and selection of the publisher's candidate space; it is **not** evidence that the DFT results were wrong. **Next action:** consult the article's candidate-generation method and supplementary information before interpreting the populations or combining them for modelling.

**Open item 2 — Ti–La representation.** The published coefficients follow `Ti = 1 − La/2`; 210 labelled entries have tabulated Ti below 1. These are observed **data representation patterns**, not proof of real titanium vacancies. **Next action:** reconcile the spreadsheet convention with the reported virtual crystal approximation (VCA), nominal formula and charge-accounting assumptions while preserving all original source values.

The audit supports source consistency checks, not full phase-specific chemical validation, leakage testing, independent machine-learning benchmarking or experimental validation. These are separate downstream workstreams.

### Reproduce the audit

1. Obtain the **supplementary Excel workbook** from the [publisher's supplementary collection](https://doi.org/10.60893/figshare.jap.c.8234602); do not expect the source XLSX to be stored in this repository.
2. Download [`BaTiO3_Phase01.ipynb`](./BaTiO3_Phase01.ipynb) and place it in the same working directory as `Supplementary Dataset.xlsx` (or a supported numbered filename variant).
3. In JupyterLab, select a Python 3 kernel with the packages required by the notebook. The project was run using the dedicated **Python (BaTiO3 Phase00)** environment. Follow the notebook's setup instructions and input-location checks.
4. Choose **Restart Kernel and Run All Cells**. Confirm the final audit status and inspect the six generated files in `phase01_outputs/`. A missing or ambiguous workbook should produce a **not-completed** status, not a success claim.
5. Compare new findings with the [audit report](./reports/phase01/source_audit_report.md) and [cross-sheet summary](./reports/phase01/cross_sheet_checks.csv) before carrying results into Phase 02.

### Publication, privacy and research-data rights

- **Designed for GitHub:** independently authored notebook code, a public-safe rendered HTML export, aggregate worksheet/QC results, an authored scientific interpretation report and metadata inventories **after a content and licence review**.
- **Keep local or link to the publisher:** original research PDF, supplementary Word document and original Excel workbook; individual unpublished source-value rows or extensive copied tables; local usernames, absolute Windows paths, credentials and temporary Jupyter files.
- **Review before upload:** `column_inventory.csv` reproduces publisher column headings, and other outputs carry source-derived metadata. Confirm the applicable supplementary-dataset permissions and reuse conditions; a separate licence is **not** assumed merely from the article being open access. Check all outputs for personal identifiers and absolute paths.
- **Attribution:** the research papers and original computational dataset belong to their cited authors/rights holders. The code and independently written annotations here are part of a personal research portfolio, **not an A*STAR collaboration or institutional endorsement**.

---

## Research foundation

This project is informed by two complementary peer-reviewed publications:

- **[*Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications*](https://doi.org/10.1063/5.0314819)** — *Journal of Applied Physics* **139**, 064101 (2026). This study supplies the **ceramic materials system, first-principles and machine-learning methodology, and supplementary computational data** used in the project.
- **[*Predicting Faster Than We Can Make: Polymer-Specific Process Physics as a Frontier for Autonomous Soft-Matter Discovery*](https://doi.org/10.1002/marc.70420)** — *Macromolecular Rapid Communications* (2026). This perspective provides the **research-infrastructure motivation** for connecting scientifically complete databases, physical reasoning, feasible materials design, practical processing and experimental validation.

The publications have distinct scientific roles. The ceramic study is the **primary dataset and technical case**; the soft-matter perspective informs **which research questions a trustworthy materials-data workflow must address**. The resulting approach is an **independent methodological synthesis**, not an assertion that polymer and ceramic processing physics are interchangeable or that either publication's research team is involved in this project.

---

## 1. Research objective and motivation

Modern computational tools can screen many candidate materials before the corresponding physical samples can be made and tested. The consequential research challenge is not only predictive speed: it is maintaining the scientific meaning, traceability and validation status of each proposed material and its associated evidence.

For a materials-discovery decision to be defensible, a predicted property must remain linked to the **composition and structural representation used, the reference calculations or measurements, the physical assumptions of those methods, the training data and validation design, and the available evidence of actual materials processing and performance**. A technically complete machine-learning table does not necessarily constitute a scientifically complete materials record.

This repository will develop a reproducible data-curation and workflow-engineering pipeline for **BaTiO₃-based ceramic compositions**. It will establish a traceable evidence pathway from the original supplementary spreadsheets to standardised scientific records, first-principles results, material descriptors and, if warranted, independently evaluated machine-learning predictions.

**Central research question**

> How can published BaTiO₃ computational data be converted into a scientifically interpretable, auditable and reproducible evidence layer that supports robust materials analysis, appropriately constrained AI-based screening and eventual integration with experimental validation?

### Specific objectives

1. **Preserve scientific provenance:** link every curated value to its original file, worksheet, row and documented computation or definition.
2. **Represent chemistry correctly:** distinguish nominal composition, spreadsheet coefficients, crystal-site descriptors, computational assumptions and unresolved interpretations.
3. **Establish reliable scientific data quality:** audit source structure, missingness, duplicate identities, consistency, units, numerical plausibility and the status of failed or unavailable results.
4. **Validate the computational evidence chain:** reconcile the descriptors and calculated energies across the supplementary sheets with explicit composition identifiers.
5. **Prepare materials-informed ML inputs:** verify feature construction, document transformations, prevent target leakage and evaluate chemical-domain generalisation.
6. **Constrain candidate design:** distinguish mathematically admissible compositions from computationally evaluated, predicted, experimentally tested and application-validated materials.
7. **Specify pathways to future physical validation:** design appropriate, clearly *proposed* metadata structures for fabrication, characterisation, long-term reliability and human review.
8. **Deliver reproducible software:** create transparent Python notebooks, reusable validation functions, data dictionaries, quality-control reports and documented execution requirements.

The sequence deliberately prioritises **scientific evidence and data reliability before predictive modelling**. AI benchmarking is an optional downstream phase, not a substitute for scientific validation.

## 2. Scientific context: composition, processing and materials properties

A recurring difficulty in materials informatics is deciding whether the selected representation contains the information that actually controls the property of interest. For some quantities, chemical structure or composition provides a useful first approximation. For others, **processing conditions, microstructure, specimen state, measurement protocol and observation timescale** can materially change the answer. A robust representation must also distinguish information available at design time from information available only after synthesis, processing or measurement.

This distinction is well illustrated by process-sensitive polymers and soft matter. Polymer structure-based descriptors do not necessarily capture **sequence, tacticity, molar-mass distribution, chain architecture or process history**. This is especially important for condition-sensitive quantities such as glass-transition temperature (**Tg**) and modulus. Thermoplastic properties may further depend on **melt viscosity, shear thinning, chain scission, crystallisation, cooling rates and repeated thermal or mechanical processing**. Small- and large-amplitude oscillatory shear, capillary rheometry and calorimetry probe different aspects of those behaviours. In supramolecular hydrogels, **water content, reversible physical associations, gelation kinetics, network topology, preparation history and ageing** can influence stiffness, swelling and release. Rheological quantities such as storage modulus **G′**, loss modulus **G″** and **tan δ**, together with structural and application-specific measurements, cannot be inferred reliably from a molecular formula alone.

The transferable scientific principle is **representation adequacy**: records should preserve the variables and measurement conditions needed to interpret a particular property. It is not a proposal to apply polymer-specific rheological laws to ceramic oxides.

For **ceramic oxides**, analogous information requirements arise through different physical mechanisms. Chemical substitution and crystal-site occupancy influence local bonding, structural distortion and polar behaviour, while **phase formation, defects, grain size, density, porosity, sintering history, electrode configuration and testing conditions** may determine the properties of a fabricated capacitor. The present source workbook provides **computational composition, descriptor and energy information**; it does not provide a traceable database of manufactured ceramic specimens. A future experimental extension would therefore need additional data rather than inferred processing histories.

### Crystal chemistry and computational representation

BaTiO₃ belongs to the `ABO₃` perovskite family. In the nominal investigated formula, **Ba, Sr and La occupy the A-site composition space**, **Ti describes the B-site chemistry**, and oxygen forms the anion sublattice. Replacing Ba²⁺ with Sr²⁺ or La³⁺ changes the chemical and electronic context; La substitution introduces questions about charge compensation that must be handled consistently with the specific computational model. Nominal formula constraints alone do not establish an experimental defect mechanism.

The published research uses **density functional theory (DFT)**, including a **virtual crystal approximation (VCA)** treatment, to calculate reference formation energies and related properties. DFT-derived values are outputs of a specified approximate quantum-mechanical calculation. They are distinct from **ML surrogate predictions**, which approximate relationships learned from labelled calculations, and from **physical measurements**, which require actual specimens and test protocols. All three evidence classes will remain separately identified throughout the project.

Formation energy will be curated using its reported definition and **eV/atom** units, together with available reference-state and method information. Elastic, thermodynamic and polarisation-related quantities discussed in the source study will be documented as **separate scientific properties** where their underlying data and definitions can be verified. They will not be collapsed into an unsupported universal materials-performance score.

## 3. Source data and present evidence

### Source documents

| Source | Role in the project | Official link |
|---|---|---|
| Published BaTiO₃ research article | Scientific questions, DFT methods, feature construction, modelling and results | [Article DOI](https://doi.org/10.1063/5.0314819) |
| Supplementary information document | Formation-energy methodology, physical-property calculations, feature definitions and model settings | [Publisher supplementary collection](https://doi.org/10.60893/figshare.jap.c.8234602) |
| Supplementary Excel workbook, sheets `S1`–`S4` | Primary composition, descriptor and calculated-energy records for curation | [Publisher supplementary collection](https://doi.org/10.60893/figshare.jap.c.8234602) |
| Autonomous soft-matter discovery perspective | Research questions concerning information quality, physical reasoning, constrained design, processing and long-term validation | [Perspective DOI](https://doi.org/10.1002/marc.70420) |

### Phase 01-verified workbook inventory

The following worksheet dimensions were recorded during initial inspection and **reconfirmed by the completed Phase 01 executable workbook audit**. This is structural verification, not independent reproduction of the published first-principles calculations.

| Worksheet | Data rows | Columns | Preliminary interpretation |
|---|---:|---:|---|
| `S1` | **30,301** | 100 | Candidate composition and descriptor space; not 30,301 independently calculated DFT targets |
| `S2` | **231** | 102 | Composition fields, descriptors, final energies and formation-energy labels |
| `S3` | **231** | 82 | Retained machine-learning input descriptors |
| `S4` | **231** | 10 | Composition, reported calculation method and structure labels, and energy records |

The executed Phase 01 audit confirms **231 unique composition keys** in each of `S2`, `S3` and `S4`, with compatible composition identities. The 18,018 declared comparable descriptor values (`S2`/`S3`) and 462 declared comparable energy values (`S2`/`S4`) showed no mismatches within the notebook's documented tolerances. No empty cells or duplicate composition keys were reported in the populated worksheet ranges. These remain **structural and cross-sheet observations**, not proof of DFT convergence, physical validity or model generalisation. See the reproducible audit outputs linked above.

The published study describes **100 initial material features** and **82 retained model inputs**, after exclusion of 16 invariant features and two non-input fields (a descriptive final-energy field and the formation-energy target). The 231 labelled records and 30,301 candidate records will remain distinct populations, with separate evidence-status definitions.

### Priority chemical-interpretation question

The nominal composition is **(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃**, with nominal A-site substitution bounds **x ≥ 0, y ≥ 0 and x + y ≤ 1**.

The completed Phase 01 audit confirms `Ba + Sr + La ≈ 1` for the 231 labelled compositions, while the **tabulated Ti coefficient** follows `Ti = 1 − La/2`; 210 entries have tabulated Ti values below 1. The main paper describes the nominal TiO₃ formula and states that explicit Ti or oxygen vacancies were **not introduced** in the specified first-principles calculations.

This requires **scientific reconciliation of source encoding and modelling assumptions**, not automatic data correction. The workflow will retain separate fields for the original coefficients, nominal representation, calculated diagnostic relationships and interpretation status. It will **not** infer actual Ti vacancies, alter the source values or assert charge-compensation mechanisms from a spreadsheet pattern alone.

That issue is a practical example of why data curation in materials science involves chemical interpretation, not simply correcting missing values and column formats.

## 4. Research strategy: a trustworthy materials-evidence workflow

The architecture follows four connected research needs: **scientific memory, physically grounded computation, constrained materials design and credible physical validation**. Each is implemented only to the level supported by the available data.

### 4.1 Scientific memory: complete metadata, provenance and quality control

A useful scientific database must retain more than a composition and a number. It needs the origins, methods, conditions, transformations and limitations that make the number interpretable. Particularly important are **unreported information, genuinely failed attempts, unsuccessful outcomes and ambiguous scientific associations**. Excluding or misclassifying such cases can introduce selection bias into downstream analysis.

**Project response**

- Maintain an immutable source registry: publication DOI, download location, source version, acquisition date, file size, SHA-256 checksum and redistribution-review status.
- Preserve source-level identity: original filename, sheet, row, column/header, formula or cached value, and stable source-record identifier.
- Define material and computation records with explicit composition, structure, computational method, reported energy, unit, descriptor source and evidence class.
- Build a descriptor dictionary covering **A-/B-site relevance, elemental meaning, weighting/aggregation rule, units, allowed values and source references**, including the 82 selected modelling inputs.
- Create a quality-control register for invalid or ambiguous values, duplicate keys, unit conflicts, source discrepancies, unresolved mappings and scientifically reviewable anomalies.
- Represent **candidate-only, DFT-calculated, ML-predicted, experimentally observed, documented failed and unknown** states explicitly. An unlabelled candidate is **not** evidence of a failed calculation or synthesis.
- Preserve raw observations; any standardisation or filtering will be recorded as a new, reproducible transformation rather than an undocumented change to a source file.

**Why it matters.** A formation-energy prediction may look precise but become unusable if its target, units, DFT assumptions or chemical identity cannot be reconstructed. A traceable database makes errors identifiable, supports reanalysis and provides a reliable starting point for later physical work.

**Expected artefacts:** `source_registry.csv`, `source_manifest.json`, `workbook_inventory.csv`, `data_dictionary.csv`, `descriptor_dictionary.csv`, `qc_findings.csv`, `evidence_status_dictionary.csv` and provenance-link tables.

### 4.2 Physical reasoning: traceable DFT references and validated ML surrogates

Fast surrogate models can be valuable when they approximate a costly physical calculation within a **specified validity domain**. However, model accuracy on nearby compositions is not equivalent to accuracy on unfamiliar chemistries, nor does agreement with DFT establish experimental performance. A reliable computational workflow therefore links predictions to the *actual reference method* and makes extrapolation visible.

**Project response**

- Maintain distinct fields for `reference_formation_energy_eV_atom`, `independent_prediction_eV_atom`, `prediction_residual_eV_atom`, `calculation_method`, `model_run_id` and `validation_split_id`.
- Reconcile the 231 labelled composition records and energy values between `S2` and `S4` by explicit scientific keys, not assumed row order.
- Reconstruct the feature inventory: explain the transition from 100 candidate features to 82 model inputs; check constants, correlated descriptors, physical definitions and inadvertent target-derived inputs.
- Confirm exact `S2`–`S3` linkage for the 82 retained features and preserve an explicit feature-exclusion manifest.
- Investigate data leakage, near-duplicate compositions and split-sensitive processing. Any learned transformation, imputation or feature selection for a new experiment must be fitted on the training partition alone.
- Where justified, benchmark simple regressors and selected tree/ensemble methods, using **MAE, RMSE, R², residual analysis, declared units and recorded seeds**. Report ordinary splits alongside feasible **held-out composition-region** tests in the Sr/La design space.
- Measure how far each screened candidate lies from the available labelled chemistry, and flag out-of-domain estimates rather than extrapolating without qualification.
- Specify, as a *future capability only*, how uncertain predictions could be submitted for additional high-fidelity calculations and subsequently recorded as new evidence.

The physical reasoning here is distinct from polymer simulations of viscoelastic flow, cooling and crystallisation. What transfers is the need to **tie a fast approximation to an identified physical reference and periodically reassess its validity**. The present repository cannot run a live closed-loop DFT service using the supplementary workbook alone.

**Expected artefacts:** `calculation_provenance.csv`, `feature_exclusion_manifest.csv`, `feature_linkage_checks.csv`, `leakage_audit.csv`, `split_plan.json`, `ml_readiness_report.md` and, if the evidence permits modelling, `benchmark_results.csv`, `prediction_audit.csv` and `model_card.md`.

### 4.3 Materials design: composition constraints and evidence-aware screening

Materials design should not rank candidates solely by a favourable predicted value. The candidate must be chemically defined, compatible with the modelling domain and appropriately assessed against physical or processing constraints. Predicted formation energy offers **one computational consideration** in materials design, not a demonstration of phase-pure synthesis, stable manufacturing or capacitor reliability.

**Project response**

- Validate the nominal A-site fraction constraints `x ≥ 0`, `y ≥ 0` and `x + y ≤ 1`, plus non-negativity and any verified bounds of the published candidate search space.
- Track the original Ba, Sr, La, Ti and O coefficients separately from a constructed nominal formula; retain the Ti–La interpretation issue for scientific review.
- Check descriptor completeness and model-input compatibility before assigning estimates to previously unlabelled candidates.
- Distinguish records that are **proposed compositions**, **reported first-principles calculations**, **independent ML predictions** and **documented experimental materials**. Advancing to a stronger evidence category requires new supporting records.
- Treat charge-compensation assumptions, structural phase, polarisation behaviour, energy barriers, mechanical properties, dielectric performance and synthesising conditions as separate constraints or evidence types.
- Produce candidate lists with explicit model version, predicted target and units, domain flag, source coverage and human-review status; avoid unsupported “best material” rankings.

A processability-aware screen can be specified for future use, but it cannot be operationally populated with **sintering yield, deposition conditions, microstructure or electrical measurements** unless those data are genuinely available.

**Expected artefacts:** `candidate_registry.csv`, `composition_validation.csv`, `composition_representation_review.csv`, `candidate_constraints.json` and conditional `candidate_screening.csv`.

### 4.4 Physical execution and characterisation: a carefully bounded data interface

Materials discovery must eventually connect a proposed composition to **a real processing route, a particular physical specimen and a measured property**. In process-sensitive thermoplastics, viscous melt flow, shear history and cooling can determine final morphology; in supramolecular hydrogels, assembly and preparation history shape the observed network state. Similar data-engineering discipline is needed in ceramics, although their mechanisms and experimental protocols differ.

For ceramic oxides, future physical records might include precursor lots and purity, powder preparation, milling, calcination, sintering temperature/time/atmosphere, coating or thin-film deposition settings, heating/cooling profiles, phase identification, grain size, density, porosity, electrode configuration, dielectric testing and instrument calibration. **These are prospective metadata requirements, not measurements found in the current workbook.**

**Project response**

- Design an **optional experimental extension** with `experimental_batch`, `specimen`, `processing_step`, `instrument_run`, `calibration`, `measurement`, `quality_event` and `failure_log` entities.
- Require separate identifiers for computational compositions/calculations and physical specimens. Matching chemical formulae do not establish sample identity.
- Distinguish intended process settings from observed conditions, original instrument files from processed measurements, and successful outcomes from recorded aborted or failed operations.
- Specify machine-readable protocol identifiers, source timestamps, units, calibration references, structured event logs, exception handling and decision audit trails.
- Include human review when a future model recommendation might influence physical experimentation.

The present project will **document the interface and validation rules**; it does not claim robotic laboratory control, experimental characterisation or access to research instruments.

**Expected artefacts:** `experimental_schema_proposal.md`, `specimen_linkage_rules.md`, `measurement_metadata_template.csv` and `instrument_event_schema.json`.

## 5. Two persistent research limits: time and physical processability

Reliable data engineering can reduce avoidable errors and support more efficient research decisions. It does not eliminate the physical constraints that govern actual materials behaviour.

### 5.1 Slow properties, ageing and mechanism-aware validation

A short test or a fast prediction is not automatically a substitute for long-duration performance. For polymers, this concern includes **creep, stress relaxation, degradation, repeat-processability, molecular or network ageing and biological response**. Accelerated approaches such as **time–temperature superposition and WLF/Arrhenius-based treatments** depend on appropriate mechanisms and valid temperature or stress regimes; morphological transitions, chemical changes and nonlinear responses can invalidate straightforward extrapolation.

For ceramic capacitors, future research may require **dielectric ageing, electrical fatigue, breakdown testing, thermal cycling and long-term device reliability**. These cannot be inferred from the supplied DFT formation-energy table.

The project will specify a future `long_horizon_validation` record with specimen identity, property, stressor, protocol, actual duration, time series, uncertainty, mechanistic assumptions and validated extrapolation domain. It will distinguish **direct observation**, **validated accelerated testing**, **unvalidated proxy** and **model extrapolation**. The fields remain unpopulated where source evidence does not exist.

### 5.2 The execution gap and processing-dependent physics

Physical automation introduces constraints that are not visible in a composition-only dataset: flow behaviour, material handling, equipment condition, fouling, thermal gradients, batch variability, instrument response and scale effects. Non-dilute polymer solutions and melts can exhibit **non-Newtonian viscosity, yield-stress behaviour, elastic recoil and shear-induced structural changes**; ceramics processing can instead involve **powder flow, slurry rheology where relevant, sintering shrinkage, defect control, grain development, phase purity and furnace or deposition uniformity**.

The project addresses these limits by specifying **route-specific process metadata and decision provenance**, not by claiming that any physical bottleneck is solved. Potential research automation must preserve human accountability, process safety, instrument state and the distinction between a proposed action and a verified outcome. Demonstration at laboratory scale would also not, without further evidence, establish manufacturing-scale reliability.

## 6. Evidence architecture and scientific data model

The planned pipeline separates evidence levels while providing explicit, inspectable links:

```text
Original publication and supplementary files
    ↓  source identifier, file hash, worksheet/cell coordinates
Immutable source record and scientific metadata
    ↓  verified composition mapping and original coefficients
Material composition and computational representation
    ↓  method, structural assumption, target definition, units
Reported DFT reference calculation
    ↓  validated descriptor definitions and composition-level linkage
Analysis-ready features and targets
    ↓  documented splitting, modelling and evaluation (optional)
Independent ML prediction with applicability and uncertainty flags
    ↓  future extension only; requires new supporting evidence
Physical processing record → identified specimen → measurement
    ↓  additional experimental programmes and observation time
Long-duration validation / performance decision
```

No link is created merely because two records occupy the same row number or have similar filenames. Proposed future entities do not imply that corresponding experimental data have been collected.

### Proposed core records

| Entity | Essential information | Scientific purpose |
|---|---|---|
| `source_record` | source ID, DOI, file hash, sheet, original cell/row, header, raw value | Trace every output back to its origin |
| `composition` | composition ID, original Ba/Sr/La/Ti/O coefficients, nominal formula, interpretation status | Preserve chemical identity and unresolved representation questions |
| `calculation` | calculation ID, composition ID, reported method/structure, target, value, unit, evidence status | Distinguish physical computation from prediction and experiment |
| `descriptor_definition` | feature name, physical meaning, site, calculation/weighting rule, unit, source | Make ML inputs scientifically interpretable |
| `feature_matrix` | composition ID, validated descriptor values, version, linkage checks | Connect correct input vectors to labelled targets |
| `qc_finding` | rule, affected record, severity, evidence, reviewer disposition | Ensure issues are documented rather than silently removed |
| `model_run` *(conditional)* | inputs, split, hyperparameters, random seed, metrics, residuals, model version | Reproduce independently generated predictions |
| `experimental_record` *(future only)* | batch, specimen, processing conditions, instrument, measurement, protocol | Permit later physical validation without fabricating data |

### Data-quality and evidence policies

- Preserve the original workbook and the precise source-to-output lineage.
- Keep **unknown, not measured, not attempted and documented failure** as distinct states.
- Do not promote a candidate to an experimentally proven material without a traceable experiment.
- Use units, method labels and reference definitions in every quantitative comparison.
- Keep anomalous or chemically ambiguous records available for scientific review rather than erasing them.
- Identify whether an artefact is **source data**, a **verified transformation**, a **statistical prediction**, an **experimental observation**, or a **future schema proposal**.

## 7. Implementation roadmap — Phases 00–09

The staged plan delivers scientific data reliability first, followed by analysis and optional machine-learning extensions. **Phase 00 is complete and published; Phase 01 has completed its local audit and its public-release files are prepared. Phases 02–09 remain planned or conditional.**

| Phase | Research purpose and implementation | Expected outputs and completion criterion |
|---|---|---|
| **00 — Research scope and source registry** | Register publication and supplementary file identifiers, licence status, acquisition details, SHA-256 hashes, scientific scope and evidence types. | `source_registry.csv`, `source_manifest.json`, `research_scope.md`. Files are identifiable, versioned and unaltered. |
| **01 — Workbook and computational-data audit** | Inventory `S1`–`S4`, worksheet formulas, headers, cell types, missingness, duplicates, composition keys and shared S2/S3/S4 values; document ambiguities and initial Ti–La findings. | `workbook_inventory.csv`, `column_inventory.csv`, `source_audit_report.md`, exception log. Every observation has a source location. |
| **02 — Scientific schema and data dictionary** | Model compositions, crystal-site information, descriptors, calculation provenance, evidence status and QC relationships. | `schema_design.md`, `data_dictionary.csv`, `descriptor_dictionary.csv`. Every curated field has semantics, unit where relevant, source and missingness policy. |
| **03 — Chemical consistency and quality control** | Validate A-site fractions, numeric ranges, identity uniqueness, composition-representation discrepancies and target-field consistency without modifying raw data. | `composition_validation.csv`, `qc_findings.csv`, `composition_representation_review.md`. Issues are explicit and reviewable. |
| **04 — Standardisation and feature documentation** | Produce consistent typed values, preserve original coefficients and target units, reconcile the 100-to-82 descriptor pipeline, and record all transformations. | `composition_standardised.csv`, `feature_dictionary.csv`, `feature_exclusion_manifest.csv`, `transformation_log.csv`. Source values remain recoverable. |
| **05 — Record linkage and evidence layer** | Join S2, S3 and S4 by verified composition identities; test feature and energy equality; report missing or conflicting joins; assemble only scientifically supported records. | `linkage_summary.csv`, `linkage_exceptions.csv`, conditional `analysis_ready_evidence.csv`. No implicit row-order matching. |
| **06 — Exploratory materials-informatics analysis** | Explore Sr/La domain coverage, labelled versus candidate populations, formation-energy distribution, descriptor correlations and chemically notable trends. | `eda_summary.md`, documented figures. All plots identify evidence class, units, sample counts and coverage limitations. |
| **07 — ML readiness and generalisation strategy** | Test feature–target linkage, leakage, redundancy, split design, chemical-neighbour similarity and potential distribution shift. | `ml_readiness_report.md`, `leakage_audit.csv`, `split_plan.json`. Validation design and data restrictions are defensible before model training. |
| **08 — Optional predictive modelling and screening** | Train transparent baselines and selected regressors, compare residuals under declared splits, and screen candidates only within documented descriptor and applicability constraints. | Conditional `benchmark_results.csv`, `prediction_audit.csv`, `model_card.md`, `candidate_screening.csv`. Predictions remain distinct from DFT and experimental results. |
| **09 — Workflow engineering, testing and release** | Consolidate deterministic extraction, stable paths, scripts, dependency management, assertions, manifests and clean-run verification. | `requirements.txt`, reproducibility instructions, automated tests and `run_manifest.json`. A clean environment reproduces all declared outputs. |

### Practical implementation sequence

**Immediate priority: publish the reviewed Phase 01 artefacts and begin Phase 02 scientific schema/data dictionary design.** The source registry and workbook audit are complete, and the unresolved candidate-space and Ti–La representation questions must remain visible during schema development. Optional modelling follows scientific validation; advanced experimental integration remains a separate future workstream.

## 8. Repository organisation and future structure

The **implemented/publication-ready files** are currently organised as follows. Phase 01 links become active after the corresponding commits; the larger development tree below is a separate *target* layout.

```text
Project_Machine_learning_and_first-principles_guided_desig/
├── README.md
├── BaTiO3_Phase00.ipynb
├── BaTiO3_Phase00.html
├── BaTiO3_Phase01.ipynb               # Phase 01: upload publication-safe copy
├── BaTiO3_Phase01.html                # Phase 01: upload public-safe HTML
├── docs/
│   └── research_scope.md
├── manifests/
│   ├── source_registry.csv
│   └── source_manifest.json
└── reports/
    ├── registration_findings.md
    └── phase01/
        ├── source_audit_report.md
        ├── workbook_inventory.csv
        ├── column_inventory.csv
        ├── formula_inventory.csv
        ├── cross_sheet_checks.csv
        └── qc_findings.csv
```

### Longer-term target structure

```text
Project_Machine_learning_and_first-principles_guided_desig/
├── README.md
├── .gitignore
├── requirements.txt                 # Finalise against executed code
├── notebooks/
│   ├── 00_scope_and_source_registry.ipynb
│   ├── 01_source_data_audit.ipynb
│   ├── 02_materials_schema_design.ipynb
│   ├── 03_composition_and_data_qc.ipynb
│   ├── 04_standardisation_and_feature_dictionary.ipynb
│   ├── 05_provenance_and_record_linkage.ipynb
│   ├── 06_exploratory_materials_analysis.ipynb
│   ├── 07_ml_readiness_and_leakage_audit.ipynb
│   ├── 08_optional_ml_benchmarks_and_screening.ipynb
│   └── 09_reproducibility_and_release.ipynb
├── src/                             # Reusable, tested extraction and QC logic
├── data/
│   ├── raw/                         # Local source files; excluded from Git until rights verified
│   ├── interim/                     # Audited working records
│   └── processed/                   # Permissible, validated derived outputs
├── docs/
│   ├── data_dictionary.csv
│   ├── schema_design.md
│   ├── descriptor_dictionary.csv
│   └── composition_representation_review.md
├── reports/
│   ├── qc/
│   └── figures/
├── manifests/
│   └── source_manifest.json
└── tests/
```

The directory tree is a **target structure**, not a claim that these notebooks and files are already implemented. Each artefact will be added as its corresponding phase is completed.

## 9. Reproducibility, scientific limitations and responsible reuse

### Reproducibility standards

- Use an immutable raw-data copy and source hashes, with no manual edits to publisher files.
- Capture original spreadsheet coordinates and source versions in all derived tables.
- Apply deterministic transformations and versioned schemas; distinguish source data from generated outputs.
- Record Python/package versions, random seeds, split membership, configuration and model settings where relevant.
- Make validation failures visible in both machine-readable logs and concise scientific reports.
- Confirm that each published summary and figure can be regenerated from controlled inputs.
- Require independent review for unresolved chemical interpretations, unexpected data patterns and extrapolative model claims.

### Scope and evidence limitations

The available materials support a substantial **computational data-curation and workflow-engineering project**. They do **not** alone demonstrate that the proposed ceramics were synthesised, that a self-driving laboratory was operated, that any particular calculation or experiment failed, or that long-term dielectric performance was measured. Proposed experimental schemas, instrument integrations and model-driven calculation requests are **design specifications**, not operational results.

A DFT-based formation-energy workflow may help organise candidate research, but it does not replace **phase and defect analysis, controlled processing, physical characterisation, durability testing or deployment validation**. These steps require appropriate additional data and experimental work.

### Research attribution and data rights

The research publications, calculations, figures and supplementary files remain attributable to their original contributors and rights holders, identified in the linked journal records. The ceramic article is described as **CC BY 4.0 except where otherwise noted**; supplementary data may have distinct terms. Before redistributing any original workbook, figure or substantial source extract, the applicable licence and permissions must be verified. The repository should otherwise link to the official sources and publish independently written code, documentation and permissible derived outputs.

This is an **independent research and professional portfolio project**, not an institutional research appointment, official collaboration, endorsement or claim of access to private laboratory systems.

## 10. Current status and next milestone

| Workstream | Current status |
|---|---|
| Main ceramic paper, supplementary information and research-framework review | **Reviewed for project scoping** |
| S1–S4 sheet inventory and preliminary 231-record cross-sheet comparisons | **Reproduced in Phase 01; reports prepared for publication** |
| Ti–La composition representation question | **Identified and retained for scientific review** |
| Phase 00 source registry, manifest, research scope and registration findings | **Completed and published** |
| Phase 01 workbook audit and automated QC | **Completed locally; publication-ready audit artefacts prepared** |
| Canonical schema, full chemical validation, standardised exports and evidence layer | **Planned** |
| Independent ML validation, benchmarking and candidate screening | **Conditional; not yet executed** |
| Experimental processing, robotics and long-term performance validation | **Outside the present dataset and project scope** |

**Next milestone:** publish the Phase 01 notebook, executed report and reviewed metadata summaries; reconcile the candidate-space and Ti–La assumptions with source methodology; then develop the Phase 02 scientific schema and data dictionaries before any standardisation or new predictive modelling.

---

## References

**Primary ceramic research and computational dataset**  
**[*Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications*](https://doi.org/10.1063/5.0314819)**. *Journal of Applied Physics* **139**, 064101 (2026).  
[Official supplementary materials and datasets](https://doi.org/10.60893/figshare.jap.c.8234602).

**Research framework for trustworthy and process-aware materials discovery**  
**[*Predicting Faster Than We Can Make: Polymer-Specific Process Physics as a Frontier for Autonomous Soft-Matter Discovery*](https://doi.org/10.1002/marc.70420)**. *Macromolecular Rapid Communications* (2026).

*Full publication metadata and complete author lists are provided by the original journal DOI records.*





