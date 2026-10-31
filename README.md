# BaTiO₃ Ceramic Materials Data Curation and AI-Ready Workflow Engineering

**Repository:** `Project_Machine_learning_and_first-principles_guided_desig`  
**Research focus:** Materials informatics · Scientific data curation · Quality assurance · Reproducible Python workflows  
**Material system:** Sr/La-substituted barium titanate, `(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`  
**Status (31 October 2026):** Source materials acquired and preliminary workbook structure reviewed; implementation and validation phases are planned.

## 1. Project overview

This independent project develops a reproducible data-curation and workflow-engineering pipeline for computational ceramic materials research. It uses the supplementary materials associated with **Guo et al. (2026), *Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications*.**

The source study investigates how strontium (Sr) and lanthanum (La) substitution affects the calculated formation energy of BaTiO₃-based compositions, integrating first-principles calculations, materials descriptors and machine-learning methods.

The project focuses on the data infrastructure supporting this analysis: source provenance, scientific metadata, composition validation, feature definitions, reliable dataset linkage, analysis-ready records and reproducible computational workflows. Machine-learning benchmarks and candidate screening form an optional extension after dataset validation.

### Research objective

**To construct a scientifically validated, traceable and reproducible data pipeline linking ceramic compositions, material descriptors and calculated formation-energy records, with documented readiness for downstream machine-learning analysis.**

### Scope

- Curate and validate the supplementary computational datasets and their accompanying scientific documentation.
- Preserve the distinction between original first-principles results, processed data and independently generated model outputs.
- Evaluate whether the supplied data support reliable feature–target linkage and appropriate predictive validation.
- Produce structured datasets, data dictionaries, QC reports and executable Python notebooks with source-to-output traceability.

## 2. Research source and data access

**Publication:** Guo et al. (2026). *Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications*. **Journal of Applied Physics, 139**, 064101.  
**Article:** https://doi.org/10.1063/5.0314819  
**Official supplementary materials:** https://doi.org/10.60893/figshare.jap.c.8234602

The source materials used for the project are:

| Source file | Contents and intended use |
|---|---|
| `Supplementary Dataset.xlsx` | Composition records, materials descriptors and supplementary numerical data across sheets `S1`–`S4`. |
| `Supplementary information.docx` | Formation-energy and thermodynamic methodology, feature abbreviations, machine-learning settings, comparative results and supporting figures. |
| Published article | Scientific context, first-principles and ML methodology, reported findings and reference results. |

The article is identified as CC BY 4.0 except where otherwise noted. Licensing and redistribution permissions for separately hosted supplementary files will be assessed independently before any original source data are published in this repository.

## 3. Preliminary dataset inventory

An initial workbook inspection established the following structure. These counts are **file-inventory observations**, not completed data-quality findings.

| Sheet | Data rows | Columns | Working interpretation | Outstanding verification |
|---|---:|---:|---|---|
| `S1` | 30,301 | 100 | Candidate composition and descriptor space | Field names, composition mapping and feature definitions |
| `S2` | 231 | 102 | Computed compositions, descriptors and formation-energy information | Target location, units, unique keys and provenance |
| `S3` | 231 | 82 | Selected machine-learning input features | Correspondence with `S2` target records |
| `S4` | 231 | 10 | Additional supplementary data | Scientific content and role in the overall workflow |

The supplementary documentation identifies **82 retained input features** after removing constant, descriptive and target fields from a larger feature set. The precise spreadsheet-to-feature mappings require verification during the audit.

The 30,301 candidate entries in `S1` are not equivalent to 30,301 independently calculated formation-energy labels. The smaller DFT-labelled dataset and the larger candidate-screening space will be maintained as distinct data populations.

## 4. Project objectives

1. Establish a documented source registry, file inventory and computational-data provenance framework.
2. Design a consistent scientific schema for compositions, descriptors, calculated properties and model outputs.
3. Apply systematic numerical, structural and composition-level quality checks.
4. Standardise validated fields while preserving source values, units and transformation history.
5. Establish defensible record linkage between the supplementary sheets and assess unresolved mappings.
6. Generate analysis-ready datasets and exploratory materials-informatics summaries.
7. Evaluate feature quality, leakage risk, model-validation design and composition-space coverage.
8. Develop optional ML benchmarks and screening only where the validated datasets support them.
9. Package the pipeline into repeatable, documented Python notebooks and reusable validation outputs.

