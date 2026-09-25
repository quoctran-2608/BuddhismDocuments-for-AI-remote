# GitHub Connector Pointer POC

This deterministic proof of concept contains ranked provenance pointers only.
It does not contain `raw_text`, copied record shards, a copied corpus, or a
second search engine.

1. Read `manifest.json`.
2. Normalize the POC key, calculate its locator bucket, and fetch that JSONL
   row.
3. Follow pointers in rank order: open `repository` at `source_sha`, then open
   `source_path` directly in GitHub.
4. Use `work_id`, `segment_id`, and `sequence_no` to locate the passage in the
   original file. Verify wording, context, provenance, text role, and witness
   in that source before making a finding.

Pointer rank only decides which source file to open first. It is not evidence
and does not override user scope, evidence hierarchy, text role, witness
separation, or provenance. GitHub Code Search is not required.

If the listed pointers cannot establish a claim, report:

`không đủ dữ liệu trong remote corpus export hiện tại`
