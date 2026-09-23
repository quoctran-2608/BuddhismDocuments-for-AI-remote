# GitHub Connector Corpus Export

This directory is a deterministic, read-only export of the existing SQLite
index. It is an access adapter, not a second research system.

1. Read `manifest.json` and verify actual corpus coverage and pinned SHAs.
2. Search UTF-8 text only under `records/`.
3. Treat `export_role: "primary"` as a hit. Rows marked `context_overlap`
   only preserve two neighboring records across shard boundaries; deduplicate
   all rows by `id`.
4. Read provenance on the record itself.
5. Inspect `relations/` and `variants/` when the research question needs them.
6. Apply the evidence hierarchy and witness separation from the repository
   research skill.

In the manifest, `shard_fields` names the columns used by each compact row in
`shards`.

Files are JSON Lines, ordered and sharded at record boundaries. If the export
does not contain enough evidence, report:

`không đủ dữ liệu trong remote corpus export hiện tại`
