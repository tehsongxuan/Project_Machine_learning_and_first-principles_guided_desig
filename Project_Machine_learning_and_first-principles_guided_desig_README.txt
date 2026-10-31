# BaTiO₃ Ceramic Materials Data Curation and AI-Ready Workflow Engineering

**Working repository:** `Project_Machine_learning_and_first-principles_guided_desig`  
**Project type:** Independent materials-data curation, scientific validation and reproducible Python workflow portfolio  
**Scientific system:** Sr/La-doped barium titanate, `(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`  
**Project status (31 October 2026):** Source files acquired; initial workbook structure inspected. All analytical phases below are **planned**, not completed.

## Overview — what are we trying to do?

This project aims to turn the supplementary materials accompanying a published BaTiO₃ machine-learning study into a **clearly documented, scientifically checked and reproducible data workflow**. The study uses first-principles (DFT/VCA) calculations to obtain formation energies for selected BaTiO₃ compositions, then trains machine-learning models to help screen a much larger composition space.

**In simple terms:** Different amounts of strontium (Sr) and lanthanum (La) are substituted for barium (Ba) in a ceramic. We want to understand which compositions were calculated, which properties were predicted, how trustworthy the data are, and how Python can make the whole process easy to check and repeat.

The priority is **data curation and workflow engineering first**. Reproducing the article's machine-learning models is an optional later stage—not a claim that the published study or CERAMIT's private self-driving laboratory has already been reproduced.

### The scientific question

How can a transparent and reusable data pipeline help scientists study the relationship between **chemical composition, materials descriptors and DFT-calculated formation energy** in Sr/La-doped BaTiO₃?

The published work also studies ferroelectric behaviour, elastic properties and temperature-dependent thermodynamics for selected compositions. These broader properties are discussed in the supplementary notes, but are **not automatically present as row-level labels in the supplied spreadsheet**.

## Research source and uploaded files

**Original article:** Chong Guo et al. (including Chee Kiang Ivan Tan), *Machine learning and first-principles guided design of BaTiO₃-based materials for capacitor applications*, *Journal of Applied Physics* **139**, 064101 (2026).  
**Article DOI:** https://doi.org/10.1063/5.0314819  
**Official supplementary collection:** https://doi.org/10.60893/figshare.jap.c.8234602

**Files used to plan this project:**

- `Supplementary Dataset.xlsx` — research workbook provided with the paper.
- `Supplementary information.docx` — calculation procedures, feature abbreviation explanations, regression settings, reported results and supplementary tables/figure.
- `Machine_learning_and_first-principles_guided_desig.pdf(1).crdownload` — user-provided article; the file is readable as a PDF despite the incomplete-download filename extension. Verify provenance and completeness before archiving it as a reference.
- `Thermoresponsive Hydrogel Data Curation and Workflow Engineering README.txt` — structural template for the independent project approach, not a BaTiO₃ data source.

### Initial workbook inventory (structure only; **not a completed data audit**)

| Workbook sheet | Observed data rows | Observed columns | Initial interpretation | Required verification |
|---|---:|---:|---|---|
| `S1` | 30,301 | 100 | Screenable composition/descriptor space | Determine meaning of all numeric headers; identify index and actual feature columns. |
| `S2` | 231 | 102 | DFT-labelled compositions and associated descriptors | Confirm formation-energy column, units, source identities and all descriptor mappings. |
| `S3` | 231 | 82 | Selected ML input features described by the article | It is **features only**; verify how targets must be linked from S2. |
| `S4` | 231 | 10 | Additional table included in the supplied workbook | **Meaning not yet established**; do not infer its role, overwrite or discard it. |

**Important:** The column headers in the supplied workbook are largely numeric identifiers rather than human-readable scientific names. The supplementary document's Table S1 explains chemical feature abbreviations, but a complete mapping from workbook headers to scientific field definitions must be checked rather than assumed. The paper describes 231 calculated compositions, 82 model inputs and predictions across 30,301 candidates. **The 30,301 candidates are not 30,301 independent DFT formation-energy labels.**

## Why this connects to my polymer and hydrogel projects

My earlier projects focus on polymer glass transition temperature (Tg) prediction, collagen hydrogel rheology and thermoresponsive hydrogel/bioink data curation. This new project transfers **data-science methods**, while carefully recognising that **ceramics and polymers obey different materials physics**.

