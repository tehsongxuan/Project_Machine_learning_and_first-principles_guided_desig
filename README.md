# BaTiO₃ Ceramic Materials Data Curation and AI-Ready Workflow Engineering

**Repository:** `Project_Machine_learning_and_first-principles_guided_desig`  
**Project type:** Independent scientific data curation and reproducible Python workflow portfolio  
**Material system:** Strontium/lanthanum-doped barium titanate, `(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`  
**Project status (31 October 2026):** Research scope defined; source files obtained and workbook structure checked. Full phase-by-phase analysis is **planned, not yet completed**.

## 1. Project overview

This project develops a transparent, reproducible data workflow based on the supplementary materials accompanying a published study of **BaTiO₃-based ceramics**. The original study used first-principles calculations and machine learning to explore how changes in chemical composition relate to calculated formation energy.

**In simpler terms:** Barium titanate is a ceramic. In this study, some barium is replaced with strontium (Sr) and lanthanum (La). The research asks how the proportions of these elements affect a calculated measure of the material's energy. My project asks a different but complementary question: **Can the supporting data be organised, checked, linked and documented reliably enough for another researcher to understand and reuse the computational workflow?**

The principal focus is **materials data curation, scientific quality control, provenance and workflow engineering**. Machine-learning reproduction is a later, conditional extension—not the starting point.

### Main research question

How can a reproducible Python pipeline transform the supplied ceramic-composition, descriptor and first-principles calculation data into a **validated, traceable and machine-learning-ready evidence layer**?

### What this project does not claim

- It does not claim to have generated the original density functional theory (DFT) calculations.
- It does not treat computed formation energies as laboratory measurements.
- It does not claim to reproduce an autonomous or robotic laboratory.
- It does not claim affiliation with or endorsement by the source publication's authors or institutions.
- It does not claim that any planned notebook, analysis, model or validation has already been completed.

## 2. Original scientific source and attribution

**Source publication:** Guo et al. (2026), *Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications*, **Journal of Applied Physics, 139**, 064101.  
**Paper DOI:** https://doi.org/10.1063/5.0314819  
**Official supplementary collection:** https://doi.org/10.60893/figshare.jap.c.8234602  
**Article licence:** [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) for article content unless otherwise noted.

The publisher's linked article provides the **complete author list**, contribution statements and publication details. The original scientific ideas, calculations, findings, tables and datasets belong to their respective creators and rights holders. This repository contains an **independent data-engineering interpretation and workflow**, not a new version of the source publication.

**Data-rights note:** The article's CC BY licence should not be assumed to apply automatically to every separately hosted supplementary dataset, image or third-party item. Before publicly uploading source files or substantial derived data, verify the specific file's licence, attribution conditions and redistribution permissions. The paper also states that supporting data are available from the corresponding author upon reasonable request. Where permissions remain unclear, publish source links, original code, documentation and permissible summary findings rather than redistributing source files.

## 3. Source files and preliminary dataset inventory

The project currently uses the following materials obtained from the publication and its supplementary collection:

| Source | Role in this project |
|---|---|
| `Supplementary Dataset.xlsx` | Main workbook containing sheets `S1`, `S2`, `S3` and `S4`. |
| `Supplementary information.docx` | Calculation descriptions, scientific abbreviations, ML settings, supplementary tables and feature-correlation figure. |
| Published research article | Scientific background, methods, reference results, interpretation and limitations. |
| Earlier thermoresponsive hydrogel README | Reference for documenting a careful, phased data-curation workflow; **not** a ceramic data source. |

### Preliminary workbook structure

The following counts describe **initial file inspection only**. They are not the results of a full data-quality audit.

| Sheet | Observed data rows | Observed columns | Preliminary role | Verification still required |
|---|---:|---:|---|---|
| `S1` | 30,301 | 100 | Candidate composition/descriptor space | Identify every numeric header and confirm chemistry/feature meanings. |
| `S2` | 231 | 102 | Calculated composition records, descriptors and formation-energy information | Confirm target field, units, keys and data provenance. |
| `S3` | 231 | 82 | Selected machine-learning input features | Verify correspondence to the correct `S2` targets. |
| `S4` | 231 | 10 | Additional supplementary sheet | **Purpose not yet verified**; retain and investigate separately. |

