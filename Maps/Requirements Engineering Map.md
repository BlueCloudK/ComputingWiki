# Requirements Engineering Map

## Source Info

- Source: `D:\Learning\Book for IT\Requirements Engineering - A Good Practice Guide.pdf`
- Source: `D:\Learning\Book for IT\Software_Requirements_3rd_Edition.pdf`
- Version: local PDFs
- Type: Requirements engineering books
- Use for: requirements, elicitation, specification, validation, management

## Extracted Knowledge Tree

- [[Requirements Engineering]] - discipline for discovering, analyzing, specifying, validating, and managing requirements. `area` `source: RE guide Ch01 / Software Requirements Part I`
  - [[Requirement]] - need, capability, or constraint the system/product must satisfy. `concept` `source: RE guide Ch01 / SR Ch01`
    - [[Functional Requirement]] - behavior or function the system must provide. `concept` `source: RE guide Ch01 / SR Ch01`
    - [[Nonfunctional Requirement]] - quality or constraint on how the system performs. `concept` `source: RE guide Ch01 / SR Ch14`
    - [[Business Requirement]] - business objective or desired benefit. `concept` `source: SR Ch05`
    - [[User Requirement]] - user goal or task-level need. `concept` `source: SR Ch06-Ch08`
    - [[System Requirement]] - system-level capability or constraint. `concept` `source: RE guide Ch01`
    - [[Quality Attribute]] - quality concern such as performance, usability, reliability, or security. `quality` `source: SR Ch14`
  - [[Requirements Process]] - lifecycle of requirements work. `practice` `source: RE guide Ch01 / SR Ch03`
    - [[Requirements Elicitation]] - discovering requirements from stakeholders, context, and sources. `practice` `source: RE guide Ch04 / SR Ch06-Ch08`
    - [[Requirements Analysis]] - refining, prioritizing, and resolving requirement issues. `practice` `source: RE guide Ch05`
    - [[Requirements Specification]] - documenting requirements in useful representations. `artifact/practice` `source: RE guide Ch06 / SR Ch10-Ch13`
    - [[Requirements Validation]] - checking requirements for correctness and fitness. `practice` `source: RE guide Ch08 / SR Ch17`
    - [[Requirements Management]] - controlling change, status, traceability, and baselines. `practice` `source: RE guide Ch09 / SR Part IV`
  - [[Requirements Elicitation]] - collecting and clarifying requirements. `practice` `source: RE guide Ch04`
    - [[Stakeholder]] - person/group with interest or influence in the system. `concept` `source: RE guide Ch04.3 / SR Ch06`
    - [[Requirements Source]] - origin of requirement information. `concept` `source: RE guide Ch04.4`
    - [[Operating Environment]] - context where the system runs. `concept` `source: RE guide Ch04.5`
    - [[Domain Constraint]] - rule from the problem domain. `concept` `source: RE guide Ch04.7`
    - [[Scenario]] - story-like description of system use. `artifact` `source: RE guide Ch04.11`
    - [[Prototype]] - rough version used to explore uncertain requirements. `artifact/practice` `source: RE guide Ch04.10 / SR Ch15`
  - [[Requirements Modeling]] - representing requirements with diagrams/tables/models. `practice` `source: RE guide Ch07 / SR Ch12`
    - [[System Context Diagram|Context Diagram]] - diagram showing system boundary and external actors/systems. `artifact` `source: SR Ch05/Ch12`
    - [[Use Case]] - goal-oriented interaction between actor and system. `artifact` `source: SR Ch08`
    - [[Data Flow Diagram]] - model of data movement through processes. `artifact` `source: SR Ch12`
    - [[State Transition Diagram]] - model of states and transitions. `artifact` `source: SR Ch12`
    - [[Decision Table]] - tabular model of conditions and outcomes. `artifact` `source: SR Ch12`
    - [[Event Response Table]] - mapping events to system responses. `artifact` `source: SR Ch12`
  - [[Requirements Management]] - managing requirement changes and traceability. `practice` `source: RE guide Ch09 / SR Ch27-Ch30`
    - [[Requirement ID]] - unique identifier for a requirement. `artifact` `source: RE guide Ch09.1`
    - [[Traceability]] - links between requirements, design, code, and tests. `practice` `source: RE guide Ch09.3 / SR Ch29`
    - [[Change Control]] - process for evaluating and accepting requirement changes. `practice` `source: RE guide Ch09.6 / SR Ch28`
    - [[Impact Analysis]] - assessing effects of a proposed change. `practice` `source: SR Ch28`
    - [[Requirements Baseline]] - agreed requirement set used as reference. `artifact` `source: SR Ch27`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Requirements]] | [[Requirements Engineering]] | area | system needs and constraints | RE guide Ch01 / SR Ch01 | MOC/node |
| [[Use Case]] | [[Requirements Modeling]] | artifact | actor-goal interaction model | SR Ch08 | existing node |
| [[Acceptance Criteria]] | [[Requirements Validation]] | artifact | condition for accepting a requirement/feature | SR Ch17 | existing node |
| [[Stakeholder]] | [[Requirements Elicitation]] | concept | person/group with system interest | RE guide Ch04.3 | candidate node |
| [[Scope]] | [[Business Requirement]] | concept/artifact | boundary of included/excluded work | SR Ch05 | existing node |
| [[Traceability]] | [[Requirements Management]] | practice | links requirements to downstream artifacts | SR Ch29 | candidate node |
| [[Change Control]] | [[Requirements Management]] | practice | governed requirement change process | SR Ch28 | candidate node |
| [[Business Rule]] | [[Requirements Modeling]] | concept | rule that constrains business behavior | SR Ch09 | candidate node |

## Notes

- This combines two requirements sources to avoid duplicate requirement trees.