| Data-science concept | In polymer/hydrogel research | In the BaTiO₃ study | What transfers—and what does not |
|---|---|---|---|
| **Composition representation** | Monomers, repeat-unit structure, block ratios, crosslink chemistry | Ba/Sr/La amounts at the ceramic A-site | Both need correct chemical representation. A doped crystalline oxide is **not** a polymer chain. |
| **Features / descriptors** | RDKit descriptors and Morgan fingerprints used to predict polymer Tg | Elemental and site-weighted properties such as atomic/ionic radii and electronegativity | Feature generation, naming, documentation and leakage checks transfer; fingerprints and site descriptors are not interchangeable. |
| **Property / target** | Tg (°C), a kinetic glass-transition measure connected with segmental mobility | DFT formation energy (eV/atom), relative to specified elemental reference states | Both may be predicted with regression; **formation energy is not Tg**, and it is not the same as a measured processing temperature. |
| **Materials response** | Hydrogel G′, G″, tan δ and temperature-dependent sol–gel response | Elastic moduli, ferroelectric response, temperature-dependent thermodynamic quantities | Scientific interpretation and unit tracking transfer. Oscillatory rheology is not directly equivalent to a static ceramic elastic modulus. |
| **Data provenance** | Link a measurement to a sample, treatment, instrument and source file | Link a composition to DFT calculation/assumptions, derived descriptors and predicted values | Never treat similar row order or filenames as proof of identity. |
| **Generalisation** | Polymer-family holdout to test unseen structures | Test across dopant ranges or composition regions | A high random-split R² may not show performance on unseen composition regions. |
| **Workflow automation** | Repeatable hydrogel extraction, QC and linkage | Repeatable spreadsheet ingestion, composition checks, feature processing and ML validation | Both benefit from scripts that work from a fresh environment and produce QC reports. |

### Three materials-science ideas to keep separate

1. **Composition versus processing.** Changing Sr/La fractions changes the ceramic chemistry. This is different from changing a polymer's sterilisation treatment, though both can influence material properties.
2. **Formation energy versus functional performance.** Formation energy is a calculated indicator of stability relative to chosen references. By itself, it does not guarantee ease of synthesis, optimal dielectric response or good capacitor performance.
3. **DFT calculation versus laboratory measurement.** Most row-level targets in this dataset come from computational calculations, not directly from a robotic instrument. The project must never invent laboratory sample IDs, experimental runs or measured outcomes.

## Project objectives

1. **Audit** original files and the meaning of their columns and sheets.
2. **Design a materials-aware schema** for compositions, descriptors, calculated targets, predictions and provenance.
3. **Validate** chemistry constraints, missingness, duplicates, numerical plausibility, units and documentation gaps.
4. **Standardise** the raw records while preserving the original source values and names.
5. **Link** S1/S2/S3 only where there is defensible composition-based evidence; keep S4 unresolved until verified.
6. **Explore** meaningful relationships between dopant fractions, descriptors and formation energy.
7. **Assess ML readiness**, including data leakage, train/test design and extrapolation risk.
8. **Optionally model and screen** new compositions using clearly labelled independent results.
9. **Automate and document** a restart-safe, independently reproducible Python workflow.

## Planned workflow — the purpose of every phase

`00 Scope → 01 Audit → 02 Schema → 03 Quality control → 04 Standardisation → 05 Provenance/linkage → 06 Exploratory analysis → 07 ML readiness → 08 Optional modelling/screening → 09 Reproducibility and release`

### Phase 00 — Research scope and source registry

**Simple purpose:** Decide exactly what scientific question we are answering and where every source came from.

- **Data science:** Record article DOI, supplementary links, filenames, file checksums, acquisition dates, data permissions, source versions and planned analyses.
- **Materials science:** Define the system `(Ba₁₋ₓ₋ᵧSrₓLaᵧ)TiO₃`, the distinction between computed formation energy and other ferroelectric/dielectric properties, and the study's scope.
- **Connection to polymer projects:** Just as a hydrogel study needs the polymer formulation and experimental treatment clearly defined, a ceramic study needs the dopant chemistry and calculation context clearly defined.
- **Planned outputs:** `source_registry.csv`, `research_scope.md`, `source_manifest.json`.
- **Success check:** No dataset is described as experimental, author-created by me, or a CERAMIT laboratory dataset without evidence.

