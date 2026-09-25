# Compact Pointer Serialization POC

This POC serializes the already-generated 500-query pointer benchmark without
running retrieval or changing candidates. `pointers/part-000001.jsonl` stores
each distinct full source/segment metadata record once under a stable
`pointer_id`. Locator rows retain query-specific `rank`, `score`, and
`match_reasons`, then reference that metadata by `pointer_id`.

To reconstruct a benchmark-equivalent pointer result:

1. Read the locator row for the query key.
2. Resolve every `pointer_id` in `pointer_refs` from the pointer table.
3. Merge each reference's `rank`, `score`, and `match_reasons` with metadata.
4. Keep the reference order unchanged.

The artifact contains no `raw_text` and is a serialization measurement only,
not a production locator design.
