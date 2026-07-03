# GRAPH_RULES

## Core rule

Wikilinks are navigation edges, not tags.

A wikilink should make the graph easier to follow. If a word is only broadly related, use plain text instead.

## When to use wikilinks

Use wikilinks for:

- direct child/component nodes
- strong conceptual dependency
- project workflow dependency
- path navigation
- MOC navigation

Good examples:

- `Kubernetes` links to `Kubernetes Pod` as a component.
- `API Contract` links to `OpenAPI` as a strong artifact relation.
- `Threat Modeling` links to `Attack Surface` when that node exists and is central to the concept.

## When not to use wikilinks

Do not use wikilinks for:

- every related word
- broad areas in `Liên quan rộng`
- keywords
- source names
- future concepts that do not exist yet
- backlinks to MOC pages just to make graph lines

## Section rules

`Gồm những gì` should contain direct child/component wikilinks only.

`Nối mạnh` can contain wikilinks, but each link should include a reason.

`Liên quan rộng` should be plain text only.

`Keywords / Từ khóa tìm kiếm` should be plain text only.

`Missing / Future nodes` in Paths should be plain text only.

## Source-layer rule

Do not link public navigation nodes to `Maps/`, `Sources/`, or source-layer notes unless there is a specific reason. Source trace text is usually enough.

## Ghost link rule

Before committing, check dangling wikilinks across:

- `00 - Knowledge Library.md`
- `MOC/`
- `Nodes/`
- `Paths/`
- `Docs/`

If a useful concept has no node yet, write it as plain text in a future/missing section.