### Phase 01 — Source-file and workbook audit

**Simple purpose:** Find out what is actually inside the supplied Excel workbook before cleaning or modelling anything.

- **Data science:** Inventory S1–S4, shapes, numeric headers, empty cells, candidate keys, file-level metadata and possible record overlaps; save an audit that does not modify the original workbook.
- **Materials science:** Identify which columns represent Ba/Sr/La fractions, calculated energies and elemental descriptors. Inspect whether data describe DFT outputs, features or predictions.
- **Connection to polymer projects:** Similar to checking raw rheology workbooks for units, headers, different experimental sweeps and ambiguous identifiers before making a tidy dataset.
- **Planned outputs:** `workbook_inventory.csv`, `raw_column_inventory.csv`, `initial_data_audit.md`.
- **Success check:** Record the observed 30,301/231/231/231 sheet row counts and explicitly flag unresolved S4 and unidentified numeric headers.

### Phase 02 — Materials-aware schema and data dictionary

**Simple purpose:** Give each scientific value a clear name and put different kinds of information in the right places.

- **Data science:** Propose separate tables for `composition_records`, `descriptor_values`, `calculation_targets`, `model_predictions`, `source_records` and `qc_findings`. Define unique IDs, allowed types, units and join keys.
- **Materials science:** Keep the A-site composition (Ba, Sr, La) distinct from the B-site (Ti), X-site (O), site-weighted descriptors and DFT formation-energy targets.
- **Connection to polymer projects:** This resembles separating a hydrogel formulation, treatment, sample and rheological measurements instead of putting unrelated information into one untraceable table.
- **Planned outputs:** `schema_design.md`, `data_dictionary.csv`, `schema_relationships.md`.
- **Success check:** Every curated field has a scientific definition or an explicit `unresolved` status; do not invent names for numbered columns.

### Phase 03 — Data quality control and chemistry constraints

**Simple purpose:** Catch mistakes or uncertainties before they silently reach the AI model.

- **Data science:** Check blanks, infinities, duplicates, inconsistent types, suspicious outliers, conflicting labels and repeated composition fingerprints. Keep a severity-ranked QC log.
- **Materials science:** Check that Sr and La fractions are non-negative, `x + y ≤ 1`, and `Ba fraction ≈ 1 − x − y` after confirming which columns represent these quantities. Document dopant valence/charge-compensation questions, but do not impose an unverified defect model.
- **Connection to polymer projects:** Just as invalid SMILES, duplicate polymer structures and conflicting Tg values require review, impossible dopant fractions or inconsistent computed energies require review.
- **Planned outputs:** `qc_findings.csv`, `composition_validation.csv`, `quality_summary.md`.
- **Success check:** A failed check becomes a visible finding; source values remain intact, and no data are silently deleted or “corrected.”

### Phase 04 — Standardisation and feature interpretation

**Simple purpose:** Make information consistent, interpretable and ready for comparison without changing its scientific meaning.

- **Data science:** Map verified numeric headers to descriptive names; standardise units, data types, missing-value conventions and composition notation; generate stable keys and a transformation log.
- **Materials science:** Keep total energy and formation energy distinct. Preserve the reported formation-energy unit **eV/atom**; do not mix it with eV/formula-unit, hydrogel rheology units (Pa), or polymer Tg (°C). Explain site-weighted atomic descriptors and the difference between constant and variable features.
- **Connection to polymer projects:** Equivalent to standardising polymer Tg units and rheology axes, but using ceramic-specific chemistry and calculated-energy conventions.
- **Planned outputs:** `composition_standardised.csv`, `feature_dictionary.csv`, `transformation_log.csv`.
- **Success check:** Every transformed value can be traced to an unchanged original value and a documented conversion or mapping.

### Phase 05 — Provenance, composition linkage and evidence layer

**Simple purpose:** Prove which records belong together instead of joining spreadsheets simply because rows appear in the same order.

