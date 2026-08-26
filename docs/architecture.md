# Mandacaru Architecture Overview

## System Goal

Mandacaru converts unstructured institutional PDFs into structured records that can be displayed, downloaded, or consumed by another system.

## Logical Flow

```text
PDF input
  -> file validation
  -> text and metadata extraction
  -> document type classification
  -> type-specific field extraction
  -> metadata and field consolidation
  -> structured table
  -> CSV, XLSX, or JSONL output
```

```mermaid
flowchart LR
    A[PDF input] --> B[Validation]
    B --> C[Text extraction]
    B --> D[PDF metadata]
    C --> E[Document classification]
    C --> F[Type-specific extraction]
    E --> F
    D --> G[Structured record]
    F --> G
    G --> H[Table and logs]
    G --> I[CSV / XLSX / JSONL]
```

## Main Components

### File management

Reads files from paths or in-memory bytes and verifies that the input has a valid PDF signature before processing.

### Preprocessing

Extracts readable document text and available metadata. The resulting text and page information become inputs to classification and extraction.

### Document classification

The classification layer combines document text with signals such as page count, filename patterns, headers, and rule-based features. A confidence threshold provides a generic fallback when classification is uncertain.

### Structured extraction

The assisted extraction layer uses document-specific fields and examples with a configured model provider. The extraction design emphasizes source fidelity, valid structured output, and avoiding invented values.

### Application layer

The web interface accepts multiple files, processes them concurrently, displays status messages and results, groups records by type, and provides downloads.

## Architectural Decisions

- Keep the core extraction logic reusable outside the interface layer.
- Separate preprocessing, classification, extraction, and output responsibilities.
- Use document-specific schemas instead of one undifferentiated output format.
- Keep the user interface focused on upload, inspection, and export.
- Use environment-based configuration for model credentials.

## Integration Boundary

Project architecture and deployment artifacts describe an API-oriented integration surface and optional external persistence. Those materials establish an intended integration boundary, while the public runnable interface reviewed for this portfolio is web-based.
