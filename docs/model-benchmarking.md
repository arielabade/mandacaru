# Model Benchmarking

## Objective

The benchmark evaluates model-assisted document-extraction components. It tests whether an extraction approach can transform extracted PDF text into a valid CSV that follows a predefined schema.

## Evaluation Dimensions

- CSV validity.
- Header conformity.
- Row conformity.
- Recorded p50 and p95 processing time.
- Practical trade-offs between response quality, latency, and implementation complexity.

## Recorded Snapshot

| Alternative | p50 / p95 | Valid CSV | Header and row checks |
| --- | ---: | --- | --- |
| Alternative A | 176.12 s / 176.12 s | Yes | Passed |
| Alternative B | 445.30 s / 445.30 s | Yes | Passed |
| Alternative C | 187.50 s / 187.50 s | No | Failed |

## Interpretation

The recorded experiment does not identify a production-ready winner. One alternative produced the fastest valid output in this snapshot. Another produced valid formatting but took longer, while a third did not satisfy the recorded output contract.

These values describe a repository benchmark snapshot rather than a statistically representative evaluation or production SLA. The raw documents, reference spreadsheets, prompts, and model credentials are intentionally excluded from this public repository.

## Engineering Value

The experiment demonstrates a practical evaluation loop: define an output contract, measure structural validity, record latency, and use the results to guide extraction and architecture decisions.
