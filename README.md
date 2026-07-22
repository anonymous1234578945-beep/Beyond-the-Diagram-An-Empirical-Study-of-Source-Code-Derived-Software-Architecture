# Beyond the Diagram: Datasets

Datasets for the paper **"Beyond the Diagram: An Empirical Study of Source-Code-Derived Software Architecture"** (under review, APSEC 2026; double-blind).

The paper studies whether developer-published architecture diagrams can serve as an evaluation reference for architecture recovery and LLM-based diagram generation. Across 50 open-source infrastructure projects, three analysts derive a source-code architecture profile per project under a shared 11-type classification scheme, classify each project's published developer diagram by viewpoint and primary architecture type, and compare both against classifications produced by three large language models (GPT-5.5, Claude Sonnet 4.6, Gemini 3.1 Pro). The central finding: under majority labels, only 5 of 50 developer diagrams primarily describe source-code architecture; the rest communicate runtime, deployment, or ecosystem concerns.

This repository contains the manual analysis datasets. The complete replication artifact — including the deterministic input-ablation control inputs and outputs, the repository audit, and all analysis scripts — is archived on Zenodo: https://doi.org/10.5281/zenodo.21462409

## Contents

| File | Description | Supports |
|---|---|---|
| `ANALYSIS anonymous.xlsx` | Master spreadsheet, one row per project. Sheets: `HUMAN` (independent source-code-derived labels from all three analysts, with evidence summaries), `DEVELOPER` (developer diagram viewpoint and primary-type labels), `CLAUDE`, `Gemini`, `GPT 5` (first-round per-model outputs), `SUMMARY`, `STYLE AGREEMENT` (cross-perspective agreement) | RQ1–RQ4; Tables IV–X |
| `human analysis 1-20.docx`, `human analysis 21-40.docx`, `human analysis 41-50.docx` | Per-project source-code proof narratives for the independent analysis: primary type and sub-architecture evidence tied to specific directories, files, and mechanisms | RQ1; Section II-C1 |
| `DIAGRAM ANALYSIS 50 (1).pdf`, `DIAGRAM ANALYSIS 50 (2).pdf` | Per-project developer diagram analyses: the collected diagrams with viewpoint and primary-type classification rationale | RQ2, RQ3; Tables V–VII |
| `prompt.docx` | The Architecture Classification Scheme definitions (11 types with references) used as the fixed prompt for all three LLMs and as the analyst codebook basis | Section II-B, II-C3 |

## Terminology mapping

The spreadsheet predates the paper's final terminology:

- **HUMAN** (rater 1, `HUMAN primary Arch` column) = the paper's *independent source-code-derived (ISC)* labels, fixed before the reliability study.
- **HUMAN 2 / HUMAN 3** = the two additional analysts in the RQ1 reliability study (Fleiss κ = 0.95).
- **DEVELOPER** = labels inferred from the project's published developer-authored diagram (majority of three raters; per-rater labels included).
- **CLAUDE / Gemini / GPT 5** = first-round per-model outputs; the paper's ensemble label is the type agreed by at least two models. The four three-way splits carry no ensemble label.

## Notes for reuse

- One retained project (Secure-Azure-Hub-Spoke-Network-Architecture) resolves to a diagram-companion repository with no source files, due to a dataset-construction link error documented in the paper (Sections II-A and VIII). Its labels rest on file names, README, and metadata. The paper reports every affected aggregate with and without it; treat this row accordingly.
- All quantitative comparisons in the paper are exact-label agreement on one primary architecture type under the shared scheme. The datasets do not encode node- or edge-level diagram content; element-level coding is future work the corpus is intended to enable.
- Repository snapshots are characterized at their July 2026 revisions; commit SHAs are recorded in the Zenodo artifact's audit.

## Citation

The paper is under double-blind review. Please cite the Zenodo artifact (DOI above) until the paper is published; a full citation will be added on acceptance.
