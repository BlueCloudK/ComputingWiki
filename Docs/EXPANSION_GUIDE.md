# EXPANSION_GUIDE

## Goal

Expand ComputingWiki systematically without creating duplicate concepts, ghost links, or noisy graph edges.

## Expansion principles

- Expand by pack, not by random nodes.
- Audit existing basenames before creating files.
- Prefer canonical English names.
- Keep main content in Vietnamese.
- Keep source trace in English.
- Avoid duplicate concepts with slightly different names.
- Avoid ghost links.
- Keep notes practical and concise.
- Do not rewrite the whole repo unless explicitly asked.
- Do not expose private method names or private learning frameworks.

## Source quality

Prefer:

- official documentation
- body of knowledge material
- textbooks and classic references
- respected engineering docs
- standards and specifications

Avoid:

- random SEO blogs
- copied tutorial fragments
- uncited claims
- long quotes from copyrighted sources

## Expansion workflow

```text
1. Select expansion pack
2. Audit existing MOC/Nodes
3. List missing concepts
4. De-duplicate canonical names
5. Create/update MOC
6. Create nodes using node schema
7. Add keywords
8. Check dangling links
9. Report changes
```

## Pack workflow details

Before writing:

- List candidate nodes.
- Remove concepts already covered by existing basenames.
- Decide which nodes are MOC-level and which are regular concept nodes.
- Decide which useful concepts should stay as future plain text because no source trace or node boundary is clear yet.

While writing:

- Do not create tutorial notes.
- Do not add long code examples.
- Do not link every related word.
- Use `Gồm những gì` only for direct child/component links.
- Use `Nối mạnh` only when the relation helps understanding or project work.
- Use `Liên quan rộng` for broad text-only associations.

After writing:

- Count files created and updated.
- Check dangling wikilinks in `00`, `MOC/`, `Nodes/`, `Paths/`, and `Docs/`.
- Check keyword sections exist for new MOC/Nodes.
- Report skipped nodes and why.
- Report git status.
