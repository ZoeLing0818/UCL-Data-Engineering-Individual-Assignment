# LLM-Assisted Risk Review Support Prototype for UK Business Entities

## Project Overview

This project develops an LLM-assisted risk review support prototype for UK business entities. It combines structured Companies House registry data, official API enrichment, curated policy guidance, and lightweight retrieval to generate analyst-facing review-support notes.

The prototype is designed to support prioritisation and interpretation rather than to make legal, regulatory, or compliance determinations. Its main goal is to show how a multi-source data-engineering workflow can be used to transform raw registry data into structured review outputs and grounded LLM-generated notes.

## Core Components

- **Entity master construction** from Companies House bulk data
- **Rule-based risk signal engineering** for prioritisation
- **Selective Companies House API enrichment** for official contextual support
- **Document ingestion** of curated policy and guidance materials
- **LLM-assisted review-note generation** using Gemini
- **Rule-based fallback notes** for robustness and interpretability
- **Lightweight RAG enhancement** using section-level policy chunks
- **Spark-based summary layer** for scalable aggregation

## Data Sources

- **Companies House bulk CSV**  
  Primary structured source for the entity universe and entity master table

- **Companies House API**  
  Supplementary official enrichment source for selected review candidates

- **Curated Markdown guidance files**  
  - `entity_review_policy.md`
  - `risk_flag_guidelines.md`
  - `manual_review_checklist.md`

- **Source provenance metadata**  
  Stored in `source_registry.json`

## Project Structure

```text
data/
├── raw/
│   └── CompaniesHouseData-2026-03-02.csv
├── processed/
│   ├── entity_master_v1.csv
│   ├── entity_risk_signals_v2.csv
│   ├── entity_external_enrichment.csv
│   └── entity_risk_signals_v2.parquet
├── docs_curated/
│   ├── entity_review_policy.md
│   ├── manual_review_checklist.md
│   └── risk_flag_guidelines.md
├── docs_raw/
│   ├── [source PDFs]
│   └── source_registry.json
└── warehouse/
    └── project.duckdb

artifacts/
├── reports/
│   ├── rag_review_note_*.md
│   └── rag_review_prompt_*.txt
└── tables/
    ├── priority_band_summary.csv
    ├── signal_trigger_summary.csv
    ├── top_high_sic_summary.csv
    ├── rag_review_outputs_summary.csv
    └── retrieved_chunks_summary.csv

01_entity_master_build.ipynb
02_risk_signal_engineering.ipynb
03_online_enrichment_source.ipynb
04_document_ingestion.ipynb
05_retrieval_and_review_support.ipynb
06_spark_entity_summary.ipynb
07_rag_review_enhancement.ipynb