**Important distinction:** The 30,301 candidate rows should **not** be described as 30,301 independently calculated DFT target values. The published study uses a smaller set of calculated compositions to support a larger ML screening exercise.

Several spreadsheet headers are numerical rather than descriptive. Their scientific meanings must be established from the supplementary documentation and verified transformations—not guessed from their positions.

## 4. Why this project follows my polymer and hydrogel work

My earlier portfolio work includes **polymer glass-transition-temperature (Tg) prediction**, **collagen hydrogel rheology data curation**, and **hydrogel/bioink experimental-data workflows**. This project transfers the *data-science approach* to a different material class. It does **not** imply that ceramic oxides are polymers or that their physical properties are interchangeable.

| Shared data-science concept | Earlier polymer/hydrogel projects | Present BaTiO₃ project | Lesson carried forward |
|---|---|---|---|
| **Representing materials** | Polymer repeat-unit structures, SMILES, formulation details | Elemental composition and crystal-site descriptors | Correct scientific representation is essential before analysis. |
| **Creating features** | RDKit descriptors and molecular fingerprints | Elemental properties, ionic radii, electronegativity and site-specific descriptors | Every feature must have a definition, origin and appropriate use. |
| **Predicting a property** | Polymer Tg, reported in °C | DFT formation energy, reported in eV/atom | Both involve regression, but the target physics and units differ. |
| **Checking measurements** | Rheology results such as G′, G″ and tan δ | Computed energies, compositions and reported supplementary properties | Units, methods and provenance must remain attached to values. |
| **Linking records** | Formulation → treatment → sample → measurement | Composition → calculated result → descriptors → optional prediction | Never assume two records belong together just because they share a row position. |
| **Testing generalisation** | Random-split performance versus polymer-family holdouts | Random splits versus withheld dopant/composition regions | A model's accuracy depends on which new materials it must predict. |
| **Building workflows** | Restart-safe extraction, validation and QC reporting | Restart-safe ingestion, composition checks, joins and model-readiness audits | Reproducibility is a scientific requirement, not just a coding convenience. |

### Three important scientific differences

1. **Tg is not formation energy.** Polymer Tg reflects a temperature-dependent change in segmental mobility; DFT formation energy describes energy relative to stated reference materials and computational assumptions.
2. **A hydrogel is not a ceramic crystal.** Polymer-network chemistry, swelling and oscillatory rheology differ from atomic substitutions, crystal structures and ceramic mechanical/electronic properties.
3. **Computation is not experiment.** A DFT-labelled row does not demonstrate that a physical ceramic specimen was manufactured or tested.

## 5. Project objectives

1. **Source audit:** Identify the original files, versions, sheet meanings, columns and metadata.
2. **Schema design:** Define consistent entities for compositions, descriptors, computed targets, predictions and provenance.
3. **Scientific QC:** Detect missing entries, duplicates, invalid dopant fractions, inconsistent numerical values and unexplained metadata.
4. **Standardisation:** Make scientific units, naming conventions and data types comparable without changing original values.
5. **Record linkage:** Connect records across the supplementary sheets **only when scientifically defensible**.
6. **Exploratory analysis:** Explain the verified relationships between composition, material descriptors and DFT formation energy.
7. **ML readiness:** Assess sample size, label linkage, leakage risk, train/test design and uncertainty.
8. **Optional modelling:** Reproduce or extend baseline regression models only after the quality gates are passed.
9. **Workflow engineering:** Create a repeatable, restart-safe Python process with traceable outputs and documented limitations.

## 6. Planned phase-by-phase workflow

`Phase 00 Scope → 01 Source audit → 02 Schema → 03 QC → 04 Standardisation → 05 Linkage → 06 Exploration → 07 ML readiness → 08 Optional modelling → 09 Reproducibility`

Each phase below describes **planned work**, not a completed deliverable.

### Phase 00 — Research scope and source registry

**Purpose in simple terms:** Decide what data we are studying, what the question is and where the data came from.

