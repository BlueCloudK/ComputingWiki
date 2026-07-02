# SWEBOK Map

## Source Info

- Source: `D:\Learning\Book for IT\swebok-v4.pdf`
- Version: SWEBOK Guide V4.0
- Type: Software Engineering body of knowledge
- Use for: software engineering core map

## Extracted Knowledge Tree

- [[Software Engineering]] - systematic discipline for building, evolving, and operating software systems. `area` `source: SWEBOK Guide`
  - [[Software Requirements]] - what software must do and the constraints it must satisfy. `area` `source: Chapter 01`
    - [[Requirements Fundamentals]] - basic terms and categories of software requirements. `topic` `source: Ch01.1`
    - [[Requirements Elicitation]] - discovering and clarifying requirements from stakeholders and other sources. `practice` `source: Ch01.2`
    - [[Requirements Analysis]] - checking, refining, prioritizing, and resolving conflicts in requirements. `practice` `source: Ch01.3`
    - [[Requirements Specification]] - recording requirements in a structured and reviewable form. `artifact/practice` `source: Ch01.4`
    - [[Requirements Validation]] - checking whether requirements describe the right system. `practice` `source: Ch01.5`
    - [[Requirements Management]] - tracking requirement changes, scope, priority, and traceability. `practice` `source: Ch01.6`
  - [[Software Architecture]] - high-level structure of a software system and its key design decisions. `area` `source: Chapter 02`
    - [[Architecture Fundamentals]] - core ideas such as stakeholders, concerns, and architectural decisions. `topic` `source: Ch02.1`
    - [[Architecture Description]] - documenting architecture with views, viewpoints, patterns, and decisions. `artifact/practice` `source: Ch02.2`
    - [[Architecture Process]] - analyzing, synthesizing, and evaluating architecture. `practice` `source: Ch02.3`
    - [[Architecture Evaluation]] - checking whether architecture satisfies important qualities and constraints. `practice` `source: Ch02.4`
  - [[Software Design]] - shaping internal software structure below the architecture level. `area` `source: Chapter 03`
    - [[Design Fundamentals]] - basic design concepts, principles, and concerns. `topic` `source: Ch03.1`
    - [[Design Process]] - activities used to move from requirements/architecture to detailed design. `practice` `source: Ch03.2`
    - [[Design Quality]] - qualities that make a design understandable, maintainable, and fit for purpose. `topic` `source: Ch03.3`
    - [[Design Documentation]] - artifacts that record design decisions and structures. `artifact` `source: Ch03.4`
    - [[Design Strategies and Methods]] - approaches and methods for producing designs. `practice` `source: Ch03.5`
  - [[Software Construction]] - coding, debugging, and integrating working software. `area` `source: Chapter 04`
    - [[Construction Fundamentals]] - basic coding and construction concepts. `topic` `source: Ch04`
    - [[Managing Construction]] - organizing construction work and controlling change. `practice` `source: Ch04`
    - [[Construction Technologies]] - tools, languages, platforms, and practices used to build software. `topic` `source: Ch04`
  - [[Software Testing]] - evaluating software behavior and quality through static and dynamic checks. `area` `source: SWEBOK testing chapter`
    - [[Testing Fundamentals]] - basic testing purpose, terminology, and principles. `topic` `source: testing chapter`
    - [[Test Levels]] - levels such as unit, integration, system, and acceptance testing. `topic` `source: testing chapter`
    - [[Test Techniques]] - methods for designing tests. `practice` `source: testing chapter`
    - [[Test Process]] - planning, designing, executing, and reporting tests. `practice` `source: testing chapter`
  - [[Software Engineering Operations]] - running software in real environments after release. `area` `source: SWEBOK operations area`
    - [[Deployment]] - releasing software into an environment where it can run. `practice` `source: operations area`
    - [[Monitoring]] - observing running software with logs, metrics, and alerts. `practice` `source: operations area`
    - [[Incident Management]] - responding to production problems and restoring service. `practice` `source: operations area`
    - [[Reliability]] - ability of software to keep working under expected conditions. `quality` `source: operations/quality areas`
  - [[Software Maintenance]] - modifying software after delivery to fix, adapt, improve, or prevent problems. `area` `source: maintenance area`
  - [[Software Configuration Management]] - controlling versions, baselines, builds, and changes. `area` `source: SCM area`
  - [[Software Engineering Management]] - planning, estimating, tracking, and managing software work. `area` `source: management area`
  - [[Software Engineering Process]] - lifecycle processes used to produce and evolve software. `area` `source: process area`
  - [[Software Quality]] - degree to which software satisfies required qualities. `area` `source: quality area`
  - [[Software Security]] - engineering software to resist misuse, attack, and unsafe exposure. `area` `source: security area`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Requirements]] | [[Software Engineering]] | area | software needs and constraints | SWEBOK Ch01 | MOC/node |
| [[Requirements Elicitation]] | [[Software Requirements]] | practice | discover requirements from stakeholders/sources | SWEBOK Ch01.2 | candidate node |
| [[Requirements Analysis]] | [[Software Requirements]] | practice | refine and resolve requirement issues | SWEBOK Ch01.3 | candidate node |
| [[Software Architecture]] | [[Software Engineering]] | area | high-level system structure and decisions | SWEBOK Ch02 | MOC/node |
| [[Architecture Description]] | [[Software Architecture]] | artifact/practice | document architecture with views and decisions | SWEBOK Ch02.2 | candidate node |
| [[Software Design]] | [[Software Engineering]] | area | internal software structure and detailed decisions | SWEBOK Ch03 | MOC/node |
| [[Software Construction]] | [[Software Engineering]] | area | coding and integrating software | SWEBOK Ch04 | candidate node |
| [[Software Testing]] | [[Software Engineering]] | area | checking software quality and behavior | SWEBOK testing chapter | map to [[Testing and Verification]] |
| [[Software Maintenance]] | [[Software Engineering]] | area | evolving software after delivery | SWEBOK maintenance area | candidate node |
| [[Software Security]] | [[Software Engineering]] | area | security as engineering concern | SWEBOK security area | map to [[Security]] |

## Notes

- This map is shallow-plus: enough metadata to judge node usefulness, not a summary of the book.