## 5. Research workflow and phase deliverables

`Source registration → Data audit → Schema design → Scientific QC → Standardisation → Record linkage → Exploratory analysis → ML readiness → Optional modelling → Reproducibility review`

The phases below define the implementation plan. Notebook results and completion statuses will be updated following execution and verification.

### Phase 00 — Research scope and source registry

**Objective:** Establish the scientific boundaries, provenance and governance of all input materials.

- Register source identifiers, publication links, file versions, acquisition dates, file hashes and reuse conditions.
- Document the Sr/La-substituted BaTiO₃ composition space, computational target and source-study assumptions.
- Define the datasets, expected outputs and criteria for progressing through subsequent phases.

**Planned outputs:** `source_registry.csv`, `research_scope.md`, `source_manifest.json`.

### Phase 01 — Source-data and workbook audit

**Objective:** Characterise the supplementary files and identify structural or metadata issues prior to transformation.

- Inventory workbook sheets, row and column counts, headers, inferred data types, missingness and duplicate candidates.
- Examine column semantics against the article and supplementary feature definitions.
- Document unresolved fields, including numerical column headers and the role of `S4`.

**Planned outputs:** `workbook_inventory.csv`, `column_inventory.csv`, `source_audit_report.md`.

### Phase 02 — Scientific schema and data dictionary

**Objective:** Define an interoperable data model for the computational ceramic records.

- Specify entities and relationships for compositions, descriptors, DFT-derived targets, predictions, source records and QC findings.
- Map the perovskite A-site composition `(Ba, Sr, La)`, B-site `(Ti)` and oxygen sublattice to verified descriptors.
- Define fields, scientific units, identifiers, valid ranges, nullable values and provenance attributes.

**Planned outputs:** `schema_design.md`, `data_dictionary.csv`, `schema_relationships.md`.

### Phase 03 — Composition validation and data quality control

**Objective:** Assess data integrity and chemical consistency while preserving the unmodified source records.

- Test missing values, data types, duplicate records, key uniqueness and numerical inconsistencies.
- For confirmed composition fields, validate `x ≥ 0`, `y ≥ 0` and `x + y ≤ 1` in `(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`.
- Flag outliers, ambiguous labels and assumptions requiring scientific review; retain a structured record of findings and dispositions.

**Planned outputs:** `qc_findings.csv`, `composition_validation.csv`, `quality_summary.md`.

### Phase 04 — Standardisation and descriptor documentation

**Objective:** Establish consistent representations of validated compositions, calculated quantities and model input features.

- Harmonise verified column names, numerical types, missing-value conventions and composition identifiers.
- Document descriptor definitions, including site-specific elemental properties, ionic radii and electronegativity measures where supported by the source documentation.
- Preserve reported units such as **eV/atom** for formation energy, alongside any applicable conversion and transformation records.

**Planned outputs:** `composition_standardised.csv`, `feature_dictionary.csv`, `transformation_log.csv`.

### Phase 05 — Provenance, record linkage and analysis-ready evidence

**Objective:** Reconstruct and validate the relationships between compositions, descriptor matrices and calculated targets.

- Assess join keys and composition-based matching between `S2`, `S3` and other relevant sheets.
- Quantify match coverage, duplicate-key conflicts, unmatched records and unresolved scientific associations.
- Generate an analysis-ready evidence table only when feature–target correspondence has been substantiated.

**Planned outputs:** `linkage_summary.csv`, `unresolved_review_items.csv`, and conditional `analysis_ready_evidence.csv`.

### Phase 06 — Exploratory materials-informatics analysis

**Objective:** Characterise the validated composition space and relationships among descriptors and calculated material properties.

- Examine Sr/La composition distributions, missingness, descriptor correlations and formation-energy trends.
- Evaluate potential relationships involving composition, ionic radius, electronegativity and other verified features.
- Report figure-level provenance, units, sample coverage and interpretation limits.