- **Data science work:** Record source URLs, article DOI, acquisition date, filenames, checksums, permissions and intended outputs.
- **Chemistry/materials work:** Define Sr/La-substituted BaTiO₃, the calculated formation-energy target and the limits of the source study.
- **Polymer/hydrogel connection:** Just as a hydrogel project must identify formulation and sterilisation conditions, this project must identify composition and calculation assumptions before comparing records.
- **Planned outputs:** `source_registry.csv`, `research_scope.md`, `source_manifest.json`.
- **Completion check:** Every source has a clear identity, purpose and reuse status.

### Phase 01 — Source-file and workbook audit

**Purpose in simple terms:** Open the supplementary workbook and establish exactly what each sheet contains before cleaning anything.

- **Data science work:** Inventory sheets `S1`–`S4`, dimensions, column labels, missingness, data types, possible identifiers and duplicate candidates without changing source values.
- **Chemistry/materials work:** Investigate which fields describe Ba/Sr/La composition, descriptors, total energy and formation energy.
- **Polymer/hydrogel connection:** This mirrors auditing original rheology spreadsheets for sheet types, axes, units and ambiguous sample labels.
- **Planned outputs:** `workbook_inventory.csv`, `column_inventory.csv`, `source_audit_report.md`.
- **Completion check:** Every unexplained sheet or column is listed as **unresolved**, not silently interpreted.

### Phase 02 — Scientific schema and data dictionary

**Purpose in simple terms:** Organise the spreadsheet into tables that tell us what each scientific number means.

- **Data science work:** Define tables for `compositions`, `descriptors`, `calculated_targets`, `predictions`, `source_records` and `qc_findings`. Specify keys, data types, units and links between records.
- **Chemistry/materials work:** Distinguish the perovskite A-site (Ba/Sr/La), B-site (Ti), oxygen site and elemental descriptors.
- **Polymer/hydrogel connection:** This is similar to separating polymer formulations, treatments, samples and measurements into a well-defined hydrogel schema.
- **Planned outputs:** `schema_design.md`, `data_dictionary.csv`, `schema_relationships.md`.
- **Completion check:** Each curated field has a verified meaning or an explicit uncertainty flag.

### Phase 03 — Data quality control and composition validation

**Purpose in simple terms:** Check that the data are chemically sensible and technically usable before an AI model sees them.

- **Data science work:** Test missing values, non-numeric fields, repeated records, potential outliers, contradictory labels and key uniqueness; write findings to a QC register.
- **Chemistry/materials work:** Once dopant fields are confirmed, check `x ≥ 0`, `y ≥ 0` and `x + y ≤ 1` for `(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`. Investigate possible charge-balance assumptions without inventing an undocumented defect chemistry.
- **Polymer/hydrogel connection:** Analogous to checking invalid polymer SMILES, duplicate canonical structures and conflicting Tg values.
- **Planned outputs:** `qc_findings.csv`, `composition_validation.csv`, `quality_summary.md`.
- **Completion check:** The process preserves all raw values and explains failures instead of silently deleting records.

### Phase 04 — Standardisation and materials-feature interpretation

**Purpose in simple terms:** Make the data consistent without losing the original scientific meaning.

- **Data science work:** Harmonise verified column labels, numeric types, missing-value conventions and keys; keep a record of every transformation.
- **Chemistry/materials work:** Preserve formation energy in **eV/atom** where that unit is confirmed, and avoid confusing it with total energy, eV/formula unit, Tg in °C or rheological modulus in Pa. Interpret elemental descriptors using the supplementary feature dictionary.
- **Polymer/hydrogel connection:** Similar to converting polymer and hydrogel data to consistent temperature, frequency and modulus units while retaining original values.
- **Planned outputs:** `composition_standardised.csv`, `feature_dictionary.csv`, `transformation_log.csv`.
- **Completion check:** Each transformed value can be traced back to its source and documented rule.

### Phase 05 — Provenance, linkage and analysis-ready evidence

**Purpose in simple terms:** Prove that the correct features and formation-energy values belong to the same composition.

- **Data science work:** Investigate validated composition-based join keys, duplicate keys, match rates and mismatched rows. Link `S3` features with `S2` targets only after the relationship is demonstrated; keep `S4` separate until identified.
- **Chemistry/materials work:** Preserve the meaning of calculated outputs and any available crystal/computational context. Do not create physical-sample IDs for computational rows.
- **Polymer/hydrogel connection:** The same principle applies as with hydrogel records: similar filenames or matching row numbers do not prove that measurements belong to one sample.
- **Planned outputs:** `linkage_summary.csv`, `unresolved_review_items.csv`, and—**only if verified**—`analysis_ready_evidence.csv`.
- **Completion check:** Links are explained, testable and reproducible; uncertainty remains visible.

