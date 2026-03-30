# LLM-Assisted Risk Review Support Prototype for UK Business Entities

## Overview

This project develops an LLM-assisted risk review support prototype for UK business entities.  
The system combines structured registry data from Companies House, official API enrichment, curated policy guidance documents, and lightweight retrieval to support analyst-facing review notes.

Rather than functioning as a predictive risk model or compliance decision engine, the prototype is designed to support prioritisation, interpretation, and manual review. It transforms raw registry data into structured review signals, enriches selected cases with additional official context, retrieves relevant policy snippets, and generates review-support notes using Gemini with a rule-based fallback path.

## Key Features

- Structured entity master construction from Companies House bulk data
- Transparent rule-based review signal engineering
- Selective Companies House API enrichment for prioritised entities
- Document ingestion and storage of curated guidance materials
- LLM-assisted review-note generation with Gemini
- Rule-based fallback review-note generation
- Lightweight RAG using section-level policy chunks
- Spark-based summary layer for scalable aggregation

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

notebooks/
├── 01_entity_master_build.ipynb
├── 02_risk_signal_engineering.ipynb
├── 03_online_enrichment_source.ipynb
├── 04_document_ingestion.ipynb
├── 05_retrieval_and_review_support.ipynb
├── 06_spark_entity_summary.ipynb
└── 07_rag_review_enhancement.ipynb
