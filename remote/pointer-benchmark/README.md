# Pointer Benchmark

This is a deterministic measurement artifact for the existing raw-text-free
pointer pipeline. It is not a production locator and does not change ranking,
evidence, source SHAs, or retrieval behavior.

- `benchmark-queries.json` records the real local index keys sampled for this run.
- `locator/` contains source pointers only; it contains no `raw_text`.
- `benchmark-summary.json` records size, pointer, duplicate, corpus, and blob-SHA
  measurements plus linear size extrapolations.

Each pointer was generated through the existing search/ranking pipeline, then
collapsed by `(corpus, work_id, source_path)` and bounded per corpus. Open the
pointer's pinned source file to verify any textual claim.
