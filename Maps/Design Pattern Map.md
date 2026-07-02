# Design Pattern Map

## Source Info

- Source: `https://refactoring.guru/design-patterns/catalog`
- Version: link-only
- Type: Design pattern catalog
- Use for: GoF pattern grouping

## Extracted Knowledge Tree

- [[Design Pattern]] - reusable design solution for recurring software design problems. `area` `source: Refactoring.Guru catalog`
  - [[Creational Pattern]] - patterns for object creation. `area` `source: catalog`
    - [[Factory Method]] - lets subclasses/implementations decide created object type. `pattern` `source: catalog`
    - [[Abstract Factory]] - creates families of related objects. `pattern` `source: catalog`
    - [[Builder]] - constructs complex objects step by step. `pattern` `source: catalog`
    - [[Prototype]] - creates objects by cloning existing ones. `pattern` `source: catalog`
    - [[Singleton]] - ensures one global instance. `pattern` `source: catalog`
  - [[Structural Pattern]] - patterns for composing objects/classes. `area` `source: catalog`
    - [[Adapter]] - makes incompatible interfaces work together. `pattern` `source: catalog`
    - [[Bridge]] - separates abstraction from implementation. `pattern` `source: catalog`
    - [[Composite]] - treats object trees uniformly. `pattern` `source: catalog`
    - [[Decorator]] - adds behavior by wrapping objects. `pattern` `source: catalog`
    - [[Facade]] - provides simplified interface to subsystem. `pattern` `source: catalog`
    - [[Proxy]] - placeholder controlling access to another object. `pattern` `source: catalog`
  - [[Behavioral Pattern]] - patterns for communication and responsibility among objects. `area` `source: catalog`
    - [[Chain of Responsibility]] - passes requests along handler chain. `pattern` `source: catalog`
    - [[Command]] - turns a request into an object. `pattern` `source: catalog`
    - [[Iterator]] - traverses collection without exposing internals. `pattern` `source: catalog`
    - [[Mediator]] - centralizes communication among objects. `pattern` `source: catalog`
    - [[Observer]] - notifies dependents when state changes. `pattern` `source: catalog`
    - [[State]] - changes behavior when internal state changes. `pattern` `source: catalog`
    - [[Strategy]] - swaps algorithms behind a common interface. `pattern` `source: catalog`
    - [[Template Method]] - defines algorithm skeleton with overridable steps. `pattern` `source: catalog`
    - [[Visitor]] - adds operations over object structure. `pattern` `source: catalog`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Design Pattern]] | [[Code Design]] | area | reusable design solution | catalog | existing node |
| [[Factory Method]] | [[Creational Pattern]] | pattern | delegate object creation | catalog | later node |
| [[Builder]] | [[Creational Pattern]] | pattern | stepwise object construction | catalog | later node |
| [[Adapter]] | [[Structural Pattern]] | pattern | interface compatibility wrapper | catalog | later node |
| [[Facade]] | [[Structural Pattern]] | pattern | simplified subsystem interface | catalog | later node |
| [[Observer]] | [[Behavioral Pattern]] | pattern | change notification | catalog | later node |
| [[State]] | [[Behavioral Pattern]] | pattern | behavior varies by state | catalog | later node |
| [[Strategy]] | [[Behavioral Pattern]] | pattern | interchangeable algorithm | catalog | later node |

## Notes

- Pattern nodes should be created only when useful, not all at once.