- **Data science:** Build composition-based keys from verified Ba/Sr/La fractions and other justified fields; test key uniqueness and match coverage across sheets. Link the 82 S3 feature columns to the correct S2 formation-energy target **only after matching has been verified**.
- **Materials science:** Preserve calculation provenance, crystal assumptions (where documented), feature origins and units. A computational composition is not automatically a physical ceramic sample.
- **Connection to polymer projects:** This matches your hydrogel rule: do not infer physical-sample linkage merely from similar filenames or position in a workbook.
- **Planned outputs:** `linkage_summary.csv`, `model_ready_evidence_layer.csv` (only if verified), `unresolved_review_items.csv`.
- **Success check:** Unmatched, ambiguous and duplicate links are reported; S4 is excluded from downstream modelling until its meaning is established.

### Phase 06 — Exploratory materials analysis

**Simple purpose:** Understand what the verified data say before asking machine learning to predict anything.

- **Data science:** Plot composition coverage, distributions of DFT formation energies, missingness, descriptor correlation patterns and group-level trends. Compare observable relationships without claiming causality.
- **Materials science:** Explore how different Sr/La fractions relate to calculated energies; interpret ionic radius, electronegativity or other descriptors only if their definitions have been confirmed. Keep discussions of ferroelectricity and temperature response tied to actual available evidence.
- **Connection to polymer projects:** Similar to exploring polymer Tg across families or hydrogel G′/G″ across test conditions before building a model. The plots are different because the material-property physics differ.
- **Planned outputs:** `eda_summary.md`, `figures/composition_space.png`, `figures/formation_energy_distribution.png`, `figures/feature_correlations.png`.
- **Success check:** Figures identify units, source, data subset and limitations. No property trend is presented as an experimentally verified mechanism merely because it appears in a correlation plot.

### Phase 07 — Machine-learning readiness and leakage audit

**Simple purpose:** Test whether a trustworthy ML experiment is possible with just 231 labelled compositions.

- **Data science:** Confirm that target values are not among input features; audit constant or near-duplicate columns; check feature definitions, small-data uncertainty and split strategy. Document the paper's 4:1 train/test split and separately consider tougher composition-region holdouts.
- **Materials science:** Ask whether a model learns chemistry trends it can reasonably interpolate or is being asked to extrapolate to dopant combinations absent from training. Distinguish feature correlations from physical mechanisms.
- **Connection to polymer projects:** Mirrors the difference between your strong polymer random-split result and substantially weaker polymer-family holdout. The key question is **where predictions are trustworthy**, not just whether R² is high.
- **Planned outputs:** `ml_readiness_report.md`, `feature_leakage_audit.csv`, `split_plan.json`.
- **Success check:** Modelling is a **go** only when target linkage, units, data quality and a reproducible validation strategy are confirmed.

### Phase 08 — Optional ML benchmarks and composition screening

**Simple purpose:** Once the data are reliable, test whether models can learn useful relationships and flag uncertain predictions.

- **Data science:** Start with a simple baseline, then consider linear regression, random forest or XGBoost. Report MAE, RMSE and R² on held-out data, plus error by composition region and uncertainty/novelty indicators. Only screen the S1 candidate space after verifying the feature schema and model applicability.
- **Materials science:** The prediction target is **DFT-calculated formation energy**, not measured capacitance, dielectric loss or synthesis success. A prediction is a screening suggestion, not a confirmed discovery.
- **Connection to polymer projects:** Reuses regression/model-evaluation experience from polymer Tg work, while changing the chemical representation and target variable.
- **Planned outputs:** `benchmark_results.csv`, `prediction_audit.csv`, `candidate_screening.csv`, `model_card.md`.
- **Success check:** Clearly distinguish my independently reproduced metrics from the paper's reported XGBoost MAE **0.105 eV/atom**, RMSE **0.162 eV/atom**, R² **0.989**. No equivalence is claimed unless preprocessing, splits and labels are demonstrably comparable.

### Phase 09 — Workflow engineering, reproducibility and portfolio release

**Simple purpose:** Make the work repeatable by another scientist without manually fixing paths, changing notebook cells or guessing data origins.

- **Data science:** Run each phase from project-root-relative paths; use deterministic random seeds, environment requirements, validated output schemas, QC summaries and a run manifest. Ensure reruns do not create duplicate records or overwrite raw sources.
- **Materials science:** Preserve scientific assumptions, distinguish raw/calculated/derived/predicted records and show how a new computational composition could be reviewed in a future materials-discovery workflow.
- **Connection to polymer projects:** Same restart-safe engineering approach as your hydrogel curation notebooks, now applied to computational ceramics.
- **Planned outputs:** `requirements.txt`, `run_manifest.json`, `validation_summary.csv`, clear GitHub documentation and optional reproducibility tests.
- **Success check:** Another person can follow the README, obtain authorised input files, run the pipeline and inspect all warnings, without assuming an actual autonomous laboratory was operated.

