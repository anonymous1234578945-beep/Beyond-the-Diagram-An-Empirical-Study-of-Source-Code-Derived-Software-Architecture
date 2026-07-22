<div align="center">

# 📐 Beyond the Diagram
### An Empirical Study of Source-Code-Derived Software Architecture

*Under review: APSEC 2026 (double-blind)*

[![Zenodo](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.21462409-blue?logo=zenodo)](https://doi.org/10.5281/zenodo.21462409)
[![Projects](https://img.shields.io/badge/Projects-50-green)](#contents)
[![Scheme](https://img.shields.io/badge/Architecture%20Types-11-orange)](#architecture-classification-scheme)
[![License](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey)](https://creativecommons.org/licenses/by/4.0/)

</div>

---

## 🔍 What Is This?

Developer-published architecture diagrams are an attractive evaluation reference for architecture recovery and LLM-based diagram generation. They are publicly available at scale. But **do they actually represent implemented software architecture?**

This repository contains the manual analysis datasets for the first empirical study of this question. We examine **50 open-source infrastructure projects**, each with a published developer diagram, and compare three architectural perspectives:

| Perspective | Method | Agreement with Source Code |
|---|---|---|
| 👩‍💻 **Independent Source-Code-Derived** | Three analysts; evidence proof tables; Fleiss κ = 0.95 | — (ground reference) |
| 📊 **Developer-Authored Diagrams** | Three raters; shared codebook; viewpoint + primary type | 26 / 50 projects (52%) |
| 🤖 **LLM Ensemble** | GPT-5.5, Claude Sonnet 4.6, Gemini 3.1 Pro | 43 / 50 projects (86%) |

> **Central finding:** Under majority labels, only **5 of 50** developer diagrams (10%, 95% CI [4, 21]) primarily describe source-code architecture. The rest communicate runtime, deployment, or ecosystem concerns — a different viewpoint entirely.

The complete replication artifact (control inputs/outputs, repository audit, analysis scripts) is archived on Zenodo:
**[https://doi.org/10.5281/zenodo.21462409](https://doi.org/10.5281/zenodo.21462409)**

---

## 📁 Contents

```
datasets/
├── ANALYSIS anonymous.xlsx          # Master label spreadsheet (all perspectives, all 50 projects)
├── prompt.docx                      # Architecture Classification Scheme (LLM prompt + analyst codebook)
├── human analysis 1-20.docx         # Source-code proof narratives, projects 1–20
├── human analysis 21-40.docx        # Source-code proof narratives, projects 21–40
├── human analysis 41-50.docx        # Source-code proof narratives, projects 41–50
├── DIAGRAM ANALYSIS 50 (1).pdf      # Developer diagram analyses, part 1
└── DIAGRAM ANALYSIS 50 (2).pdf      # Developer diagram analyses, part 2
```

### `ANALYSIS anonymous.xlsx`
The master dataset. One row per project across seven sheets:

| Sheet | Contents |
|---|---|
| `HUMAN` | Independent source-code-derived labels (all 3 analysts), evidence summaries, sub-architectures |
| `DEVELOPER` | Developer diagram viewpoint + primary-type labels (all 3 raters) |
| `CLAUDE` | First-round Claude Sonnet 4.6 outputs |
| `Gemini` | First-round Gemini 3.1 Pro outputs |
| `GPT 5` | First-round GPT-5.5 outputs |
| `SUMMARY` | Cross-perspective agreement overview |
| `STYLE AGREEMENT` | Per-architecture-style concordance rates |

*Paper reference: RQ1–RQ4; Tables IV–X*

### `human analysis [range].docx`
Per-project source-code proof narratives: primary type and sub-architecture evidence tied to specific source directories, files, and line-level mechanisms. These are the evidence records that underlie the `HUMAN` spreadsheet labels.

*Paper reference: RQ1; Section II-C1*

### `DIAGRAM ANALYSIS 50 (1/2).pdf`
The collected developer diagrams with per-project viewpoint classification rationale and primary-type reasoning.

*Paper reference: RQ2, RQ3; Tables V–VII*

### `prompt.docx`
The Architecture Classification Scheme: all 11 type definitions with textbook and industry references. Served as both the fixed LLM prompt and the basis of the analyst codebook.

*Paper reference: Section II-B, II-C3*

---

## 🏛️ Architecture Classification Scheme

The shared 11-type scheme used across all three perspectives:

| # | Type | Primary Concern |
|---|---|---|
| 1 | **Layered** | Stack of dependent layers |
| 2 | **Pipeline** | Ordered sequential processing stages |
| 3 | **Microkernel** | Stable core + registered plug-in extensions |
| 4 | **Service-Based** | Coarse-grained deployed services |
| 5 | **Event-Driven** | Asynchronous, decoupled event flow |
| 6 | **Space-Based** | In-memory distributed processing |
| 7 | **Orchestration-Driven** | Centralized service coordination |
| 8 | **Microservices** | Small, independently deployable services |
| 9 | **Hub-and-Spoke** | Shared services around isolated workload spokes |
| 10 | **Strangler Fig** | Incremental legacy replacement |
| 11 | **Hexagonal** | Domain logic behind ports and adapters |

Types 1–8 from Richards & Ford (2020); types 9–11 from Microsoft Azure, AWS Prescriptive Guidance.

---

## 🗺️ Terminology Mapping

The spreadsheet column names predate the paper's final terminology:

| Spreadsheet | Paper term |
|---|---|
| `HUMAN primary Arch` (rater 1) | Independent source-code-derived (ISC) label — the ground reference |
| `HUMAN 2`, `HUMAN 3` | Additional analysts in the RQ1 reliability study (Fleiss κ = 0.95) |
| `DEVELOPER` sheet | Developer-authored diagram labels (majority of three raters) |
| `CLAUDE` / `Gemini` / `GPT 5` sheets | First-round per-model outputs; ensemble = majority of ≥ 2 models |

---

## ⚠️ Notes for Reuse

**Source-free project.** One retained project (*Secure-Azure-Hub-Spoke-Network-Architecture*) resolves to a diagram-companion repository with no source files, due to a dataset-construction link error documented in Sections II-A and VIII of the paper. Its labels rest on file names, README, and metadata only. The paper reports every affected aggregate both with and without this project; treat its row accordingly.

**Measurement scope.** All quantitative comparisons are exact-label agreement on one primary architecture type under the shared 11-type scheme. The datasets do not encode node- or edge-level diagram content. Element-level coding is future work this corpus is designed to enable.

**Snapshot date.** Repository snapshots are characterized at their July 2026 revisions. Commit SHAs for all 50 repositories are recorded in the Zenodo artifact audit file.

---

## 📄 Citation

The paper is under double-blind review. Until publication, please cite the Zenodo artifact:

```bibtex
@dataset{beyond_the_diagram_2026,
  author    = {Anonymous Author(s)},
  title     = {Beyond the Diagram: An Empirical Study of Source-Code-Derived
               Software Architecture — Datasets},
  year      = {2026},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.21462409},
  url       = {https://doi.org/10.5281/zenodo.21462409}
}
```

A full paper citation will be added on acceptance.

---

<div align="center">
<sub>Artifact for APSEC 2026 submission · Double-blind anonymized · All metadata sanitized</sub>
</div>
