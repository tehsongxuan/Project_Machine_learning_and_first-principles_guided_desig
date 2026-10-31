# Thermoresponsive Hydrogel Data Curation and Workflow Engineering

**An independent, reproducible scientific Python project for organising, validating and connecting polymer-characterisation, rheology, imaging and biological evidence.**

**Project status:** Source collection and initial archive-level inspection completed; scientific data extraction, standardisation, validation and cross-technique linkage are in development.

> **Central objective:** Convert heterogeneous experimental files into structured, quality-controlled and traceable materials datasets, while preserving the scientific meaning and limitations of the original measurements. This is a data-curation and workflow-engineering project, **not** a predictive polymer-design or machine-learning modelling study at this stage.

## Quick navigation — Phase 0 publication

The following Phase 0 file links use the canonical repository paths described in the [Phase 0 publication checkpoint](#phase-0-publication-checkpoint). **Repository file links become accessible after the corresponding artefacts have been committed to `main`.** The editable notebook is presently located at the repository root; the larger `notebooks/` directory shown later in this README remains a proposed structure for subsequent phases.

- [Repository home](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation)
- [Phase 0 — scientific scope and publication checkpoint](#phase-0-publication-checkpoint)
- [Phase 0 — executable Jupyter notebook](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/00_scope_and_source_registry.ipynb)
- [Phase 0 — scientific HTML report](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/reports/phase0/00_scope_and_source_registry.html)
- [View Phase 0 HTML report in a browser](https://htmlpreview.github.io/?https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/reports/phase0/00_scope_and_source_registry.html)

- [Phase 0 — scientific figures and source-register links](#phase-0-output-inventory-and-direct-file-links)
- [Phase 0 — reproducible local execution](#phase-0-environment-and-reproducibility)
- [Original experimental paper](https://doi.org/10.1021/acs.biomac.6c01032)
- [Original dataset and 13 source archives](https://zenodo.org/records/21902628)

**Phase 0 HTML link note:** Both links above open the uploaded `reports/phase0/00_scope_and_source_registry.html` file. The first opens the GitHub file page; the second renders the same HTML through an external HTML preview service.

---

## 1. Research references and original data

| Resource | Reference | Role in this project |
|---|---|---|
| Research article | [Nemati Mahand, S. *et al.* (2026), *Impact of Sterilization Techniques on the Physicochemical and Biological Properties, and 3D Printability of Thermoresponsive Hydrogels*, **Biomacromolecules**, 27, 6527–6542](https://doi.org/10.1021/acs.biomac.6c01032) | Scientific context, experimental methods, published results and interpretation |
| Original experimental dataset | [Zenodo record 21902628](https://zenodo.org/records/21902628) · [Dataset DOI](https://doi.org/10.5281/zenodo.21902628) | Deposited source files, retained under their original names |
| Journal article page | [ACS Publications](https://pubs.acs.org/doi/10.1021/acs.biomac.6c01032) | Published methods, figures, tables and article-associated information |
| Data-management framework | [FAIR Guiding Principles](https://www.go-fair.org/fair-principles/) | General principles of findable, accessible, interoperable and reusable research data |

**Attribution:** The experimental work, original data, figures and scientific conclusions belong to the cited researchers. The curation pipeline and documentation developed here are an independent educational and research-portfolio exercise. No affiliation with the original research group is implied. Usage or redistribution of original deposited files must follow the source's applicable rights and licence terms.

## 2. Project overview and scientific motivation

Synthetic thermoresponsive hydrogels are polymer systems whose physical state and mechanical response change with temperature. Their behaviour depends on the **chemical structure of the polymer**, its **molecular architecture and molar-mass distribution**, its **concentration and solvent environment**, and its **processing and measurement history**.

A useful conceptual sequence is:

**Polymer structure and composition → molecular association and self-assembly → temperature-dependent gelation → viscoelastic behaviour → printing performance and biological response**

The original study investigates how sterilisation or disinfection treatments affect three thermoresponsive polymer systems. It includes complementary characterisation methods: size-exclusion chromatography (SEC/GPC), proton nuclear magnetic resonance (¹H NMR), Fourier-transform infrared spectroscopy (FTIR), rheology, sol–gel observations, printing images and biological assessments.

These measurements answer different scientific questions. For example, SEC measures molar-mass distributions, FTIR and NMR provide chemical evidence, and rheology measures how the hydrogel resists deformation and flows. An image of a printed grid documents geometry, not molecular weight. A reliable data pipeline must **preserve these distinctions while making justified links between experimental records**.

### Research questions

1. What files, data formats, experimental treatments and metadata are present in the source deposit?
2. Which original measurements can be extracted and standardised without losing their acquisition context?
3. Where are values missing, units inconsistent, calibration details absent, or sample relationships unverified?
4. How can polymer structure, processing history, SEC, NMR, FTIR and rheology evidence be represented in linked scientific tables?
5. Can numerical measurements and suitably calibrated printing images be visualised or analysed reproducibly?
6. Which cross-technique comparisons are supported by the data, and which must remain explicitly unresolved?

## 3. Polymer systems and experimental design

| Polymer system | Molecular architecture | Thermoresponsive behaviour | Why its identity matters for curation |
|---|---|---|---|
| **Pluronic F127 (poloxamer 407)** | PEO–PPO–PEO triblock copolymer: hydrophilic poly(ethylene oxide) outer blocks and a more hydrophobic poly(propylene oxide) middle block | Temperature-dependent hydration and micellisation can lead to gel formation at suitable concentrations | Polymer grade, composition, concentration, thermal history and treatment must be retained with the measurement |
| **pMeOx-b-pnPrOzi** | Diblock poly(2-methyl-2-oxazoline)-block-poly(2-*n*-propyl-2-oxazine) | Warming can promote thermogelation through temperature-dependent self-assembly | Distinct synthesised batches are used in the published study; batch identity cannot be discarded |
| **pMeOx-b-pPheOzi-b-pMeOx** | Triblock poly(2-methyl-2-oxazoline)-block-poly(2-phenyl-2-oxazine)-block-poly(2-methyl-2-oxazoline) | **Inverse thermogelation:** the system can form a gel on cooling | Heating and cooling cannot be treated as equivalent, and the temperature of each experiment is essential metadata |

**Treatments discussed in the source study:** untreated control, autoclaving, aerobic dry heat, anaerobic dry heat, ethanol washing, UV irradiation and filtration; supplementary work includes repeated filtration, combined treatments and treatment of formulated hydrogels.

An important distinction is whether sterilisation was performed on **polymer powder**, a **dilute solution** or a **fully formulated hydrogel**. These are not interchangeable experimental conditions. For the diblock system, the study also describes **two synthesised batches**, with the filtration experiments using a different batch from several other treatment groups. Our schemas and comparisons must retain this information.

## 4. Original Zenodo archive inventory

The following are the **13 deposited ZIP archives**. Filenames, including their original spelling and punctuation, are preserved here. The internal-entry counts below are from an initial structural inspection; they **do not** represent numbers of independent experiments or biological specimens.

| Original archive name | Internal file entries | Main material | Proposed curation focus |
|---|---:|---|---|
| `Figure 2b,c,d-SEC.zip` | 6 | OriginLab SEC/GPC projects | Chromatogram and molar-mass metadata |
| `Figure S16-SEC.zip` | 3 | Additional SEC/GPC projects | Repeated-filtration comparison; overlapping projects |
| `Figure S2,3,4,11-1H NMR.zip` | 755 | Raw/processed NMR instrument directories and project files | Acquisition metadata, spectra, processing lineage |
| `Figure S5,6,7-FTIR.zip` | 64 | FTIR text exports and instrument/project files | Spectral units, chemical-characterisation QC |
| `Figure3,4,5, and S8-Rheology data.zip` | 15 | OriginLab rheology projects | Gelation, deformation, flow and recovery |
| `Figure S1 and 2b-Solgel transitions.zip` | 8 | Gelation photographs/figure images and support file | Conditions and visual observations |
| `Figure S9,10, and 6.zip` | 116 | Printing photographs and support files | Printing-image inventory and image QC |
| `Figure S21-Printing.zip` | 17 | Additional printing images and support files | Printing after hydrogel treatment |
| `Figure S 12,13,14-Bacterial gwroth test.zip` | 61 | Sterilisation-screening photographs and support files | Biological-image inventory and experiment context |
| `Figure S15-Bacterial growth after 3time Filtration.zip` | 11 | Filtration-related photographs and support file | Repeated-filtration evidence |
| `Figure S17-Autoclave followed by filtration.zip` | 8 | Sequential-treatment photographs and support file | Treatment-sequence provenance |
| `Figure S18.zip` | 5 | Hydrogel-treatment images | Formulated-hydrogel observations |
| `Figure S19,20,22-Sterilization of hydrogels by UV.zip` | 50 | Mixed SEC, NMR, FTIR, rheology, documents and images | Cross-technique processing of supplementary experiments |
| **Total** | **1,119** | **13 original archives** | **File-level inventory, not independent sample count** |

### Initial source-inspection findings

- **243 image files** (`.jpeg`, `.jpg` and `.png`) were identified, including printing photographs, experimental observation images and low-resolution previews.
- **35 OriginLab `.opju` project files** were identified. Some retain worksheets, graphs or analysis settings in a proprietary project format; complete numerical recovery must be verified before scientific processing is claimed.
- **26 numerical FTIR text spectra**, containing **60,472 numeric spectral observations**, were located. Of these, **24 specify `%T` (percentage transmittance)** and **2 specify `Abs` (absorbance)**. These are different signal representations and should not be plotted together as if their values had identical meanings.
- The deposit contains Bruker-style NMR acquisition/processing files, including `fid` records, and numerical SEC text exports in the supplementary hydrogel-treatment archive.
- Content-identical SEC projects occur in more than one archive. Such repetition must be distinguished from genuinely repeated laboratory measurements.
- Some image entries are only **160 × 120 pixels**, suitable as previews but not reliable for detailed quantitative morphology measurement.

**Status of these findings:** verified *file-structure and header-level observations*, **not** a claim that all raw instrument values, all physical sample identities or all published results have been independently reconstructed.

## 5. Data curation: preserving scientific meaning

Data curation is the process of making experimental records **understandable, consistent, traceable and reusable**. It is not simply deleting blank rows or renaming columns.

| Workstream | Plain-language purpose | Scientific/Python implementation | Planned evidence |
|---|---|---|---|
| **Source registration** | Know where every file originated | Record Zenodo DOI, archive path, original filename, size, file type and checksum | `source_registry.csv`, `source_file_inventory.csv` |
| **File integrity** | Know whether files can be opened reliably | Validate ZIP integrity; report unreadable or truncated files | `file_integrity_report.csv` |
| **Format classification** | Distinguish instrument data from previews and software files | Detect `.opju`, Bruker acquisition files, text spectra, images, PDFs and support files | `file_format_register.csv` |
| **Scientific metadata** | Record how measurements were made | Capture polymer, batch, medium, treatment, temperature, time, instrument and analysis parameters where documented | `measurement_register.csv` |
| **Schema design** | Put each kind of information in the correct table | Define data types, column meanings, units and keys | `data_dictionary.csv`, schema definitions |
| **Missing-data analysis** | Identify what is unavailable and why | Check missing values and classify `not measured`, `not determined`, `not applicable`, `unresolved` and similar cases | `missing_data_report.csv` |
| **Duplicate investigation** | Avoid double-counting | Use file hashes plus experimental context; distinguish copied files from repeat acquisitions | `duplicate_review.csv` |
| **Scientific standardisation** | Make compatible measurements comparable | Standardise valid units and labels, always retaining original values | Standardised measurement tables |
| **Provenance** | Trace every output to its evidence | Record source archive, internal path, worksheet/record and transformation steps | `record_linkage.csv`, `transformation_log.csv` |
| **Quality assurance** | Make uncertainties visible rather than hiding them | Rule-based checks and a reviewable issue register | `qc_findings.csv`, `validation_summary.csv` |

### Missing-value handling

Not every empty field represents the same situation:

- **Missing/unknown:** a value is not available from the inspected source.
- **Not determined (`ND`):** the authors could not reliably determine a value using the method or signal available.
- **Not applicable (`NA`):** the field does not apply to that observation.
- **Not printable:** an experimental outcome, not a missing numerical printing measurement to be imputed.
- **Bounded/censored result:** a reported result such as `<5` or `>250` is a limit, **not** an exact observation of 5 or 250.
- **Not yet extractable:** data may exist in a proprietary format, but a validated export has not been obtained.

The workflow will preserve the **reported text or qualifier**, the numerical bound where applicable, and a separate missingness/status code. No experimental values or sample identities will be fabricated.

### Why provenance and sample linkage matter

Two files may mention the same polymer and treatment yet belong to **different synthesis batches, measurement dates, prepared specimens or analysis runs**. A defensible scientific database must distinguish:

- **Source-supported link:** explicitly supported by a specimen identifier, instrument record, methods section or other direct evidence.
- **Candidate link:** plausible based on filenames, figure labels or treatment descriptions, but not verified.
- **Unresolved link:** insufficient information for a justified relationship.

Generated database keys are for organisation; they must not be presented as original physical-sample identifiers.

## 6. Polymer-characterisation workflows

### 6.1 SEC/GPC — molar-mass distributions

**Polymer science:** Size-exclusion chromatography separates polymer chains according to their behaviour in the chromatographic system. Appropriate calibration or detector methods support estimates of **number-average molar mass (`Mn`)**, **weight-average molar mass (`Mw`)** and **dispersity (`Đ = Mw/Mn`)**. The width and shape of a chromatogram may reveal changes in a polymer population, but detector time and signal alone are not absolute molecular-weight measurements.

**Planned processing:**

1. Catalogue OriginLab projects and readable instrument exports separately.
2. Extract elution time, detector response, channel identity, acquisition conditions and calibration details when present.
3. Preserve original signal and any separately reported baseline-corrected or normalised signal.
4. Record polymer batch and treatment conditions; identify repeat controls and possible recalibration between analytical sessions.
5. Check monotonic time axes, missing detector points, duplicated measurement files and invalid/missing molecular-weight metadata.
6. Produce original-unit chromatograms and scientifically valid comparisons; compare source-reported `Mn`, `Mw` and `Đ` only on a documented method basis.
7. Flag discrepancies between instrument exports, methods text and published tables for review rather than resolving them by assumption.

**Visualisations:** detector-response versus elution-time overlays; molar-mass/dispersity comparisons; calibration and acquisition-metadata coverage; treatment-level results with source provenance.

**Limitation:** A proprietary `.opju` file may require an Origin export or a validated compatible reader. A plotted SEC peak must not be turned into a molecular-weight distribution without appropriate calibration.

### 6.2 ¹H NMR — chemical identity and block composition

**Polymer science:** ¹H NMR detects chemically distinct proton environments. Well-resolved, correctly assigned signals can support polymer-structure identification, block-composition estimation and degree-of-polymerisation calculations. Overlapping or poorly isolated peaks limit reliable integration.

**Planned processing:**

1. Identify raw `fid` acquisitions, acquisition parameters, processed spectra and software-support files.
2. Extract documented metadata such as spectrometer frequency, solvent, temperature, acquisition name and processing settings.
3. Keep raw acquisitions separate from processed spectra and paper-reported integrated results.
4. Create spectral plots in chemical shift (ppm), with reference and phase/baseline handling clearly documented.
5. Record signal assignments and integration decisions as reviewable scientific annotations.
6. Compare molecular descriptors derived from NMR with separately determined SEC results, without assuming perfect agreement.
7. Preserve cases where block composition or end-group analysis cannot be determined reliably.

**Visualisations:** spectral overlays by treatment; acquisition-metadata coverage; annotated chemical-shift regions; data-availability matrices.

### 6.3 FTIR — chemical bonds and degradation evidence

**Polymer science:** FTIR measures vibrational responses associated with chemical bonds and functional groups. Comparing spectra before and after sterilisation may reveal changes consistent with oxidation, chemical modification or other treatment effects, subject to spectral quality and interpretation.

**Verified data issue:** The source text files contain both **percentage transmittance (`%T`) and absorbance (`Abs`)**. For a valid transmittance fraction `T`, absorbance is `A = −log10(T)`; percentage transmittance must first be converted to a fraction. Conversion is appropriate only with valid signal definitions and defensible measurement conditions. Original measurements remain unchanged.

**Planned processing:**

1. Parse source headers, wavenumber axes, detector signal and declared units.
2. Validate numerical row counts, wavenumber ordering, value ranges and missing values.
3. Separate transmittance and absorbance until their representations are properly handled.
4. Retain raw spectra alongside any documented transformed, baseline-corrected or normalised versions.
5. Generate overlays for matching polymer/treatment combinations.
6. Report possible spectral features as *candidates for scientific interpretation* rather than automatically asserting specific chemical products.
7. Maintain peak-selection, baseline and transformation logs to allow comparisons to be reproduced.

**Visualisations:** original FTIR spectra; treatment overlays; spectral-unit coverage; annotated review regions; transformed-versus-source comparisons.

## 7. Rheology and thermogelation workflow

**Rheology** examines how a material deforms and flows when forces are applied. This is central to injectable and printable thermogels because a formulation must flow during delivery, establish sufficient shape or network stability, and often recover after strong deformation.

| Measurement | What it means | Scientific information to preserve | Planned analysis / figure |
|---|---|---|---|
| **Storage modulus, G′ (Pa)** | Elastic or energy-storing response | Temperature, frequency, strain, geometry and conditioning | `G′` curves and comparisons |
| **Loss modulus, G″ (Pa)** | Viscous or energy-dissipating response | Same testing conditions as G′ | `G″` curves; `tan δ = G″/G′` where justified |
| **Temperature sweep** | How stiffness and viscous response change with temperature | Heating/cooling direction, ramp rate, dwell time and oscillatory settings | G′/G″ versus temperature; operational crossover candidates |
| **Frequency sweep, when available** | How network response varies with deformation timescale | Angular frequency, fixed temperature, strain within the LVR | G′/G″ versus angular frequency |
| **Amplitude / strain sweep** | When response becomes nonlinear as deformation increases | Applied strain or stress, frequency, temperature | Modulus versus strain; LVR review |
| **Flow sweep** | How viscosity varies with shear rate | Rate range, temperature and instrument conditions | Viscosity versus shear rate; shear-thinning checks |
| **Yield / flow response** | When material begins to yield or becomes predominantly flow-like | Operational definition and loading mode | Yield/flow summary with definitions |
| **Structure-recovery test** | Whether response returns after high shear | High/low shear sequence and duration | Response versus time and recovery summaries |

### Gelation is an operational measurement

A frequently used analysis identifies a temperature at which `G′` crosses `G″`. This can give an **operational crossover temperature**, but it does **not automatically prove a persistent, three-dimensional gel network**. Frequency, strain, concentration, temperature ramp, sample equilibration and thermal history can change the result. Therefore:

- Record the **gel-point definition** used in each source.
- Distinguish reported gelation temperature from independently recalculated crossover temperature.
- Keep heating and cooling trajectories separate.
- Preserve non-gelling, missing and excluded cases as meaningful outcomes.
- Evaluate low-frequency network behaviour only where suitable measurements actually exist.
- Document assumptions when calculating recovery ratios, model fits or other derived rheological properties.

**Planned outputs:** standardised rheology tables, method-condition registry, rheology plots, operational gelation summaries, transformation records and limitations reports. The current source contains primarily OriginLab projects; numerical exports must be verified before these are described as completed results.

## 8. Printing-image curation and computer vision

The deposited image collections offer a second major engineering task: organising **visual scientific evidence** rather than only numerical instrument tables. The source article describes printed grids imaged using optical/stereo-microscopy and related photography; raw SEM and TEM micrograph datasets have **not** been established in this deposit.

### Image inventory and metadata

For each image, the proposed pipeline records original archive/path, format, image width and height, checksum, colour mode, any embedded metadata, documented specimen/treatment context and image-review status.

### Image quality and scientific suitability

Automated checks can flag unreadable images, duplicate content, low resolution, poor contrast, blur, unusual aspect ratios or absent scale information. These are *screening flags*, not proof that an image is scientifically invalid. Preview thumbnails, overview photographs and measurement-ready microscopy images must be distinguished.

### Quantitative printing assessment (conditional on calibration)

Where resolution, physical scale, treatment identity and image quality are sufficient, proposed analysis includes:

- Segmenting printed strands and pores.
- Measuring central strand widths away from intersections.
- Recording pore area and perimeter.
- Comparing shapes between documented polymer/treatment groups.
- Calculating the reported printability descriptor `Pr = L²/(16A)` for suitable grid pores, where `L` is the pore perimeter and `A` is the pore area; `Pr ≈ 1` corresponds to a square pore.
- Comparing computed image features with *separately labelled* measurements published by the original researchers.

All segmentation thresholds, regions of interest, scale assumptions and failed cases will be logged. Visual resemblance alone is not sufficient to infer physical pore dimensions or hydrogel network mesh size.

**Visualisations:** indexed HTML image galleries; image-format/resolution summaries; before/after comparisons; annotated segments and pores; QC-image contact sheets; distributions of validated geometry measurements.

## 9. Sol–gel, sterilisation and biological evidence

Visual sol–gel tests, culture photographs and cytocompatibility measurements provide experimental context beyond spectroscopy and rheology. Their interpretation depends on polymer identity, formulation, **stage of treatment**, incubation or observation duration, and assessment method.

### Proposed curation and checks

- Represent control, autoclave, dry-heat, anaerobic dry-heat, ethanol, UV, single/repeated filtration and sequential processes using a **controlled treatment vocabulary** without altering original labels.
- Record concentration, treatment temperature/time and whether the specimen was powder, solution or formulated hydrogel where reported.
- Link photographs to figure captions, source folders, observation times and treatment descriptions when evidence supports the link.
- Separate *qualitative observations* from independently measured cell-viability or IC50 values.
- Record assay concentration, duration, organism/cell model, biological versus technical replicates and reported uncertainty.
- Preserve thresholded IC50 values (`<...` or `>...`) and distinguish missing from censored results.
- Document the paper's stated limitations for microbial-growth screening: appearance and microscopy are not equivalent to formal pharmacopoeial sterility assurance.

**Visualisations:** treatment-evidence matrices; biological-outcome summaries with censoring indicated; photographic galleries; data-coverage charts.

## 10. Scientific schemas and cross-technique linkage

A useful analysis-ready data model should keep **entities** (what something is) separate from **measurements** (what was observed) and **evidence** (where a claim came from).

| Proposed output | Purpose |
|---|---|
| `source_registry.csv`, `archive_inventory.csv`, `source_file_inventory.csv` | Source DOI, archive inventory and original file provenance |
| `polymer_register.csv`, `polymer_batch_register.csv` | Chemical identity, architecture and documented batch information |
| `formulation_register.csv`, `treatment_register.csv` | Concentration, medium, treatment conditions and treatment stage |
| `measurement_register.csv`, `measurement_conditions.csv` | Technique, run, instrument settings and acquisition context |
| `sec_measurements_standardised.csv` | Traceable chromatograms and reported/calculated molar-mass fields |
| `nmr_measurements_standardised.csv` | Acquisition metadata, spectra or documented chemical assignments |
| `ftir_measurements_standardised.csv` | Wavenumber, observed signal, original units and valid transformations |
| `rheology_measurements_standardised.csv` | Rheological observations and test conditions |
| `image_records_standardised.csv`, `printing_measurements.csv` | Image metadata, QC and validated image-derived descriptors |
| `biological_assay_register.csv` | Experimental biological observations and reported results |
| `record_linkage.csv`, `unresolved_review_items.csv` | Confirmed, candidate and unresolved relationships |
| `data_dictionary.csv`, `qc_findings.csv` | Field definitions, validation rules and quality-review evidence |
| `transformation_rules.csv`, `standardisation_decisions.csv`, `run_manifest.json` | Processing steps, choices, software versions and reproducibility evidence |

### Intended evidence pathway

`Polymer / batch → formulation → treatment / processing history → measurement run → raw source file → validated observation → derived result → published comparison`

Links will be created **only when supported** by original metadata, paper methods or other explicit evidence. Comparisons at polymer/treatment level are not a substitute for confirming that two measurements came from the *same physical sample*.

## 11. Quality-control framework

The pipeline will use automated rules for clearly detectable problems, with human scientific review for interpretative decisions.

| QC category | Example rule or review question | Response |
|---|---|---|
| **Integrity** | Does the ZIP pass CRC validation? Is the file readable? | Log pass/failure with original path |
| **Completeness** | Are expected mandatory fields available for the specific method? | Report missingness by technique |
| **Units** | Is FTIR `%T` being mixed with absorbance? Are molar masses and temperatures labelled? | Preserve source form; transform only with a documented rule |
| **Numerical validity** | Are instrument axes numeric and plausible? Are duplicates or non-finite values present? | Flag for review; avoid silent deletion |
| **Acquisition context** | Are temperature, ramp rate, frequency, strain and instrument settings known? | Mark comparisons limited if conditions differ |
| **Identity** | Is polymer batch or treatment stage ambiguous? | Retain uncertainty and do not join unsupported records |
| **Spectral processing** | Was the spectrum smoothed, normalised or baseline-corrected? | Record transformations and maintain raw arrays |
| **Imaging** | Is image scale sufficient for a proposed physical measurement? | Separate visual QC from quantitative analysis eligibility |
| **Replicates** | Are technical replicates distinguishable from independent material batches? | Avoid pseudoreplication and inflated sample counts |
| **Reporting** | Are `ND`, `NA`, `not printable` and bounded values retained accurately? | Encode reason/qualifier separately |
| **Reproducibility** | Does a clean-run notebook regenerate the expected output schema and counts? | Produce validation summary and run manifest |

A QC flag is **not automatically an error**, and a scientifically plausible outlier should not be removed merely because it looks unusual. Findings will be tracked with a rule, evidence, severity, review status and documented resolution.

## 12. Scientific visualisation plan

**Visualisations are part of the intended workflow, not decorative additions.** A figure is produced only when the underlying measurements and relevant units have been successfully extracted and validated.

| Area | Planned plots or visual products |
|---|---|
| **Source audit** | Archive-size charts; file types by archive; duplicate-content summaries; instrument-format coverage |
| **Data quality** | Missing-data heatmaps; QC-category counts; metadata-completeness charts; experimental coverage matrices |
| **SEC/GPC** | Elution-time chromatograms; normalised detector-response overlays; molar-mass and dispersity summaries |
| **NMR** | Chemical-shift spectra; selected peak annotations; acquisition-parameter comparisons |
| **FTIR** | Original and justified transformed spectra; control/treatment overlays; unit-consistency plots |
| **Rheology** | G′/G″ versus temperature; modulus versus strain/frequency where available; viscosity versus shear rate; recovery curves |
| **Sol–gel and printing** | Condition-labelled image galleries; before/after treatment views; validated strand/pore geometry |
| **Biological data** | Treatment-level assay summaries; qualifiers/censoring-aware outcome charts; image-evidence galleries |
| **Integrated evidence** | Polymer × treatment × technique coverage maps; provenance/linkage diagrams; scientifically supported cross-technique comparisons |

Plots will specify source, units, experimental conditions and whether values are **measured**, **source-reported**, **calculated** or **image-derived**. Uncertainty and replicates will be displayed when supported. No missing curve or point will be invented to complete a figure.

## 13. Reproducible Python workflow engineering

The project is designed as a reusable scientific-data pipeline rather than a set of manually edited figures.

**Planned tools:** Python, pandas, NumPy, Matplotlib, Jupyter Notebook, standard ZIP/hash/path libraries, and suitable validated readers or libraries for specialised formats. Image analysis may use Pillow, scikit-image or OpenCV when warranted. Instrument-specific packages will be selected only after compatibility is tested.

**Engineering principles**

- Keep **raw**, **intermediate** and **processed** files in separate locations.
- Use relative paths and configuration files, not user-specific Windows folders.
- Inventory source archives without modifying them; do not rely on arbitrary ZIP extraction order.
- Develop small, testable Python functions for readers, conversions, schema checks and visualisations.
- Validate column types, record counts, units, source identifiers and output file integrity.
- Maintain explicit processing decisions and a `run_manifest.json` containing input fingerprints, execution details and software versions.
- Save figures and quality-control reports with stable descriptive filenames.
- Preserve original records and document exclusions, uncertainties and failed extractions.
- Test completed notebooks using: **Close → Reopen → Restart Kernel → Run All**.
- Document installation and dependencies so plotting is reproducible rather than quietly omitted when a library is missing.

### Proposed repository layout

```text
thermoresponsive-hydrogel-data-curation/
├── README.md
├── requirements.txt                  # to be added after dependency validation
├── data/
│   ├── raw/                          # original files referenced; see source licence
│   ├── interim/                      # intermediate extraction results
│   └── processed/                    # standardised, quality-checked outputs
├── notebooks/
│   ├── 00_scope_and_source_registry.ipynb
│   ├── 01_source_archive_audit.ipynb
│   ├── 02_scientific_schema_and_qc.ipynb
│   ├── 03_polymer_characterisation.ipynb
│   ├── 04_rheology_and_gelation.ipynb
│   ├── 05_image_curation_and_printing.ipynb
│   ├── 06_multimodal_evidence_linkage.ipynb
│   └── 07_reproducibility_validation.ipynb
├── src/                              # reusable readers, checks and plot functions
├── figures/                          # reproducibly generated scientific figures
├── reports/                          # source audit, QC and HTML summaries
└── docs/                             # schemas, data dictionary and methods
```

*The structure above is planned; listed directories and notebooks should not be interpreted as already present in the repository. Large raw data remain attributed to the Zenodo source rather than being duplicated in GitHub without a rights and size review.*

## 14. Project roadmap and phase deliverables

| Phase | Purpose | Proposed deliverables | Completion criteria |
|---|---|---|---|
| **0 — Scope and source registry** | Define the scientific questions, source rights, techniques and study boundaries | Source registry, scope notes, methods-context checklist | All source references and intended analyses documented |
| **1 — Archive audit** | Enumerate all files and their roles | Inventory, file hashes, integrity checks, format review and archive plots | Reproducible counts for all 13 archives |
| **2 — Schemas and QC** | Define linked entities and transparent validation rules | Data dictionary, registers, QC log and missingness report | Every core field has a meaning, type, source and validation rule |
| **3 — Polymer characterisation** | Extract usable SEC, NMR and FTIR evidence | Standardised spectra/chromatograms, provenance and comparison figures | Source values and transformations are verifiable |
| **4 — Thermogel rheology** | Analyse source-supported temperature, deformation, flow and recovery data | Rheology tables, method registers and graphs | Gelation definitions and experimental conditions retained |
| **5 — Image curation and printing** | Catalogue and inspect visual evidence; quantify where calibrated | Image inventory, HTML gallery, QC figures, approved image-derived measurements | Quantitative claims supported by scale and validation |
| **6 — Evidence linkage** | Integrate polymer, batch, treatment, measurements and outcomes | Linkage table, evidence matrices and unresolved-linkage log | No unsupported physical-sample joins |
| **7 — Workflow validation** | Make extraction, QC and figure generation reproducible | Clean-run reports, manifests, dependency documentation | Complete notebook execution from a fresh session |
| **8 — Portfolio reporting** | Publish documented results and limitations | Updated README, phase reports, figures and curated evidence catalogue | Every completed claim traceable to a source or reproducible output |

**Phase status:** Source acquisition and preliminary archive inspection have been performed. The end-to-end pipeline and phase deliverables remain **planned / in development**, not completed or independently validated.

## Phase 0 publication checkpoint

**Checkpoint:** Phase 0 — Scientific Scope and Source Registry. This stage establishes a reproducible source-registration and scientific-scope baseline using the deposited data associated with *Impact of Sterilization Techniques on the Physicochemical and Biological Properties, and 3D Printability of Thermoresponsive Hydrogels*. It does not claim that SEC molar-mass distributions, NMR/FTIR peak assignments, gelation temperatures, viscoelastic curves, printed-strand geometry or biological outcomes have been independently reconstructed.

### Phase 0 research references and original source

| Resource | Reference | Scientific or workflow role |
|---|---|---|
| Experimental research article | [Nemati Mahand *et al.*, *Biomacromolecules* (2026)](https://doi.org/10.1021/acs.biomac.6c01032) · [ACS article page](https://pubs.acs.org/doi/10.1021/acs.biomac.6c01032) | Published experimental methods, chemical systems, reported treatments and study limitations. |
| Original research deposit | [Zenodo 21902628](https://zenodo.org/records/21902628) · [Dataset DOI](https://doi.org/10.5281/zenodo.21902628) | Thirteen original experimental ZIP archives, maintained locally with unchanged original filenames. |
| Research-data principles | [FAIR Guiding Principles](https://www.go-fair.org/fair-principles/) | Findable source descriptions, accessible provenance, interoperable metadata and reusable workflow design. |
| GitHub publication guidance | [Adding files to a repository](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository) | Version-controlled publication of code, figures and scientific documentation. |

### Phase 0 scientific scope and implemented workflow

Phase 0 connects polymer chemistry with source-aware data engineering through the following tasks:

1. **Polymer architecture and thermoresponse.** Register Pluronic F127 (PEO–PPO–PEO), pMeOx-b-pnPrOzi and pMeOx-b-pPheOzi-b-pMeOx as distinct materials. Block composition, temperature-dependent assembly, inverse gelation and batch distinctions are scientific metadata, not interchangeable labels.
2. **Experimental provenance.** Catalogue SEC/GPC, ¹H NMR, FTIR, rheology, sol–gel observations, 3D printing and biological-source archives. Preserve source filenames, checksums and archive-member counts while distinguishing digital records from independently prepared specimens.
3. **Treatment-context registration.** Preserve control conditions, thermal, UV, ethanol and filtration treatments, including differences between polymer powders, solutions and formulated hydrogels where reported.
4. **Scientific schema preparation.** Define preliminary metadata requirements for polymer identity, batch, concentration, solvent, processing, test temperature, heating/cooling direction, instrument settings, units and reporting provenance.
5. **Quality-control design.** Identify rules for missing fields, incompatible numerical representations, ambiguous file-to-sample relationships, duplicate content and limitations of proprietary instrument formats.
6. **Scientific visualisation.** Generate traceable archive-size and experimental-category figures alongside a conceptual structure–measurement–performance pathway. These figures describe data availability and workflow logic rather than newly analysed experimental measurements.
7. **Reproducible workflow engineering.** Register inputs and outputs, record package versions, write stable artefact filenames and validate results using a clean Jupyter kernel.

**Phase 0 execution evidence:** The submitted executed notebook registered 13 source archives and 1,119 archive members, produced 12 CSV/JSON output files and three PNG figures, and recorded 10 passed structural validation checks. These counts describe the digital archive and software checks; they do **not** demonstrate that 1,119 independent specimens or measurements were analysed. Fresh-kernel reproduction remains dependent on access to the same source archives and a compatible Python environment.

### Phase 0 core notebook and HTML reports

| Resource | Canonical repository location | Access |
|---|---|---|
| **Executable Python/Jupyter notebook** | `00_scope_and_source_registry.ipynb` | [Open Phase 0 notebook](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/00_scope_and_source_registry.ipynb) |
| **Published Phase 0 HTML report (executed notebook export)** | `reports/phase0/00_scope_and_source_registry.html` | [Open HTML source](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/reports/phase0/00_scope_and_source_registry.html) · [View rendered report in browser](https://htmlpreview.github.io/?https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/reports/phase0/00_scope_and_source_registry.html) |
| **Separate generated scientific scope summary** (not yet published) | `reports/phase0/phase0_scientific_scope_report.html` | Generated summary remains separate from the executed notebook HTML; a direct link should be enabled after that file is uploaded. |

The Jupyter notebook contains the executable Python cells and scientific explanations. The published `00_scope_and_source_registry.html` file is the executed notebook export, displaying the code, outputs and scientific interpretation. The separately generated `phase0_scientific_scope_report.html` is a distinct scientific summary and is not linked as published until uploaded. Browser rendering uses a third-party HTML preview service; the corresponding GitHub links remain the canonical references. All figures used by the generated scientific report are expected under `figures/phase0/` so relative image paths can resolve.

### Phase 0 output inventory and direct file links

The following paths correspond to outputs of the Phase 0 notebook. File links are **publication targets, not a statement that the files are already present on GitHub**. Only reviewed outputs should be committed after source-reuse and private-local-path checks.

#### A. Scientific source and metadata registers

| Scientific record | Direct GitHub file link | Role |
|---|---|---|
| `source_registry.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/source_registry.csv) | Source publication, Zenodo DOI and data-origin register. |
| `archive_registry.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/archive_registry.csv) | Thirteen original ZIP archives, scientific categories, sizes and member counts. |
| `polymer_system_register.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/polymer_system_register.csv) | Polymer identity, block architecture and thermoresponsive context. |
| `published_batch_descriptions.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/published_batch_descriptions.csv) | Publication-derived polymer-batch descriptions; not newly measured batches. |
| `published_treatment_register.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/published_treatment_register.csv) | Documented sterilisation treatments, stages and reported conditions. |
| `experimental_technique_register.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/experimental_technique_register.csv) | Characterisation methods, expected evidence and acquisition context. |
| `research_questions.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/research_questions.csv) | Scientific questions connecting polymer chemistry, processing and evidence. |
| `metadata_requirements.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/metadata_requirements.csv) | Candidate scientific metadata, units and data-validation expectations. |
| `preliminary_qc_rules.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/preliminary_qc_rules.csv) | Preliminary, reviewable quality-control checks. |
| `phase0_input_verification.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/phase0_input_verification.csv) | Archive file-identity checks and input integrity. |
| `phase0_run_manifest.json` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/phase0_run_manifest.json) | Processing provenance, source references and software versions. |
| `phase0_validation_summary.csv` | [Open file](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/data/processed/phase0/phase0_validation_summary.csv) | Phase 0 structural and output-validation results. |

#### B. Phase 0 scientific visualisations

| Figure | Direct GitHub figure link | Interpretation |
|---|---|---|
| `phase0_archive_sizes.png` | [View figure](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/figures/phase0/phase0_archive_sizes.png) | Compressed-source archive-size comparison; size does not indicate independent sample count. |
| `phase0_scientific_category_coverage.png` | [View figure](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/figures/phase0/phase0_scientific_category_coverage.png) | File-category representation across polymer-characterisation and application evidence. |
| `phase0_scientific_evidence_pathway.png` | [View figure](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/figures/phase0/phase0_scientific_evidence_pathway.png) | Conceptual relationship between polymer architecture, treatment, experimental characterisation and material performance; not a verified specimen-level linkage. |

The figures must be interpreted with their dataset, measurement and sample-level limitations. File-count charts do not establish representative experimental sampling. The conceptual evidence pathway illustrates the intended scientific data model and is not a confirmed same-specimen provenance graph.

### Phase 0 environment and reproducibility

The locally configured environment is named **`Python (Thermogel Phase 0)`** and corresponds to the Conda environment `thermogel-phase0`. The project uses Python and scientific packages including pandas, NumPy, Matplotlib, Jupyter/ipykernel and nbclient. Package compatibility must be checked within the selected environment; installing into the unrelated Anaconda base environment is not required.

- [Project dependency specification](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/requirements.txt) — dependency manifest for a reproducible installation, when added to the repository.
- [Git exclusion rules](https://github.com/tehsongxuan/thermoresponsive-hydrogel-data-curation/blob/main/.gitignore) — prevents large raw archives, temporary outputs, checkpoints and private environment artefacts from being inadvertently committed, when added to the repository.

The executable Phase 0 notebook currently resides at the **repository root**, consistent with the working Jupyter directory. The separate `notebooks/` layout in the earlier proposed repository plan can be adopted later, provided the published notebook link and any relative paths are updated together.

**Required local source layout:**

```text
thermoresponsive-hydrogel-data-curation/
├── README.md
├── 00_scope_and_source_registry.ipynb
├── data/
│   ├── raw/
│   │   └── zenodo_21902628/
│   │       └── [the 13 original Zenodo ZIP archives, unchanged]
│   └── processed/
│       └── phase0/
│           └── [generated CSV and JSON records]
├── figures/
│   └── phase0/
│       └── [three generated PNG figures]
└── reports/
    └── phase0/
        ├── 00_scope_and_source_registry.html      # published executed notebook HTML
        └── phase0_scientific_scope_report.html # separately generated summary, when uploaded
```

**Execution procedure:** Open `00_scope_and_source_registry.ipynb`, select **Python (Thermogel Phase 0)**, and run **Kernel → Restart Kernel and Run All Cells**. The 13 original ZIP files must remain in `data/raw/zenodo_21902628/`. Execution should regenerate the declared named outputs without relying on previously defined notebook variables or manually extracted source archives. The `phase0_validation_summary.csv` and `phase0_run_manifest.json` should be reviewed after each run; software validation does not establish the experimental validity of unpublished measurements or cross-technique physical-sample relationships.

### Phase 0 GitHub publication guidance

The initial public checkpoint comprises the updated `README.md`, the single canonical Jupyter notebook, the generated scientific report, three independently created Phase 0 figures and the documented environment. The supporting Phase 0 CSV/JSON registers are linkable and useful for scientific transparency **after their content, source permissions and local-path exposure have been reviewed**. Public-access status must not be confused with permission to redistribute third-party deposited files.

The **13 original Zenodo ZIP files** are intentionally not reproduced in the GitHub repository. The associated journal PDF, source image collections, raw proprietary instrument projects, downloaded software environments and notebook checkpoint directories likewise remain local unless reuse permission and publication necessity are established. All source records remain attributable to their original researchers via the DOI references above.

**Phase 0 handoff:** The registered sources, metadata requirements, treatment definitions, preliminary QC rules and documented limitations establish the starting point for **Phase 1 — Source Archive Audit**. Later phases may implement full archive-member inventories, scientific schema mapping, verified numerical extraction, imaging quality control and evidence-led links, without treating matching filenames as proof of specimen identity.

---

## 15. Known limitations and scientific safeguards

1. **Proprietary projects:** OriginLab `.opju` files may require authorised Origin export or a proven compatible extraction method. A preview graph is not equivalent to a validated numeric export.
2. **Batch effects:** Different polymer batches and calibration dates can affect apparent cross-treatment differences and must be documented.
3. **Method differences:** SEC solvents, flow settings, instrument conditions and analysis methods may vary; comparisons need protocol-level checks.
4. **Thermal history:** Thermogel measurements depend on concentration, medium, heating/cooling direction, ramp rate and equilibration history.
5. **Missing identities:** Not all filenames provide sufficient evidence to connect an instrument run or image to a unique physical specimen.
6. **Spectral ambiguity:** Automatic peak detection is not a substitute for chemical assignment, baseline evaluation or independent method validation.
7. **Microscopy limits:** Optical/stereo-microscopy photographs are not SEM/TEM micrographs; quantitative geometry requires calibration and suitable resolution.
8. **Biological interpretation:** Photographic microbial-growth assessments do not establish formal sterility assurance or clinical suitability.
9. **Sample size:** Hundreds of files or tens of thousands of spectral points do not imply an equivalent number of independent experimental samples.
10. **Causal interpretation:** Correlation between treatment, spectroscopy, rheology and printing outcomes does not by itself identify a unique molecular mechanism.

Scientific uncertainty will remain visible in the curated outputs. The intention is to produce **defensible evidence**, not artificially complete tables.

## 16. Expected value and future extension

The intended result is a **reusable, auditable materials-data workflow** able to move from original heterogeneous research files to clearly defined, quality-checked and source-linked experimental records.

It will demonstrate practical capabilities in:

- Polymer-science-aware metadata and schema design.
- Numerical spectroscopy and rheology data processing.
- Unit and measurement-context validation.
- Image-data curation and conditional quantitative image analysis.
- Experimental provenance and batch-aware record linkage.
- Automated scientific visualisation and reproducible Python execution.
- Transparent reporting of unresolved scientific-data limitations.

Future work could extend the approach to appropriately sourced **SEM, TEM, cryo-TEM, scattering or additional thermogel formulation datasets**, and eventually support cross-study comparison or carefully validated machine-learning studies. Such modelling is **outside the present project scope** and would require sufficient independent, comparable and traceable experimental records.

## 17. Acknowledgements

This independent project uses data deposited by **Saba Nemati Mahand, Saumya Palliyawaththage, J. Maurice Pütz, Parsa Amin, Ekaterina Takmakova and Robert Luxenhofer**, with the related findings published in *Biomacromolecules* (2026).

Please cite the **[original article](https://doi.org/10.1021/acs.biomac.6c01032)** and **[Zenodo dataset](https://doi.org/10.5281/zenodo.21902628)** when using the original research materials. Scientific credit for the experiments and source datasets remains with their authors.

