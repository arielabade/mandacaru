# Mandacaru User Manual

## Purpose

Mandacaru helps users extract and structure information from institutional PDF documents. It was designed for higher-education and public-sector workflows where official documents must be organized for analysis, reporting, transparency, or reuse in other systems.

## Supported Document Types

The documented workflows cover:

- Resolutions.
- Ordinances.
- Normative instructions.
- Undergraduate course pedagogical projects.
- Generic institutional documents through a metadata-oriented fallback.

## Processing a Document

1. Open the web interface.
2. Select **Browse files** and upload one or more PDF documents.
3. Wait while each document is validated, read, classified, and structured.
4. Review the processing log and the resulting table.
5. Select a document type tab when more than one type is present.
6. Download the structured records in CSV, XLSX, or JSON format.

## What the User Receives

The result combines document metadata with fields extracted according to the detected type. Depending on the schema, records may contain identifiers, titles, dates, issuing bodies, signatures, decisions, course information, full text, page count, and other source-grounded fields.

The extraction workflow is designed to preserve information from the source document. Missing values should remain empty or use the application's documented fallback rather than being invented.

## Practical Limitations

The current workflow expects PDF files with an extractable text layer. Processing quality and response time depend on document structure, language-model availability, and the configured deployment.