**Planned outputs:** `eda_summary.md`, `composition_space.png`, `formation_energy_distribution.png`, `feature_correlations.png`.

### Phase 07 — Machine-learning readiness and validation strategy

**Objective:** Determine whether the curated dataset supports meaningful and reproducible predictive evaluation.

- Review the feature matrix, target correspondence, constant or redundant features, potential target leakage and sample size.
- Design baseline and composition-aware validation strategies, subject to the available data and chemical coverage.
- Assess extrapolation risks associated with candidate compositions outside the training region.

**Planned outputs:** `ml_readiness_report.md`, `leakage_audit.csv`, `split_plan.json`.

### Phase 08 — Optional predictive benchmarking and composition screening

**Objective:** Assess reproducible formation-energy prediction after completion of the relevant data-quality and validation checks.

- Compare a reference baseline with suitable regressors, potentially including linear models, random forest and XGBoost.
- Report MAE, RMSE and R² on clearly defined validation sets, together with model limitations and error analyses.
- Apply a validated model to candidate compositions only where input-feature compatibility has been established; distinguish these predictions from source DFT results and the paper's reported metrics.

**Planned outputs:** `benchmark_results.csv`, `prediction_audit.csv`, conditional `candidate_screening.csv`, `model_card.md`.

### Phase 09 — Reproducibility, testing and repository release

**Objective:** Deliver a traceable, restart-safe computational workflow suitable for independent review.

- Use relative paths, versioned dependencies, repeatable random seeds, explicit configuration and stable output locations.
- Maintain automated data checks, execution manifests and source-to-result provenance.
- Verify that notebooks execute consistently from a clean environment and that regenerated outputs correspond to the documented transformations.

**Planned outputs:** `requirements.txt`, `run_manifest.json`, `validation_summary.csv`, execution instructions and supporting tests.

## 6. Planned repository structure

```text
Project_Machine_learning_and_first-principles_guided_desig/
├── README.md
├── requirements.txt
├── data/
│   ├── raw/                         # Source inputs retained locally pending rights review
│   ├── interim/                     # Audited and source-linked working records
│   └── processed/                   # Validated and appropriately distributable outputs
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
│   ├── data_dictionary.csv
│   └── unresolved_review_items.csv
├── reports/
│   ├── qc/
│   └── figures/
└── tests/
```

Folders and phase notebooks will be added as implementation progresses.

## 7. Technical environment

**Planned tools:** Python, Jupyter Notebook, pandas, NumPy, Matplotlib, scikit-learn and, where required, XGBoost and SHAP. Git and GitHub will provide version control and project documentation.

The dependency list will be finalised against the executed notebooks rather than populated with unused packages.

## 8. Data integrity and responsible reuse

- Retain source data without modification and record file identifiers and checksums.
- Maintain traceable transformations and separate source calculations, standardised records and independently generated predictions.
- Record ambiguous mappings, incomplete metadata and unresolved quality findings without introducing unsupported values.
- Document model-evaluation assumptions, split design and any limitations in composition-space coverage.
- Verify dataset-specific reuse and redistribution conditions before publishing original supplementary files or substantive extracts. Where permissions are unclear, provide links to the official source and publish original code and documentation instead.

## 9. Project status and next steps

**Completed to date:** Research scope, source acquisition, review of supplementary documentation and preliminary inventory of workbook sheets `S1`–`S4`.

**Next stages:** Implement Phase 00 and Phase 01; establish verified field semantics and quality-control findings; progress through schema design, standardisation and linkage before any predictive modelling. Status summaries and results will be updated as phases are executed.

## 10. Citation and project independence

**Reference:** Guo et al. (2026). *Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications*. *Journal of Applied Physics*, **139**, 064101. https://doi.org/10.1063/5.0314819

The original publication and accompanying research materials are credited to their authors and rights holders. This repository documents an **independent materials-data curation and computational workflow project**; it is not an official collaboration with, or endorsement by, the source research team or its affiliated institutions.




