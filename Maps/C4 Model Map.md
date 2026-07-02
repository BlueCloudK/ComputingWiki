# C4 Model Map

## Source Info

- Source: `https://c4model.com/`
- Version: link-only
- Type: Software architecture diagram model
- Use for: architecture diagram nodes

## Extracted Knowledge Tree

- [[C4 Model]] - model for describing software architecture at multiple abstraction levels. `area/model` `source: c4model.com`
  - [[System Context Diagram]] - shows software system, users, and external systems. `artifact` `source: C4 model level 1`
  - [[Container Diagram]] - shows deployable/runnable containers inside a system. `artifact` `source: C4 model level 2`
  - [[Component Diagram]] - shows components inside a container. `artifact` `source: C4 model level 3`
  - [[Code Diagram]] - optional low-level code structure view. `artifact` `source: C4 model level 4`
  - [[Supplementary Diagram]] - additional diagrams for special views. `artifact` `source: C4 supplementary diagrams`
    - [[System Landscape Diagram]] - broad view of multiple systems. `artifact` `source: C4 supplementary`
    - [[Dynamic Diagram]] - shows runtime interactions over time. `artifact` `source: C4 supplementary`
    - [[Deployment Diagram]] - shows deployment environment and runtime nodes. `artifact` `source: C4 supplementary`
  - [[Abstraction Level]] - level of detail used to describe architecture. `concept` `source: C4 model`
  - [[Software System]] - system being described. `concept` `source: C4 model`
  - [[Container]] - deployable/runnable unit such as app, API, database. `concept` `source: C4 model`
  - [[Component]] - structural part inside a container. `concept` `source: C4 model`
  - [[Relationship]] - connection or dependency between elements. `concept` `source: C4 model`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Architecture Diagram]] | [[Software Architecture]] | artifact | visual architecture representation | C4 model | candidate node |
| [[C4 Model]] | [[Software Architecture]] | model | four-level architecture view model | c4model.com | candidate node |
| [[System Context Diagram]] | [[C4 Model]] | artifact | users/external systems around system | C4 level 1 | candidate node |
| [[Container Diagram]] | [[C4 Model]] | artifact | apps/services/databases inside system | C4 level 2 | candidate node |
| [[Component Diagram]] | [[C4 Model]] | artifact | components inside container | C4 level 3 | candidate node |
| [[Deployment Diagram]] | [[Supplementary Diagram]] | artifact | runtime deployment view | C4 supplementary | candidate node |

## Notes

- Useful for project architecture notes and AI context handoff.
