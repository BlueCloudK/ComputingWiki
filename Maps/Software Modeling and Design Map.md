# Software Modeling and Design Map

## Source Info

- Source: `D:\Learning\Book for IT\gomaa-softwaremodellinganddesign.pdf`
- Version: local PDF
- Type: Software modeling and design book
- Use for: UML, modeling, software architecture, object-oriented design

## Extracted Knowledge Tree

- [[Software Modeling and Design]] - using models and design methods to shape software before/during construction. `area` `source: contents`
  - [[UML Notation]] - standard visual notation for object-oriented analysis/design. `language/artifact` `source: Ch02`
  - [[Software Life Cycle Model]] - structure of software development stages. `concept` `source: Ch03`
  - [[Software Design Concept]] - core ideas for organizing software design. `topic` `source: Ch04`
  - [[Software Architecture Concept]] - core ideas for high-level software structure. `topic` `source: Ch04`
  - [[Software Modeling Method]] - method for producing and using software models. `practice` `source: Ch05`
- [[Software Modeling]] - representing software behavior, structure, and interactions. `area` `source: Part II`
  - [[Use Case Modeling]] - modeling actor goals and system interactions. `practice` `source: Ch06`
  - [[Static Modeling]] - modeling stable structures such as classes and relationships. `practice` `source: Ch07`
  - [[Object and Class Structuring]] - organizing classes and objects. `practice` `source: Ch08`
  - [[Dynamic Interaction Modeling]] - modeling runtime interactions. `practice` `source: Ch09`
  - [[Finite State Machine]] - model of states and transitions. `model` `source: Ch10`
  - [[State Dependent Interaction Modeling]] - modeling behavior that depends on state. `practice` `source: Ch11`
- [[Architectural Design]] - designing high-level organization of software systems. `area` `source: Part III`
  - [[Software Architecture]] - high-level software structure and decisions. `area` `source: Ch12`
  - [[Subsystem Architecture]] - architecture organized into subsystems. `architecture` `source: Ch13`
  - [[Object-Oriented Architecture]] - architecture built around objects/classes. `architecture` `source: Ch14`
  - [[Client Server Architecture]] - architecture split between clients and servers. `architecture` `source: Ch15`
  - [[Service Oriented Architecture]] - architecture organized around services. `architecture` `source: Ch16`
  - [[Component Based Architecture]] - architecture composed of components. `architecture` `source: Ch17`
  - [[Concurrent Architecture]] - architecture addressing concurrent execution. `architecture` `source: Ch18`
  - [[Real Time Architecture]] - architecture with time constraints. `architecture` `source: Ch18`
  - [[Software Product Line Architecture]] - architecture supporting related product variants. `architecture` `source: Ch19`
  - [[Quality Attribute]] - externally meaningful system quality concern. `quality` `source: Ch20`
- [[Architecture Pattern]] - reusable structure for architecture problems. `area` `source: Appendix A`
  - [[Architectural Structure Pattern]] - pattern for organizing architectural elements. `pattern` `source: Appendix A.1`
  - [[Architectural Communication Pattern]] - pattern for communication among architectural elements. `pattern` `source: Appendix A.2`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Use Case Modeling]] | [[Software Modeling]] | practice | model user-system goals/interactions | Ch06 | candidate node |
| [[Class Diagram]] | [[Static Modeling]] | artifact | model classes and relationships | Ch07 | candidate node |
| [[Sequence Diagram]] | [[Dynamic Interaction Modeling]] | artifact | model object interactions over time | Ch09 | candidate node |
| [[State Machine]] | [[Finite State Machine]] | model | states and allowed transitions | Ch10 | existing node |
| [[Software Architecture]] | [[Architectural Design]] | area | high-level structure/decisions | Ch12 | MOC/node |
| [[Quality Attribute]] | [[Architectural Design]] | quality | system quality concern | Ch20 | candidate node |

## Notes

- Good bridge from requirements into architecture/design nodes.
