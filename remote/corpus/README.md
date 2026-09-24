# GitHub Connector Corpus Export

This directory is a deterministic, read-only export of the existing SQLite
index. It is an access adapter, not a second research system.

1. Read `manifest.json` and verify actual corpus coverage and pinned SHAs.
2. Read `locator/manifest.json`, normalize the query or identifier as declared,
   calculate its bucket, and fetch the listed locator part file(s).
3. Resolve locator shard indexes through the root manifest `shards` array.
   Record shard indexes retain full coverage and are ordered by the best
   matching record in each shard.
4. For ordinary research, fetch roughly the first 20–50 candidate shards and
   verify the actual query in exported content. Continue deeper when exhaustive
   research or insufficient evidence requires it.
5. Treat `export_role: "primary"` as a hit. Rows marked `context_overlap`
   only preserve two neighboring records across shard boundaries; deduplicate
   all rows by `id`.
6. Read provenance on the record itself.
7. Inspect `relations/` and `variants/` when the research question needs them.
8. Apply the evidence hierarchy and witness separation from the repository
   research skill.

In the manifest, `shard_fields` names the columns used by each compact row in
`shards`. Locator results are candidate file locations, not evidence or
scholarly conclusions. Priority follows the shared deterministic final
record-ranking semantics, but it is not a byte-for-byte reproduction of SQLite
FTS/BM25 candidate generation. GitHub Code Search is optional only and is never
required.

Files are JSON Lines, ordered and sharded at record boundaries. If the export
does not contain enough evidence, report:

`không đủ dữ liệu trong remote corpus export hiện tại`