### Phase 06 — Exploratory ceramic materials analysis

**Purpose in simple terms:** Understand the patterns in the validated data before attempting predictions.

- **Data science work:** Create distributions, missingness summaries, descriptor correlations, composition-space plots and formation-energy trends.
- **Chemistry/materials work:** Interpret relationships involving Sr/La fractions and confirmed properties such as ionic radius or electronegativity, without claiming that correlation proves a physical mechanism.
- **Polymer/hydrogel connection:** Comparable to plotting polymer Tg by structure/family or hydrogel G′/G″ by experimental condition before model fitting.
- **Planned outputs:** `eda_summary.md` and figures such as `composition_space.png`, `formation_energy_distribution.png` and `feature_correlations.png`.
- **Completion check:** Every chart identifies its data source, subset, scientific units and limitations.

### Phase 07 — Machine-learning readiness and data-leakage audit

**Purpose in simple terms:** Check whether the verified data support a fair and meaningful prediction test.

- **Data science work:** Check target inclusion among features, constant columns, possible duplicate leakage, feature quality, sample size and train/test splits. Compare a conventional holdout with more demanding composition-region tests where feasible.
- **Chemistry/materials work:** Examine whether new candidate compositions lie within the chemistry learned from the 231 DFT-labelled cases or require extrapolation.
- **Polymer/hydrogel connection:** This echoes the contrast between good random-split Tg results and weaker predictions on an unseen polymer family. Strong in-sample accuracy does not guarantee useful predictions on unfamiliar materials.
- **Planned outputs:** `ml_readiness_report.md`, `leakage_audit.csv`, `split_plan.json`.
- **Completion check:** Do not proceed to modelling until feature–target linkage, data quality and validation design have passed review.

### Phase 08 — Optional machine-learning benchmarks and screening

**Purpose in simple terms:** Only after quality checks, test whether models predict formation energy accurately for genuinely held-out compositions.

- **Data science work:** Compare a baseline against suitable regressors such as linear regression, random forest and XGBoost; report MAE, RMSE and R²; inspect errors across composition regions. Screen `S1` candidates only if its feature schema is confirmed.
- **Chemistry/materials work:** Remember that the prediction is **DFT formation energy**, not directly measured capacitance, manufacturability or laboratory success.
- **Polymer/hydrogel connection:** Reuse the discipline of polymer Tg modelling, but with different chemical descriptors and a different physical target.
- **Planned outputs:** `benchmark_results.csv`, `prediction_audit.csv`, `candidate_screening.csv` (conditional), `model_card.md`.
- **Completion check:** Independently produced results are labelled separately from the source paper's reported results; no unverified model reproduction is claimed.

### Phase 09 — Reproducible workflow engineering and GitHub release

**Purpose in simple terms:** Make the process easy for another person to rerun, audit and understand.

- **Data science work:** Use relative paths, pinned dependencies where appropriate, repeatable random seeds, stable output names, automated checks, run logs and an execution manifest. Re-running a phase should not damage original data or create uncontrolled duplicate outputs.
- **Chemistry/materials work:** Preserve assumptions and distinguish **original calculated data**, **curated/derived values** and **new model predictions**.
- **Polymer/hydrogel connection:** Extends the restart-safe, provenance-aware workflow style used in the thermoresponsive hydrogel project.
- **Planned outputs:** `requirements.txt`, `run_manifest.json`, `validation_summary.csv`, reproducibility instructions and optional tests.
- **Completion check:** A reader can obtain appropriately licensed inputs and understand each step, its outputs and unresolved limitations.

## 7. Planned repository structure

This layout is **proposed**, not yet fully created:

```text
Project_Machine_learning_and_first-principles_guided_desig/
├── README.md
├── requirements.txt
├── data/
│   ├── raw/                       # Local originals; do not upload without rights review
│   ├── interim/                   # Audited, source-linked working tables
│   └── processed/                 # Validated outputs where redistribution is permitted
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
├── docs/
│   ├── scientific_glossary.md
│   ├── data_dictionary.csv
│   └── unresolved_review_items.csv
├── reports/
│   ├── qc/
│   └── figures/
└── tests/
```

