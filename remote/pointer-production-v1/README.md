# Production Pointer Locator v1

This is the raw-text-free production runtime locator for `terms/latin` and
`ids`. It uses the verified existing pointer ranking, corpus balancing, and
provenance fields; it is not a second search engine or scholarly authority.

1. Read `manifest.json` and `production-summary.json`.
2. Look up the exact production key under its SHA-256 bucket.
3. Follow ranked pointers to the pinned upstream source file and verify context,
   provenance, evidence class, text role, and witness before making a finding.

`terms/cjk` full trigram vocabulary is intentionally not materialized in v1.
The local CJK trigram FTS remains build/retrieval infrastructure, not a
Buddhist-term vocabulary. If these pointers cannot establish a claim, report:

`không đủ dữ liệu trong remote corpus export hiện tại`
