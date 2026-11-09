# BaTiO₃ Materials Data Curation and AI-Ready Workflow Engineering

## Quick navigation — Phase 00 publication

The following Phase 00 artefacts are published in the repository. Links are relative to the `main` branch and use the current file paths. **Phase 00 covers source registration and evidence boundaries; the Phase 01 workbook audit has not yet been completed.**

- [Repository home](./)
- [Phase 00 — executable Jupyter notebook](./BaTiO3_Phase00.ipynb)
- [Phase 00 — scientific HTML report](./BaTiO3_Phase00.html)
- [View Phase 00 HTML report in a browser (external preview)](https://htmlpreview.github.io/?https://github.com/tehsongxuan/Project_Machine_learning_and_first-principles_guided_desig/blob/main/BaTiO3_Phase00.html)
- [Phase 00 — research scope](./docs/research_scope.md)
- [Phase 00 — source registry (CSV)](./manifests/source_registry.csv)
- [Phase 00 — source manifest (JSON)](./manifests/source_manifest.json)
- [Phase 00 — registration findings](./reports/registration_findings.md)
- [Project implementation roadmap — Phases 00–09](#7-implementation-roadmap--phases-0009)

**Publication scope:** The notebook and outputs document provenance checks, file integrity and the boundary between registration and scientific validation. They do not establish that the DFT calculations, composition encodings or predictive models are independently validated. The original supplementary PDF, DOCX and XLSX files are intentionally not re-hosted here; they are linked to their official publisher sources in the research-foundation and source-data sections below. The external HTML preview is a third-party service, and will display correctly only if the uploaded HTML is a valid rendered export.

---

**An independent research-data engineering project for reproducible, chemistry-aware materials informatics**

**Material system:** Sr/La-substituted barium titanate, nominally `(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`  
**Research methods:** Solid-state chemistry · First-principles calculations · Scientific data curation · Data engineering · Machine-learning validation · Reproducible Python workflows  
**Project status:** Phase 00 source registration, integrity checks and research-scope documentation are complete. Preliminary workbook and cross-sheet observations have been recorded. The comprehensive Phase 01 workbook audit, chemical validation and independent modelling remain outside the completed Phase 00 scope.

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

### Preliminary workbook inventory

The following findings originate from an **initial inspection** of the supplied workbook, not yet from the complete, publicly executable audit planned for Phases 00–01.

| Worksheet | Data rows | Columns | Preliminary interpretation |
|---|---:|---:|---|
| `S1` | **30,301** | 100 | Candidate composition and descriptor space; not 30,301 independently calculated DFT targets |
| `S2` | **231** | 102 | Composition fields, descriptors, final energies and formation-energy labels |
| `S3` | **231** | 82 | Retained machine-learning input descriptors |
| `S4` | **231** | 10 | Composition, reported calculation method and structure labels, and energy records |

Initial checks indicate **231 unique composition keys** in each of `S2`, `S3` and `S4`, with compatible composition identities; shared `S2`/`S3` feature values and the `S2`/`S4` reported energy values agree in the preliminary comparisons. No empty cells in the inspected populated ranges or exact duplicate complete records were found. These are **structural observations**, not proof of DFT convergence, physical validity or model generalisation. They will be independently reproduced, logged and exposed to inspection in the implementation.

The published study describes **100 initial material features** and **82 retained model inputs**, after exclusion of 16 invariant features and two non-input fields (a descriptive final-energy field and the formation-energy target). The 231 labelled records and 30,301 candidate records will remain distinct populations, with separate evidence-status definitions.

### Priority chemical-interpretation question

The nominal composition is **(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃**, with nominal A-site substitution bounds **x ≥ 0, y ≥ 0 and x + y ≤ 1**.

In the initial workbook inspection, `Ba + Sr + La = 1` for the 231 labelled compositions, while the **tabulated Ti coefficient** follows `Ti = 1 − La/2`; 210 entries have tabulated Ti values below 1. The main paper describes the nominal TiO₃ formula and states that explicit Ti or oxygen vacancies were **not introduced** in the specified first-principles calculations.

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

The staged plan delivers scientific data reliability first, followed by analysis and optional machine-learning extensions. **Phase 00 outputs are published above; the remaining phases and outputs are planned unless explicitly identified as completed.**

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

**Immediate priority: Phases 00–01.** Establish source integrity and reproduce the preliminary structural and 231-record linkage observations in a standalone notebook or script. Subsequent stages should proceed only once source semantics and exception handling are documented. Optional modelling follows scientific validation; advanced experimental integration remains a separate future workstream.

## 8. Planned repository structure

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
| S1–S4 sheet inventory and preliminary 231-record cross-sheet comparisons | **Preliminary checks performed; public reproducible audit pending** |
| Ti–La composition representation question | **Identified and retained for scientific review** |
| Phase 00 source registry, manifest, research scope and registration findings | **Completed and published** |
| Phase 01 workbook audit and automated QC | **Planned; not yet executed** |
| Canonical schema, full chemical validation, standardised exports and evidence layer | **Planned** |
| Independent ML validation, benchmarking and candidate screening | **Conditional; not yet executed** |
| Experimental processing, robotics and long-term performance validation | **Outside the present dataset and project scope** |

**Next milestone:** develop the Phase 01 executable workbook audit, reproduce the S1–S4 workbook inventory and explicit S2/S3/S4 consistency checks, and publish a transparent findings register before beginning data standardisation or predictive modelling.

---

## References

**Primary ceramic research and computational dataset**  
**[*Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications*](https://doi.org/10.1063/5.0314819)**. *Journal of Applied Physics* **139**, 064101 (2026).  
[Official supplementary materials and datasets](https://doi.org/10.60893/figshare.jap.c.8234602).

**Research framework for trustworthy and process-aware materials discovery**  
**[*Predicting Faster Than We Can Make: Polymer-Specific Process Physics as a Frontier for Autonomous Soft-Matter Discovery*](https://doi.org/10.1002/marc.70420)**. *Macromolecular Rapid Communications* (2026).

*Full publication metadata and complete author lists are provided by the original journal DOI records.*




