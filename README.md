# BaTiO₃ Ceramic Materials Data Curation and AI-Ready Workflow Engineering

**Repository:** `Project_Machine_learning_and_first-principles_guided_desig`  
**Research focus:** Materials informatics · Solid-state chemistry · Scientific data curation · Computational provenance · Quality assurance · Reproducible Python workflows  
**Material system:** Sr/La-substituted barium titanate, nominally `(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`  
**Project type:** Independent scientific computing and research-data engineering portfolio  
**Status — 4 November 2026:** Source acquisition, document review and preliminary workbook/linkage checks completed. Executable phase notebooks, full validation and independent modelling are **not yet completed**.

> **Research objective:** Establish a traceable, scientifically checked evidence pipeline connecting original source cells, ceramic compositions, computational calculations, elemental descriptors and optional machine-learning predictions. The longer-term aim is to support reliable, physics-aware materials-design decisions without conflating computational screening, experimental fabrication and validated device performance.

---

## Contents

1. [Project overview and scientific motivation](#1-project-overview-and-scientific-motivation)
2. [Research sources, attribution and data rights](#2-research-sources-attribution-and-data-rights)
3. [Source data and preliminary findings](#3-source-data-and-preliminary-findings)
4. [Scientific foundations: ceramics, thermodynamics and data science](#4-scientific-foundations-ceramics-thermodynamics-and-data-science)
5. [Research framework across the eight-page perspective](#5-research-framework-across-the-eight-page-perspective)
6. [Detailed alignment with Section 5.1 and its four modules](#6-detailed-alignment-with-section-51-and-its-four-modules)
7. [Section 5.2: the two limits that an automated loop cannot remove](#7-section-52-the-two-limits-that-an-automated-loop-cannot-remove)
8. [Data model, scientific integrity and evidence classification](#8-data-model-scientific-integrity-and-evidence-classification)
9. [Implementation roadmap: Phases 00–09](#9-implementation-roadmap-phases-0009)
10. [Quality gates, reproducibility and repository structure](#10-quality-gates-reproducibility-and-repository-structure)
11. [Expected research contribution, boundaries and next steps](#11-expected-research-contribution-boundaries-and-next-steps)
12. [References and research independence](#12-references-and-research-independence)

## 1. Project overview and scientific motivation

This project develops a **reproducible scientific data-curation and workflow-engineering pipeline** for the published study **Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications** (2026). The source study uses first-principles calculations, feature engineering and regression models to screen Sr/La-substituted barium titanate compositions. Its aim is to identify promising computational composition regions and investigate selected structural, ferroelectric, mechanical and thermal properties relevant to capacitors.

The present project addresses a complementary research-infrastructure question:

**How can composition records, source calculations, materials descriptors and predictive outputs be curated into a reproducible, auditable evidence layer that a research team could confidently inspect, verify and extend?**

The project also examines how the research-infrastructure principles discussed in the 2026 perspective **[*Predicting Faster Than We Can Make: Polymer-Specific Process Physics as a Frontier for Autonomous Soft-Matter Discovery*](https://doi.org/10.1002/marc.70420)** can inform the curation of BaTiO₃ computational materials data. Particular attention is given to scientifically complete databases, physically informed simulation, process-aware materials design, and the traceability of experimental validation. This is an **independent methodological comparison across materials classes**, not a claim that the processing physics of polymers and ceramics are interchangeable or that the present work is part of the cited research programme.

### Research questions

1. Can the supplementary workbook's composition, descriptor and calculated-energy records be traced back to their exact source worksheets and cells?
2. Are formulae, A-/B-site fields, chemical fractions, methods, units and feature definitions scientifically consistent, or do they require explicit review?
3. Can the 231 reported DFT-labelled compositions be joined reproducibly across supplementary sheets without relying on row position?
4. Does the available metadata support leakage-aware modelling and scientifically defensible extrapolation to the wider 30,301-composition candidate space?
5. Which parts of a materials-discovery framework—**database, physical reasoning, constrained design and experimental evidence intake**—can be implemented with public computational data, and which require future laboratory evidence?
6. How can provenance, uncertainty, failure classification, long-horizon validation and researcher oversight be built into the workflow from the outset?

### Deliverable philosophy

The first priority is a **source-linked, scientifically validated computational dataset**. Model benchmarking is conditional on satisfactory data checks. Proposals for robotic fabrication, instrument integration or long-term performance testing remain labelled as future architecture rather than accomplished laboratory work.

## 2. Research sources, attribution and data rights

| Reference | Primary role | Access |
|---|---|---|
| **[C]** 2026 ceramic study, **Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications**, *Journal of Applied Physics* **139**, 064101 | Ceramic chemistry, methods, DFT/ML workflow, computational results | [DOI: 10.1063/5.0314819](https://doi.org/10.1063/5.0314819) |
| **[SI]** Supplementary information to [C] | Formation-energy formulae, elastic and phonon-based thermodynamics, descriptor definitions, model settings, comparison tables | [Official supplementary collection](https://doi.org/10.60893/figshare.jap.c.8234602) |
| **[X]** Supplementary Dataset.xlsx, worksheets S1–S4 | Primary tabular records for this independent curation exercise | [Official supplementary collection](https://doi.org/10.60893/figshare.jap.c.8234602) |
| **[P]** 2026 perspective, **Predicting Faster Than We Can Make: Polymer-Specific Process Physics as a Frontier for Autonomous Soft-Matter Discovery**, *Macromolecular Rapid Communications* | Research framework: prediction–production gap, process-sensitive data, autonomous workflow modules and limits | [Journal record](https://doi.org/10.1002/marc.70420) |

All eight printed pages of [P], the main ceramic article and the supplementary text were considered when preparing this plan. Sections and figure numbers below refer to the **published sources**, not figures generated by this project. The article author lists are available through the original publication records.

**Responsible reuse.** The ceramic article states that its article content is CC BY 4.0 except where otherwise noted. Rights attached to separately hosted supplementary files must be checked independently. This public repository should distribute original scripts, permissible validation summaries and documentation; the original workbook, paper PDFs and publisher figures should **not** be republished without confirming applicable permissions. Raw inputs should remain unchanged and be acquired from the official source links.

## 3. Source data and preliminary findings

### 3.1 Supplementary workbook inventory

The initial structural audit identified the following worksheets. **Counts below are source-file observations, not the results of a full scientific-data validation or DFT reproduction.**

| Sheet | Data rows | Columns | Observed content | Evidence boundary |
|---|---:|---:|---|---|
| **S1** | **30,301** | **100** | Composition/descriptor candidate space; formula-generated row index | Candidate entries are not 30,301 independent DFT calculations or synthesised materials. |
| **S2** | **231** | **102** | Compositions, descriptors, reported final energies and formation energies | Calculated labels require method and unit provenance; not experimental capacitor measurements. |
| **S3** | **231** | **82** | Selected machine-learning input features | Feature matrix alone is not a target table or validated test split. |
| **S4** | **231** | **10** | Compositions, `GGA-PBE(VCA)`, `P4mm`, and reported energy values | Contains selected computation descriptors, not complete electronic-structure input/output logs. |

Preliminary comparisons indicate **231 unique composition keys** shared by S2, S3 and S4; shared S2/S3 selected-feature values match, and the S2/S4 final- and formation-energy fields agree for the linked compositions. No exact duplicate complete records or empty cells were detected within the inspected populated ranges. These observations must be reproduced by the public Phase 01 audit before being promoted to final project findings. [X]

The published study describes a progression from **100 candidate material features** to **82 model inputs**, excluding 16 constant features, one descriptive final-energy feature and the formation-energy target. The model-ready matrix contains 231 rows, while a larger candidate space is screened using ML predictions. [C, pp. 4–5; SI, Table S1 and Figure S1]

### 3.2 Priority scientific review: nominal versus tabulated composition

The nominal material system is:

`(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`, subject to `x ≥ 0`, `y ≥ 0` and `x + y ≤ 1` for the nominal A-site fractions.

The preliminary spreadsheet inspection found `Ba + Sr + La = 1` across the 231 labelled entries, but the workbook's **tabulated Ti coefficient** follows `Ti = 1 − La/2`, with Ti below 1 in **210 of the 231 records**. The main article explains that its stated first-principles models did not explicitly introduce Ti- or O-vacancy charge-compensation defects. [C, p. 3; X]

**Curation response:** retain the original Ti field, define separate `nominal_formula`, `source_formula` and `Ti_tabulated` attributes, record the observed algebraic relationship as a QC review item and investigate the modelling convention. **Do not infer actual Ti vacancies, alter coefficients to match the nominal formula or claim a verified physical defect mechanism from the spreadsheet alone.** The article's discussion of electronic/VCA compensation and the spreadsheet representation must remain distinguishable.

### 3.3 Evidence categories

The workflow will distinguish at least:

- `candidate_only`: a composition/descriptor record without a supplied reference energy;
- `calculation_reported`: a DFT-related calculated energy is provided and attributable;
- `prediction_generated`: an independently produced ML estimate with model version and validation context;
- `experimental_result_documented`: physical synthesis or measurement supported by an actual experimental source;
- `failed_calculation_documented`: a failed computational attempt supported by a source log;
- `unknown`: provenance or status cannot yet be resolved.

**Absence of a DFT label is not evidence of a failed calculation or unsuccessful synthesis.** No genuine failure log should be created from unlabelled S1 rows.

## 4. Scientific foundations: ceramics, thermodynamics and data science

### 4.1 Ceramic chemistry and the formation-energy target

BaTiO₃ is a perovskite oxide, often described by an `ABO₃` crystal framework. In this composition family, Ba, Sr and La contribute to the nominal **A-site** composition; Ti occupies the B-site in the nominal formula; oxygen forms the anion framework. Sr and La substitutions change local chemical and electronic environments and are studied for their effects on polar order and dielectric behaviour. [C, pp. 1–4]

The study uses **density functional theory (DFT)** and a **virtual crystal approximation (VCA)**-related workflow to calculate formation energies for selected compositions. DFT estimates electronic-structure energies under specified physical approximations. VCA represents mixed-site substitution using averaged pseudopotential descriptions; the main paper also describes selected supercell calculations and associated electronic-compensation assumptions. Different computational routes should not be collapsed into a single undocumented method label. [C, p. 3; SI, Text S1]

Formation energy is defined relative to specified elemental reference states and a normalisation convention. The reported target is in **eV/atom**. A more negative value may be informative *within the stated reference and method*, but it does not alone establish phase purity, processability, long-term reliability, experimentally achieved dopant incorporation or capacitor performance.

The publication additionally investigates selected polarisation behaviour, Landau–Ginzburg–Devonshire (LGD) parameters, elastic anisotropy and thermodynamic properties. These are **separate physical quantities** with different calculation methods, units and levels of evidence. Supplementary material documents elastic quantities including bulk, shear and Young's moduli, and phonon-related thermal quantities such as entropy, enthalpy and heat capacity. [C, pp. 8–15; SI, Texts S2–S3 and Tables S4–S5]

### 4.2 Materials descriptors and modelling

The source study constructs elemental and site-specific descriptors using compositional weighting, including elemental attributes such as atomic/ionic radii, atomic weight, electronegativity, valence-related quantities and other tabulated properties. Correlated descriptors can become redundant; constant columns contain no discriminating information within the training population. [C, pp. 4–5; SI, Table S1]

The published modelling compares linear regression, support vector regression, multilayer perceptron, decision-tree regression, random forest and XGBoost. It reports a **4:1 training/test ratio**, MAE/RMSE/R² metrics and SHAP-based interpretation. The reported high predictive agreement is a result **from that study's evaluation design** and does not establish reliable extrapolation to every new chemical region. [C, pp. 5–8; SI, Tables S2–S3]

Independent benchmarking will therefore assess `feature → target` lineage, duplicate or near-neighbour composition leakage, preprocessing fitted on training folds, blocked composition-region splits where feasible, and uncertainty/out-of-distribution warnings before candidate screening.

### 4.3 Transferable concepts from polymer and soft-matter research

The perspective distinguishes **chemistry-dominated**, **condition-dependent** and **process-history-dependent** properties. These represent a hierarchy of what information a materials model must retain. [P, p. 3; Figure 2 on p. 4]

- **Chemistry-dominated behaviour:** Repeat-unit or molecular descriptors can capture substantial information for some intrinsic quantities. In ceramics, elemental composition and structure-related descriptors serve analogous *data-representation* functions, but describe different physics.
- **Condition-dependent behaviour:** Polymer **glass-transition temperature (Tg)** and modulus can depend on molecular mass, heating/measurement protocols and thermal history. Ceramic polar transitions, symmetry and calculated energetics likewise require well-defined conditions and structural assumptions; the corresponding physical mechanisms are different.
- **Process-history-dependent behaviour:** Semicrystalline morphology, melt strength, network organisation and degradation may require processing histories that cannot be reconstructed from a molecular string. For ceramics, analogous data-engineering questions concern powder preparation, thermal schedules, sintering, defects, grain structure, deposition history and device measurements—**only when such data actually exist**.

Polymer informatics features such as SMILES, RDKit descriptors and molecular fingerprints, and soft-matter measurements such as **storage modulus G′, loss modulus G″, tan δ, shear-rate-dependent viscosity and sol–gel transitions**, provide methodological precedents for careful feature definition, unit treatment and source linkage. They are not used as numerical substitute features for the present oxide dataset.

The unifying principle is **scientifically sufficient representation**: no model can condition on processing, structure, uncertainty or measurement conditions that the dataset does not record.

## 5. Research framework across the eight-page perspective

This section records the perspective's intellectual progression. **Page 5 is developed in depth in Sections 6–7 below**; the surrounding pages are retained because they explain why the modules are necessary and where their effectiveness ends.

| Printed page | Scientific argument and research emphasis | Implication for this repository |
|---|---|---|
| **1 — Abstract and opening** | Modern prediction and generative design are accelerating faster than the capacity to fabricate, process and validate some materials; the limiting step can lie in process physics and slow performance outcomes. | Prioritise scientifically complete data and evidence status, not only model accuracy. |
| **2 — Three waves of AI; prediction–production asymmetry** | Descriptor regression, learned representations and generative/autonomous design expand capability; validated data and physical experiments do not necessarily keep pace. Data-sparse unfamiliar regions create extrapolation risk. | Maintain the 231 DFT-labelled and 30,301 candidate populations separately; test domain coverage and blocked generalisation. |
| **3 — Three property regimes; two material cases** | Chemistry, measurement conditions and process history contribute differently to material behaviour. Thermoplastics depend on melt flow and thermal history; supramolecular hydrogels depend on aqueous assembly and network state. | Attach method/structure/condition metadata to ceramic energy records; design future processing and measurement schemas without treating polymers as ceramics. |
| **4 — Figures 2 and 3; autonomous-lab transition** | A representation hierarchy identifies missing measurements and metadata. Contrasting thermoplastic and hydrogel cases reveal different experimental bottlenecks and slow validation horizons. | Define a data dictionary and evidence-lineage hierarchy; separate model inputs, computed properties and future physical tests. |
| **5 — Section 5.1 and start of 5.2** | Four modules—**Database, Simulation, Generation, Synthesis/Manufacturing/Characterisation**—must interact around reliable informatics. Closed loops do not eliminate long-duration testing. | Core architecture for Phases 00–09; detailed implementation and quality gates in Section 6. |
| **6 — Figure 4 and continuation of 5.2** | Fast surrogate loops require slower, periodic high-fidelity checks; physical handling, scale-up, ageing mechanisms and safe autonomy remain limiting. | Include future recalibration requests, validation horizons, execution-event provenance and human review; do not present them as operational. |
| **7 — Concluding roadmap** | Prioritise metadata-complete failure-inclusive databases, soft-matter process science, fast surrogates, mechanism-aware ageing bridges and processability-aware design. Impact is material deployment rather than prediction speed alone. | Invest first in data provenance and QC, then ML readiness, then carefully bounded experimental integration specifications. |
| **8 — References** | Provides the cited research context and supporting literature; no separate supplementary experimental dataset is presented on this page. | Trace claims to the cited perspective and the ceramic source; keep article figures and publisher content linked rather than copied into the repository. |

### 5.1 Three waves of AI and the validated-data gap — Pages 1–2

The perspective's qualitative Figure 1 contrasts rapid growth in modelling capability with slower accumulation of validated physical evidence. This project addresses that asymmetry at the **data interface**: a candidate generated by a model cannot be treated as a DFT-labelled reference, and a DFT-labelled calculation cannot be treated as a fabricated device. The project will provide machine-readable evidence categories and traceable record ancestry so that scientific claims can be evaluated at their actual evidence level.

### 5.2 Three property regimes — Page 3

The perspective challenges over-reliance on a chemistry-only representation when material performance depends on preparation, state or measurement protocol. For the ceramic study, a composition must be linked to its **computational representation** (A/B-site fields, structure label, electronic method and target definition), and future experimental properties would require processing, specimen and measurement conditions. *This is a transfer of scientific metadata discipline, not a transfer of polymer-specific constitutive models.*

### 5.3 Two contrasting process-sensitive cases — Pages 3–4

**Sustainable thermoplastics:** The perspective stresses melt viscosity, shear thinning, extrusion and cooling histories, reprocessing stability and long-term recyclability. Techniques such as SAOS/LAOS rheology, capillary rheometry and DSC/FSC provide measurements that a repeat-unit descriptor cannot replace. A corresponding ceramic data architecture would need process-route, thermal-programme, equipment and microstructure records if real fabrication data were later supplied.

**Supramolecular hydrogels:** Gel formation, transient non-covalent interactions, water content, network topology and preparation history can affect stiffness, swelling, release and biomedical performance. Rheology, small-angle scattering, cryogenic microscopy and release assays interrogate different levels of material structure. The analogous *data-engineering* lesson is to preserve specimen and protocol context and not infer unobserved material states from formulation alone. The source BaTiO₃ workbook contains computational records and is **not** such an experimental dataset.

### 5.4 Representation hierarchy and the physical-validation boundary — Page 4

Figure 2 progresses from repeat-unit chemistry through sequence/architecture to processed morphology and assembly. Figure 3 contrasts two materials classes along the same chain: what a design representation captures, what it misses, which experiments supply missing evidence and which slow outcomes determine success. For this project, that logic motivates a typed evidence chain:

```text
Original source file + cell coordinates
       ↓
Composition and computational representation
       ↓
DFT-related reference calculation + method metadata
       ↓
Verified descriptors + 82-feature modelling matrix
       ↓
Model run + split + validation + optional prediction
       ↓
[Future only] documented synthesis → specimen → measurement → long-horizon validation
```

Each arrow requires a verifiable identifier or a documented unresolved linkage; no downstream status is inferred merely because an upstream record exists.

## 6. Detailed alignment with Section 5.1 and its four modules

The perspective's Section 5.1 (printed Page 5) proposes an informatics-centred loop with **four integrated modules**. The sections below set out a direct implementation response using the actual BaTiO₃ data. They differentiate **source evidence**, **independent planned engineering** and **future physical extensions**.

### 6.1 Section 5.1.1 — Database (Memory)

**Research issue.** Scientifically useful memory must preserve conditions, uncertainty, lineage, successes, documented failures and actual process history. Storing isolated numerical results without the conditions that produced them can mislead model training and materials decisions. [P, p. 5]

**Available ceramic evidence.** The workbook supplies source compositions, selected descriptors, calculated energies and method labels for linked computational records. The supplementary text supplies feature nomenclature and calculation descriptions. It does **not** supply a full experimental batch history, physical failure log or complete computational job provenance for every entry. [C; SI; X]

**Planned curation response:**

1. **Source registration:** capture publisher DOI, file name, SHA-256, byte size, acquisition/version date, worksheet name, Excel row/column, exact original header, source-cell values, formulas versus cached values and redistribution-review status.
2. **Chemistry-aware schema:** represent `composition_id`, nominal A-site fractions, original Ba/Sr/La/Ti/O coefficients, computational target, units and source identifiers. Keep nominal and workbook-reported formulae separately.
3. **Descriptor dictionary:** record each abbreviation, chemical/physical meaning, A-/B-/X-site role, aggregation or weighting formula, unit, permissible range and reference to [SI]. Audit all **82 selected inputs** rather than assuming numerical column labels are self-explanatory.
4. **Calculation metadata:** retain `GGA-PBE(VCA)` and `P4mm` labels where S4 supports them; store additional paper-level VCA/supercell/DFT assumptions without assigning unsupported individual-run metadata.
5. **Failure-inclusive schema, without invented failures:** provide nullable fields for calculation-job outcome, error reason, physical processing outcome and reviewer disposition; distinguish `unknown` from `failed` and `not attempted`.
6. **Quality and uncertainty:** store validation rule, severity, source evidence, disposition, provenance status and unresolved interpretation. An unverified method parameter is recorded as unavailable, not guessed.
7. **Evidence lineage:** maintain links from source file/cell through composition → calculation → descriptor/feature vector → split/model run → optional prediction. Preserve original source records unchanged.

**Suggested outputs:** `source_registry.csv`, `source_manifest.json`, `workbook_inventory.csv`, `composition.csv`, `calculation.csv`, `descriptor_dictionary.csv`, `qc_findings.csv`, `provenance_links.csv`, `evidence_status_dictionary.csv`.

**Acceptance criteria:** every curated row maps back to a source location; composition keys are unique or explicitly flagged; descriptor meanings are documented or unresolved; unlabelled S1 candidates are never automatically marked as failures; no original scientific observation is silently replaced.

**Research value:** a reusable and auditable computational evidence base, with a clear boundary between known, missing and uncertain scientific information.

### 6.2 Section 5.1.2 — Simulation (Physical Reasoning)

**Research issue.** Faster surrogate predictors are useful when tied to accurate physical calculations and periodic recalibration; a rapid approximate model does not replace an expensive high-fidelity solver or a physical experiment. The perspective illustrates this through multiscale simulations of polymer rheology, viscoelastic flow and processing. [P, p. 5]

**Available ceramic evidence.** The source study combines DFT-related formation-energy calculations with feature engineering and machine learning. The 231 labelled records allow a retrospective relationship between **calculated reference values** and **statistical predictions** to be studied. They do not provide an authorised live DFT scheduler or an autonomous recalculation service. [C, pp. 3–8; SI; X]

**Planned engineering response:**

1. Preserve distinct types for `source_formation_energy_eV_atom`, `independent_prediction_eV_atom`, `prediction_residual_eV_atom` and `calculation_method`. A DFT reference remains a calculation rather than an experimental measurement.
2. Reconcile the 231 S2/S4 reference-energy values by explicit composition identifiers and identify exceptions instead of assuming the same row order implies identity.
3. Verify construction of **100 initial features**, the exclusion of **16 constant features plus two non-input fields**, and the resulting **82 selected feature columns**. Reconcile S2 and S3 names and numerical values.
4. Audit feature definitions and correlations (Pearson correlation, multicollinearity, constant variables); prevent final-energy or target-derived values from entering model inputs.
5. Apply split-aware preprocessing: any fitted transformations or learned feature selection must be fitted only on training folds during independent validation. The publisher-supplied 82-feature matrix can audit the published representation, but cannot by itself prove that a new split is leakage-free.
6. If modelling is justified, compare transparent baselines with selected regressors (for example, linear regression, random forest and XGBoost), report **MAE, RMSE and R²** with units, and retain split membership, seed, model settings and prediction residuals.
7. Evaluate an ordinary random split against feasible **composition-blocked or held-out Sr/La-region validation**; quantify domain-of-applicability and extrapolation limitations.
8. Propose—without claiming execution—a future `calculation_request` record to route uncertain high-value predictions for new high-fidelity computations and record re-calibration outcomes.

**Suggested outputs:** `calculation_provenance.csv`, `feature_exclusion_manifest.csv`, `feature_linkage_checks.csv`, `leakage_audit.csv`, `split_plan.json`, `ml_readiness_report.md`; conditional `benchmark_results.csv`, `prediction_audit.csv`, `model_card.md`.

**Acceptance criteria:** 231 linked targets reconcile or exceptions are reported; the 82 input features contain no explicit target/final energy; no composition key crosses a train/test boundary; metrics have declared units and experimental scope; prediction uncertainty and extrapolation are communicated; no reproduced-performance claim is made before independent execution.

**Research value:** a defendable bridge from physical-computation data to ML outputs, with transparent assumptions and limits.

### 6.3 Section 5.1.3 — Generation (Design)

**Research issue.** Candidate design must account for scientific feasibility and processability **during selection**, not only after a predictor produces an apparently favourable property. The perspective describes integrating synthesis and processing constraints into generation. [P, p. 5]

**Available ceramic evidence.** S1 provides a large composition candidate space; S2/S4 supply a much smaller DFT-labelled subset; the ceramic paper uses formation-energy trends to select representative compositions and subsequently investigates specific ferroelectric, mechanical and thermal quantities. A predicted energy alone does not establish a synthesised or device-ready material. [C, pp. 2–5, 8–15; X]

**Planned engineering response:**

1. Validate nominal A-site substitution constraints: `x ≥ 0`, `y ≥ 0`, `x + y ≤ 1`; record valid composition-domain boundaries and their source.
2. Preserve the observed Ti–La workbook pattern and investigate source computational encoding separately from nominal stoichiometry and any proposed physical defect model.
3. Audit candidate descriptor completeness and compatibility with the validated feature dictionary before any model estimates are generated.
4. Classify each candidate as `candidate_only`, `calculation_reported`, `prediction_generated`, `published_property_analysis` or `experimental_result_documented` **only with evidence**; do not promote a predicted candidate into a synthesis result.
5. Distinguish composition validity, electrostatic/charge-compensation interpretation, relative calculated energy, phase behaviour, dielectric response and manufacturing feasibility. These are not interchangeable approval flags.
6. If optional candidate screening is implemented, include prediction, model version, interpolation/extrapolation flag, known structural assumptions and **researcher review status**; do not publish a composite 'best material' ranking without independently defined and validated criteria.
7. Make processability-aware screening a **future rule interface**: require verified sintering, deposition, microstructure or electrical data before claiming process-specific feasibility.

**Suggested outputs:** `candidate_registry.csv`, `composition_validation.csv`, `composition_representation_review.csv`, `candidate_status.csv`, `candidate_constraints.json`; conditional `candidate_screening.csv`.

**Acceptance criteria:** chemically invalid or out-of-scope entries have explicit reasons; original coefficients remain recoverable; predicted stability is not labelled experimental stability; no unobserved synthesis or performance claims appear.

**Research value:** candidate records usable for disciplined hypothesis generation, rather than unsupported material claims.

### 6.4 Section 5.1.4 — Synthesis, Manufacturing and Characterisation (Action and Perception)

**Research issue.** The physical execution layer can remain the limiting stage. The perspective's examples—non-Newtonian liquids, viscous melts, shear and thermal histories, fouling, reactor handling and inline measurements—are process-specific. Robotic throughput alone does not guarantee reproducible material state or faithful measurement. [P, p. 5]

**Available ceramic evidence.** The supplied 231 energy records are **computational records**, not traceable physical ceramic specimens, powder batches, sintering cycles, thin-film deposition runs, laboratory dielectric spectra or robotic action logs. The published article discusses calculated materials properties and selected structural models; such calculations cannot be re-labelled as experiment records. [C; X]

**Planned integration specification—not a claim of laboratory operation:**

1. Define future entities for `experimental_batch`, `raw_material_lot`, `specimen`, `processing_step`, `instrument_run`, `measurement`, `calibration`, `quality_event` and `failure_log`.
2. Permit route-specific metadata where justified: precursor identity/purity; powder mixing/milling; calcination and sintering temperatures, dwell and atmosphere; heating/cooling profiles; ceramic density and porosity; phase/microstructure characterisation; thin-film deposition variables; dielectric and electrical testing conditions.
3. Keep **intended parameters** distinct from **measured/achieved parameters**; require sample identity and timestamps before attaching physical observations.
4. Separate identifiers for **computational composition/calc jobs** from **manufactured specimens and instrument runs**; a formula match does not prove the same sample exists.
5. Specify future instrument-adapter inputs/outputs, units, calibration records, machine-readable protocols, exception handling and append-only action logs; include human review before an autonomous decision is accepted.
6. Document aborted runs and negative results only when records become available. Experimental absence is an evidence gap, not a fabricated failure count.
7. Reserve future process-history and physical-property validation fields for ceramics rather than copying polymer melt-rheology columns into an inappropriate material modality.

**Suggested outputs:** `experimental_schema_proposal.md`, `instrument_event_schema.json`, `specimen_linkage_rules.md`, `measurement_metadata_template.csv`, `integration_requirements.md`.

**Acceptance criteria:** no computational record acquires a physical `specimen_id` without documented evidence; future measurements require units, instrument/protocol context and provenance; all instrumentation fields remain proposals until real, authorised laboratory data are available.

**Research value:** a defensible data-interface specification that can support future experimental integration, while preserving the distinction between a computational portfolio and a deployed autonomous laboratory.

## 7. Section 5.2: the two limits that an automated loop cannot remove

The framework's Section 5.2 begins on Page 5 and continues on Page 6; Figure 4 on Page 6 shows a fast inner loop and slower checks that re-anchor simulation and measurements. The two limits are essential **engineering constraints**, not reasons to abandon automation.

### 7.1 Limit 1 — Time and slow-property validation

The perspective warns that optimising short-duration proxies can miss the very long-duration properties that define practical success. It discusses time–temperature superposition (including WLF or Arrhenius treatments in restricted regimes), chemically accelerated ageing and mechanism-preserving validation. Such bridges are only defensible when their physical assumptions are checked; viscoelastic transitions, chemistry changes and nonlinear response can invalidate extrapolation. [P, pp. 5–6]

**Material-specific connection:** for polymeric materials, relevant slow outcomes include creep, relaxation, degradation, recyclability retention and biological responses. For ceramic capacitors, potential future concerns include dielectric ageing, electrical fatigue, breakdown strength, thermal cycling and long-term device reliability. The supplementary formation-energy workbook **does not supply those long-horizon tests**.

**Project response:**

- Model a proposed `long_horizon_validation` entity with `specimen_id`, target property, stressor, protocol, actual observation duration, environmental conditions, raw time series, uncertainty and mechanistic extrapolation assumptions.
- Distinguish direct observation, validated accelerated test, unvalidated proxy and ML extrapolation through explicit evidence status.
- Record mechanism checks and the domain for any future accelerated ageing model; do not estimate years-long device life from a DFT formation energy or a short test.
- Keep long-duration or physical fields absent—not imputed—when only computational reference data exist.

**Current deliverable:** a documented future-data schema and evidence rule set. **Not delivered:** accelerated ageing experiments or demonstrated capacitor lifetime predictions.

### 7.2 Limit 2 — Physical execution and rheological/handling constraints

The perspective's second limit concerns physically handling non-dilute, process-sensitive soft matter—viscosity, viscoelasticity, yield stress, shear-induced structure, fouling and temperature dependence. Flow-rate optimisation is not the same as reproducible material synthesis. [P, pp. 5–6]

A ceramic project faces **different possible physical bottlenecks**: powder flow, slurry rheology (where a slurry route applies), phase purity, sintering shrinkage, defects, thermal gradients, grain evolution, deposition conditions and batch variation. Those are **future ceramic experimental metadata requirements**, not findings in the current supplementary workbook.

**Project response:** design modality-specific interfaces linking composition → process route → equipment conditions → specimen → measurement → QC decision, while keeping process histories and instrumentation identifiers out of the computational-only tables until supported by genuine records.

### 7.3 Discovery-to-manufacturing, scale and safe operation

Page 6 also highlights that milligram-scale screening does not establish manufacturing-scale robustness and that autonomous operation requires safety and auditable responsibility. A candidate selected by a model must survive the physics and constraints of later process scales. A future decision/action log should therefore contain the proposal, constraints checked, human approval, observed execution, error state and source measurements. This project will **specify** such fields; it will not claim industrial scale-up or safe operation of actual robotics.

### 7.4 Concluding roadmap — Page 7

The perspective prioritises: (1) metadata-complete, failure-inclusive scientific databases; (2) deeper study of difficult process physics; (3) faster physics-informed surrogate simulation; (4) mechanism-aware bridging to slow validation; and (5) processability-aware design. For this independent BaTiO₃ exercise, the practical sequence is **database and provenance first → scientific QC and linkage → modelling readiness → optional predictions → future process-aware evidence intake**. The expected contribution is better research decisions and auditability, **not an unsupported claim that physical material discovery has already been accelerated**.

## 8. Data model, scientific integrity and evidence classification

### 8.1 Core entities justified by the supplied data

| Entity/table | Indicative key fields | Reason for inclusion |
|---|---|---|
| `source_file` and `source_row` | `source_id`, `sha256`, `worksheet`, `excel_row`, `excel_column`, `acquired_at` | Exact source-cell provenance and repeatable extraction. |
| `composition` | `composition_id`, `Ba`, `Sr`, `La`, `Ti_tabulated`, `O`, `nominal_formula`, `source_formula` | Distinguish chemistry-level representation and the Ti/La discrepancy. |
| `calculation` | `calculation_id`, `composition_id`, `method`, `space_group`, `energy_value`, `unit`, `source_id` | Represent S2/S4 DFT-related targets and computational context. |
| `descriptor_dictionary` | `feature_name`, `site`, `definition`, `aggregation_rule`, `unit`, `source_ref` | Interpretable and reviewable input features. |
| `feature_matrix` / `linkage` | `composition_id`, `feature_version`, `target_reference`, `linkage_status` | Validate the 82 features against the correct 231 targets. |
| `qc_finding` | `finding_id`, `source_record_id`, `rule_id`, `severity`, `evidence`, `disposition` | Preserve anomalies and scientific review decisions. |
| `model_run` (conditional) | `run_id`, `feature_version`, `split_id`, `seed`, `estimator`, `metrics` | Trace optional independent predictions. |
| `experimental_specimen` (future only) | `specimen_id`, `batch_id`, `processing_run`, `measurement_id` | Reserved for genuine future physical records, not synthetic laboratory data. |

### 8.2 Quality-control principles

- **Non-destructive:** retain raw values and source coordinates; put standardised values and diagnostic calculations in new fields.
- **Chemistry-aware:** validate nominal A-site fractions but keep the original Ti representation under investigation; do not equate formula constraints with verified charge compensation.
- **Calculation-aware:** preserve energy reference, normalisation, method assumptions and units (`eV/atom`); do not substitute calculated energies for experimental tests.
- **Leakage-aware:** separate target and descriptive final-energy fields from model inputs; prevent duplicate or composition-neighbour leakage where relevant.
- **Source-aware:** use exact keys and row-level exceptions for S2/S3/S4 joins; do not assume spreadsheet row position establishes sample identity.
- **Failure-aware:** distinguish not evaluated, not reported, unsuccessful calculation and failed physical experiment.
- **Evidence-aware:** keep published results, reproduced checks, independent ML estimates, hypothetical extensions and physical observations clearly labelled.
- **Reviewer-aware:** ambiguous chemistry and method inconsistencies receive explicit review status, with no silent 'correction'.

### 8.3 Audit and acceptance gates

| Gate | Required verification |
|---|---|
| **A — Source integrity** | Stable file hashes, version/rights manifest, source-cell traceability and immutable raw inputs. |
| **B — Chemical representation** | A-site constraints assessed; nominal versus tabulated Ti documented and unresolved mechanism not misreported. |
| **C — Cross-sheet linkage** | All available labelled records reconciled across S2/S3/S4 using declared keys, with numeric agreement and exceptions. |
| **D — Descriptor legitimacy** | All 82 selected inputs defined or explicitly unresolved; target/final energy absent from predictors. |
| **E — Evidence classes** | Candidate-only, DFT reference, ML prediction, actual documented experiment and genuine failure distinguished. |
| **F — ML readiness** | Feature–target linkage, sample coverage, leakage controls and split design accepted before training. |
| **G — Reproducibility** | Fresh-session rerun yields stable counts/outputs, manifest and QC report; nondeterministic steps are documented. |
| **H — Scientific claims** | Repository results reflect work actually executed; no unverified autonomous-lab, synthesis or long-term performance claims. |

## 9. Implementation roadmap: Phases 00–09

The phase definitions below are **implementation commitments and proposed output paths**, not claims that executable notebooks or QC datasets already exist. Each phase has an explicit scientific rationale, workflow and completion check.

| Phase | Focus and intended scientific contribution | Principal deliverables | Completion gate |
|---|---|---|---|
| **00** | Register source/version/rights, scientific assumptions and evidence classes. | `source_registry.csv`, `source_manifest.json`, `research_scope.md` | Complete manifest and source hashes. |
| **01** | Audit every sheet, header, original formula cell, type, duplicate and key. | `workbook_inventory.csv`, `column_inventory.csv`, `source_audit_report.md`, `qc_findings.csv` | Every reported result has source coordinates. |
| **02** | Design canonical composition/calculation/descriptor/QC schema. | `schema_design.md`, `data_dictionary.csv`, `schema_relationships.md` | Keys, definitions, units and missingness rules documented. |
| **03** | Validate composition constraints and numerical quality; investigate Ti encoding. | `composition_validation.csv`, `composition_representation_review.csv`, `qc_findings.csv` | No destructive fixes or undocumented mechanism assignments. |
| **04** | Standardise composition fields, energy units and descriptors. | `composition_standardised.csv`, `feature_dictionary.csv`, `transformation_log.csv` | Source values preserved; 82-feature dictionary checked. |
| **05** | Link S2, S3 and S4 by verified keys and build evidence layer. | `linkage_summary.csv`, `linkage_exceptions.csv`, conditional `analysis_ready_evidence.csv` | Record-level reconciliation and exceptions reproducible. |
| **06** | Explore composition region, formation-energy distribution and descriptors. | `eda_summary.md`, `composition_space.png`, `formation_energy_distribution.png`, `feature_correlations.png` | Figures show counts, units, provenance and inference limits. |
| **07** | Review ML readiness, leakage, split design and chemical-domain coverage. | `ml_readiness_report.md`, `leakage_audit.csv`, `split_plan.json` | Validation design justified before training. |
| **08** | Optional reference baselines and candidate screening when justified. | `benchmark_results.csv`, `prediction_audit.csv`, `model_card.md`, conditional `candidate_screening.csv` | Predictions separated from DFT and experiments; limitations documented. |
| **09** | Clean rerun, testing, documentation and versioned release. | `requirements.txt`, `run_manifest.json`, `validation_summary.csv`, `tests/` | Reproducible regeneration from permitted raw inputs. |

### Phase 00 — Research scope and source registry

**Purpose:** guarantee that downstream data have known origin, permitted usage, unambiguous version and scientific scope. Register input file paths, publication DOI, hash, size and acquisition date; document distinction between computational reference and predicted/experimental values. **Python:** `pathlib`, `hashlib`, `json`, structured CSV writing. **Quality gate:** a clean run can verify the source file before extraction.

### Phase 01 — Full source-data audit

**Purpose:** move beyond preliminary sheet sizes to verified structural and scientific evidence. Inventory `S1`–`S4`, original cell addresses, types, numeric headers, formula/cached-value pairs, missingness and duplicates; map candidate versus DFT-labelled populations; re-check unique composition keys and S2/S3/S4 values; document Ti/La issues without 'repairing' them. **Python:** auditable workbook reads, structured extraction and report generation. **Quality gate:** another researcher can trace each reported count and exception back to an original cell.

### Phase 02 — Scientific schema and dictionary

**Purpose:** represent composition, calculation, feature definition and QC as linked scientific objects. Define A-/B-site semantics, DFT target reference, method evidence and required versus optional metadata. **Python:** typed schema validation with versioned dictionaries and stable IDs. **Quality gate:** every curated field has a defined meaning, provenance and missingness rule.

### Phase 03 — Composition validation and scientific QC

**Purpose:** distinguish data anomalies from physically meaningful computational conventions. Validate bounds, key uniqueness, numeric plausibility and composition constraints; preserve Ti/La discrepancy as an unresolved interpretative item. **Python:** declarative tests, exception registers and review dispositions. **Quality gate:** every issue has evidence, severity and non-destructive treatment.

### Phase 04 — Standardisation and feature documentation

**Purpose:** make verified source features consistent and analysis-ready without losing meaning. Record formula representations, feature weighting, descriptor sites, type conversions and `eV/atom` target units; reconcile 100 source features versus 82 model inputs. **Python:** deterministic transformations, feature dictionary and exclusion manifest. **Quality gate:** all transformations can be traced and reversed or reconstructed.

### Phase 05 — Provenance and reliable record linkage

**Purpose:** ensure each modelling row connects to the correct calculated target. Match S2/S3/S4 via scientific keys, compare shared features and energies, quantify unmatched records and duplicate conflicts; emit evidence tables only after linkage passes. **Python:** explicit joins, validation assertions and source-to-output lineage. **Quality gate:** no row-order-only joins; full exception report.

### Phase 06 — Exploratory materials-informatics analysis

**Purpose:** understand the observed chemical domain before modelling. Examine Sr/La distributions, energies, descriptor correlation structure, data density and outliers; connect interpretation to source calculation conditions. **Python:** NumPy, scientific tabular summaries, Matplotlib. **Quality gate:** every figure reports provenance, sample count, unit and interpretation limits.

### Phase 07 — Machine-learning readiness

**Purpose:** decide whether 231 reference values support a valid predictive experiment and what generalisation can be claimed. Assess label alignment, leakage and redundancy, restricted chemical coverage, near-neighbours and random versus blocked validation. **Python:** split manifests and leakage tests. **Quality gate:** split plan pre-specified and data-derived operations confined to training folds.

### Phase 08 — Optional regression and screening

**Purpose:** independently benchmark formation-energy prediction where justified. Compare suitable baselines and selected published model families, report MAE/RMSE/R² and residual patterns under documented splits; apply models to candidates only with compatible descriptors and domain checks. **Python:** scikit-learn and optional XGBoost/SHAP. **Quality gate:** no unsupported claims of reproducing published metrics or validated experimental performance.

### Phase 09 — Workflow engineering and reproducibility

**Purpose:** make the whole process restart-safe and independently auditable. Use relative paths, pinned dependency versions, deterministic outputs where feasible, versioned configuration, automated assertions, run manifests and documented exceptions. **Python:** modular scripts/tests and clean Jupyter execution. **Quality gate:** an independent clean run regenerates the declared output evidence.

## 10. Quality gates, reproducibility and repository structure

### Planned repository layout

```text
Project_Machine_learning_and_first-principles_guided_desig/
├── README.md
├── requirements.txt                    # Created after actual dependency verification
├── .gitignore                          # Exclude restricted raw data / transient files
├── data/
│   ├── raw/                             # Local only until rights are verified
│   ├── interim/                         # Intermediate, provenance-preserving outputs
│   └── processed/                       # Validated and redistributable outputs only
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
├── src/                                  # Reusable extract/validate/link functions
├── docs/
│   ├── data_dictionary.csv
│   ├── schema_design.md
│   ├── composition_representation_review.md
│   └── source_and_method_notes.md
├── reports/
│   ├── qc/
│   └── figures/
├── manifests/
│   └── source_manifest.json
└── tests/
```

This tree represents the **intended structure**. Notebooks and files will be added as completed work warrants; an empty folder listing is not evidence of an implemented pipeline.

### Execution standards

- Keep original source inputs immutable and use hashes to detect source changes.
- Use explicit, validated schema and join keys; retain original cell coordinates.
- Record versions of Python, installed packages, code and configuration in each completed phase.
- Make output directories deterministic and avoid manual notebook-state dependencies.
- Produce both machine-readable QC findings and a concise human-readable scientific interpretation.
- Define pass/fail criteria before running a test; preserve findings that require expert review.
- Recompute every published summary from controlled scripts and document any unreproducible source claims.
- Keep the original sources and published results clearly distinct from independently generated analyses.

## 11. Expected research contribution, boundaries and next steps

### Demonstrable contributions after implementation

A completed project should provide:

- **A provenance-complete computational materials register** connecting source files and cells with compositions, DFT-related calculation records and descriptors.
- **Chemistry-aware validation** addressing A-site substitution constraints, uncertain Ti/La representation and scientific units without overwriting data.
- **Verified S2–S3–S4 record linkage**, with record-level exceptions and target/feature lineage.
- **Scientific-data quality assessment** covering missingness, duplicates, feature meaning, evidence class, correlation and leakage risk.
- **Reproducible workflow execution** with manifests, data dictionaries, tests, QC reports and independently auditable transformations.
- **Conditional ML-readiness and regression studies**, with composition-domain limitations and explicit prediction versus reference status.
- **Future-ready interfaces** for calculation requests, failures, experimental provenance and long-horizon validation, carefully identified as specifications rather than operational systems.

### Boundaries of current evidence

The public supplemental workbook does **not**, by itself, establish actual ceramic synthesis, a running self-driving laboratory, physical robot integration, experimentally measured electrical reliability, independently documented DFT job failures or real long-term ageing outcomes. Nor can computational formation-energy screening alone resolve the polymer perspective's handling and long-horizon testing limitations. Any such activities would require new data, experimental infrastructure and separate validation.

### Current versus planned work

| Workstream | Status as of 4 November 2026 |
|---|---|
| Main article and supplementary documentation review | **Completed for research scoping** |
| Preliminary S1–S4 structural inventory and 231-record cross-sheet comparison | **Preliminary checks completed; reproducible public Phase 01 audit pending** |
| Ti–La composition discrepancy identified | **Flagged for scientific review; not resolved** |
| Source registry, manifest and complete automated audit notebooks | **Planned** |
| Canonical schema, comprehensive QC and verified data exports | **Planned** |
| ML leakage audit, independent modelling and candidate screening | **Conditional / planned** |
| Actual synthesis, robotic integration and long-term physical tests | **Outside current scope** |

**Immediate next milestone:** implement Phases **00 and 01**, beginning with a source manifest, full workbook audit, explicit 231-record S2/S3/S4 linkage tests and a documented chemical-interpretation findings register. Advance to data standardisation and modelling only when those gates have been met.

## 12. References and research independence

- **[C]** **Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications**. *Journal of Applied Physics* **139**, 064101 (2026). [https://doi.org/10.1063/5.0314819](https://doi.org/10.1063/5.0314819).
- **[SI, X]** Official supplementary information and research workbook associated with [C]. [https://doi.org/10.60893/figshare.jap.c.8234602](https://doi.org/10.60893/figshare.jap.c.8234602).
- **[P]** **Predicting Faster Than We Can Make: Polymer-Specific Process Physics as a Frontier for Autonomous Soft-Matter Discovery**. *Macromolecular Rapid Communications* (2026). [https://doi.org/10.1002/marc.70420](https://doi.org/10.1002/marc.70420). Particularly Section 5.1 (p. 5), Section 5.2 (pp. 5–6), Figures 1–4, and the concluding roadmap (p. 7).

**Attribution and independence.** The original research, calculations, interpretations and supplementary datasets remain attributable to their respective authors and rights holders, as identified in the linked publisher records. This repository documents an **independent educational and professional materials-data engineering project**. It does not claim an official institutional collaboration, a research appointment, endorsement, access to internal laboratory systems or authorship of the original studies. Original datasets and copyrighted publisher graphics will be linked or reused only in accordance with applicable licensing and permissions.
