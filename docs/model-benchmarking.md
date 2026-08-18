# Model Benchmarking

## Objective

The benchmark evaluates local language models as document-extraction components. It tests whether a model can transform extracted PDF text into a valid CSV that follows a predefined schema.

## Evaluation Dimensions

- CSV validity.
- Header conformity.
- Row conformity.
- Cell-level agreement with a reference output.
- Recorded p50 and p95 processing time.
- Practical trade-offs between response quality, latency, and implementation complexity.

## Recorded Snapshot

| Model | p50 / p95 | Valid CSV | Header and row checks | Cell accuracy |
| --- | ---: | --- | --- | ---: |
| Gemma 7B | 176.12 s / 176.12 s | Yes | Passed | 5% |
| Mistral 7B | 445.30 s / 445.30 s | Yes | Passed | 0% |
| Llama 3 8B | 187.50 s / 187.50 s | No | Failed | 0% |

## Interpretation

The recorded experiment does not identify a production-ready winner. Gemma produced the fastest valid output in this snapshot, while the cell-level agreement remained low. Mistral produced valid formatting but took longer and did not match the reference cells. Llama 3 8B did not satisfy the recorded output contract.

These values describe a repository benchmark snapshot rather than a statistically representative evaluation or production SLA. The raw documents, reference spreadsheets, prompts, and model credentials are intentionally excluded from this public repository.

## Engineering Value

The experiment demonstrates a practical evaluation loop: define an output contract, measure both structural validity and content quality, record latency, and use the results to guide model and architecture decisions.
