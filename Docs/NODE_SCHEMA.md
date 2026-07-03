# NODE_SCHEMA

## Standard node format

Use this public ComputingWiki node format for concept nodes:

```md
# English Name

Aliases: ...

Type: ...

## Context / Ngữ cảnh

## Boundary / Ranh giới

### Nó là gì

### Nó không phải là gì

## Core Mechanism / Cơ chế lõi

## Project Role / Vai trò trong dự án

## Output / Artifact nên có

## Decision Checklist / Câu hỏi kiểm tra

## Failure Modes / Cách nó gây lỗi

## Khi nào chưa cần hoặc dễ over-engineer

## Gồm những gì

## Nối mạnh

## Liên quan rộng

## Keywords / Từ khóa tìm kiếm

## Source trace
```

## Field rules

`Aliases:` should contain real alternative names, acronyms, and Vietnamese names when useful. Do not stuff unrelated keywords here.

`Type:` should classify the node as an area, concept, artifact, practice, pattern, protocol, tool, or system concern.

`Context / Ngữ cảnh` explains when the concept appears and why a reader would care.

`Boundary / Ranh giới` separates what the concept is from what it is not. This prevents vague or overloaded notes.

`Core Mechanism / Cơ chế lõi` explains the stable mechanism behind the concept.

`Project Role / Vai trò trong dự án` explains how the concept affects design, implementation, debugging, testing, deployment, or operations.

`Output / Artifact nên có` names concrete artifacts such as config, schema, decision note, diagram, metric, test, runbook, policy, or checklist.

`Decision Checklist / Câu hỏi kiểm tra` contains questions specific to the node. Avoid generic questions that could fit any concept.

`Failure Modes / Cách nó gây lỗi` explains concrete ways the concept can break a project or system.

`Khi nào chưa cần hoặc dễ over-engineer` explains when the concept is not needed yet or becomes too heavy.

`Gồm những gì` is for direct child/component wikilinks only.

`Nối mạnh` is for strong wikilinks with a short reason.

`Liên quan rộng` is text only. Do not use wikilinks there.

`Keywords / Từ khóa tìm kiếm` is for search terms only. Do not use wikilinks.

`Source trace` should be short and in English.