## 8. Simple glossary: chemistry and data science

| Term | Plain-language meaning | Why it matters |
|---|---|---|
| **BaTiO₃** | Barium titanate, an inorganic ceramic oxide. | The material being studied; it is not a polymer. |
| **Doping** | Replacing part of one element with another. | Sr/La fractions define the investigated composition changes. |
| **Perovskite A-site/B-site** | Different positions in the crystal lattice. | Features must describe the correct atomic sites. |
| **DFT** | Quantum-mechanical calculations used to estimate material properties. | Computational results must not be labelled experimental measurements. |
| **VCA** | Virtual Crystal Approximation for modelling mixed atomic sites. | It is an approximation requiring documented assumptions. |
| **Formation energy** | Calculated energy relative to defined elemental reference states. | A modelling target, not direct proof that a material will be easy to make. |
| **Descriptor / feature** | A numerical property used as input to a model. | Definitions and provenance determine whether it is scientifically meaningful. |
| **MAE** | Mean absolute error between predictions and reference values. | Its unit matches the target, such as eV/atom. |
| **Provenance** | Evidence of where a value came from and what happened to it. | Enables independent checking and reliable joins. |
| **Data leakage** | Information that should not be available to the model enters training. | Can make reported accuracy look misleadingly strong. |
| **Generalisation** | How well a model works on cases unlike its training examples. | Central to responsible materials screening. |

## 9. Proposed tools

Python · Jupyter Notebook · pandas · NumPy · Matplotlib · scikit-learn · optional XGBoost and SHAP · Git · GitHub.

Only tools actually used will be added to the completed environment requirements. This repository does **not** claim to perform new DFT calculations or physical robotic experiments.

## 10. Scientific integrity, privacy and data reuse

- Preserve source files unchanged and record checksums.
- Keep original calculated quantities separate from standardised values and new predictions.
- Never invent missing results, measurement records, experimental sample IDs or correspondence between sheets.
- Keep unresolved scientific uncertainties—especially numeric headers, the meaning of `S4` and `S2`–`S3` linkage—clearly documented.
- Explain all transformations, unit decisions, source assumptions and limitations.
- Do not publish private correspondence, personal contact details or non-public researcher information in this repository.
- Link to the publisher's complete author list through the original DOI rather than repeating individual co-author names in project prose.
- Give appropriate credit under the applicable licence, distinguish original source research from independent contributions and avoid implying endorsement.
- Review the **supplementary file's own licence** before posting the workbook, figures or substantial data extracts publicly. Public download access is not, by itself, permission to redistribute.
- If the data licence is uncertain, keep the source files locally and publish original code, source citations and download instructions instead.

## 11. Current project status and next steps

**Current stage: Planning and initial source-structure inspection.** The workbook's S1–S4 sheet dimensions have been identified, and the scientific documentation has been reviewed to design the workflow. **Full row-level QC, schema verification, standardisation, composition-based linkage, exploratory analysis and ML modelling have not yet been completed.**

**Immediate next steps:**

1. Implement **Phase 00** to document source files, provenance, licence checks and the scientific research scope.
2. Implement **Phase 01** to examine every workbook column, record missingness and investigate the purpose of `S4`.
3. Establish scientifically defensible column mappings and record linkage before proceeding to transformations or machine learning.
4. Update this README after each phase is actually executed and reviewed.

## 12. Attribution and research independence

This is an **independent educational and professional portfolio project** informed by the peer-reviewed article and its published supplementary materials, with methodology adapted from my earlier polymer and hydrogel data curation work.

The **original research team retains credit for its publication, scientific calculations, findings and supporting materials**. The complete bibliographic record and author list are available through the [original article DOI](https://doi.org/10.1063/5.0314819).

The data curation methods, code, documentation, validation reports and analyses developed for this repository will be identified as independent contributions. **This project does not represent an official institutional collaboration, research appointment, endorsement or access to internal laboratory systems.** Reuse of original source material remains subject to its applicable licence and any additional permissions required.



