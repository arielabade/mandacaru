# Engineering Decisions

This document summarizes the engineering reasoning supported by the project artifacts. It intentionally describes decisions conceptually and does not reproduce implementation code, private configuration, or internal credentials.

## Reusable Processing Core

The project separates a Python package from the user interface. This boundary keeps file validation, preprocessing, classification, extraction, and structuring reusable by other application surfaces.

## Document-Specific Schemas

Resolutions, ordinances, normative instructions, and undergraduate course pedagogical projects expose different kinds of information. The extraction layer therefore uses document-specific fields and examples, with a generic metadata fallback for unsupported types.

## Source-Grounded Extraction

The extraction design emphasizes literal information from the source document, valid structured output, missing values rather than invented values, and avoidance of duplicate fields. This is a practical control for using a language model in a data-processing workflow.

## Interoperable Outputs

CSV, XLSX, and JSONL outputs allow users and downstream systems to consume the result without being tied to the Streamlit interface. The same structured records can support spreadsheets, data pipelines, dashboards, or future integrations.

## Defensive Processing

The application validates PDF inputs, reports file-level failures, preserves processing logs, and handles multiple files with progress feedback. These behaviors turn a model-backed function into a more usable product workflow.

## Model Evaluation Before Commitment

The benchmark compares local language models using structural validity, schema conformity, and latency. The recorded results do not establish a production-ready model, which is why this portfolio documents the experiment as an engineering evaluation rather than as an unsupported performance claim.