## Suggested repository structure (planned, not yet implemented)

```text
Project_Machine_learning_and_first-principles_guided_desig/
├── README.md
├── requirements.txt                 # Added when dependencies are established
├── data/
│   ├── raw/                         # Locally retained source files; check redistribution rights
│   ├── interim/                     # Audit-ready tables and unmodified extractions
│   └── processed/                   # Validated, traceable derived outputs
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
└── tests/                           # Added as validation code is developed
```

## Plain-language scientific glossary

| Term | Simple explanation | Important caution |
|---|---|---|
| **BaTiO₃** | Barium titanate, a ceramic oxide used in dielectric/electronic-materials research. | Not a polymer. |
| **Doping** | Replacing part of one element with another to change a material's composition and properties. | It can affect charge balance and structure; a formula alone does not describe all defects. |
| **A-site / B-site** | Different positions occupied by elements in the perovskite crystal structure. | Site descriptors are not polymer molecular fingerprints. |
| **DFT** | A quantum-mechanical calculation method used to estimate material energies and properties. | A calculated value is not the same as a measured laboratory value. |
| **VCA** | Virtual Crystal Approximation; models mixed atomic sites using an averaged representation. | A useful approximation, not an explicit atom-by-atom defect model. |
| **Formation energy** | A calculated energy relative to defined reference elements, used when reasoning about stability. | It is not direct proof of synthesizability or dielectric performance. |
| **Descriptor / feature** | A numeric description of a material supplied to a model. | Must be defined, correctly linked and free of target leakage. |
| **MAE** | Typical absolute prediction error, in the units of the target. | Compare only using compatible test data and units. |
| **Provenance** | A record of where data came from and how they were changed. | Critical for scientific trust. |
| **Model generalisation** | Whether a model works on materials unlike those it was trained on. | Random test splits may overstate performance in new chemistry regions. |

## Tools (proposed)

Python · Jupyter Notebook · NumPy · pandas · Matplotlib · scikit-learn · optional XGBoost / SHAP · Git · GitHub. Tools will be added only when required by a validated project phase; **no first-principles calculations or robotic experiments are claimed**.

## Scientific data integrity and publication rules

- Preserve the original workbook and supplementary document unchanged; store cryptographic file checksums.
- Keep raw values, calculated DFT outputs, derived descriptors and ML predictions separately labelled.
- Explain units, transformations, assumptions, potential data leakage and unresolved scientific questions.
- Treat `S4` and unexplained numeric column labels as **unresolved** until independently identified.
- Never join S3 to S2 by row position alone without verifying that the compositions align.
- Do not invent missing DFT energies, experimental measurements, sample IDs, synthesis conditions or physical lab records.
- Never describe this repository as a reproduction of CERAMIT, a self-driving lab, or a collaboration with A*STAR/IMRE.
- Respect the original publisher/data licence; do not redistribute input source files on GitHub unless explicitly permitted. Prefer download instructions and code-only reproduction.
- Distinguish published paper performance from results obtained independently in this project.

## Current project status and next action

**Planning / source-structure inspection stage.** I have the article, `Supplementary information.docx`, and `Supplementary Dataset.xlsx`; a limited structural check confirms workbook sheets S1–S4 and their row/column dimensions. **No completed row-level QC, column mapping, linkage, exploratory analysis, prediction model or scientific conclusion is claimed.**

**First action:** Implement Phase 00 and Phase 01. Confirm the workbook's numeric columns and S4 meaning before any transformation, merging or modelling. The next decision will be whether S2's formation-energy targets can be linked to S3's 82 input features with scientifically verified composition keys.

## Attribution and independence

The publication and supplied research data are credited to their original authors. The project is an **independent educational and professional portfolio exercise**, inspired by the source paper and the workflow style of the user's earlier thermoresponsive hydrogel data-curation project. It is **not** an A*STAR/IMRE research appointment, an official collaboration with Dr Ivan Tan, or a representation of internal CERAMIT laboratory systems.
