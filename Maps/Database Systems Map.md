# Database Systems Map

## Source Info

- Source: `D:\Learning\Book for IT\Database System Concepts 7th Ed.pdf`
- Version: 7th edition
- Type: Database systems textbook
- Use for: database, relational model, SQL, design, transactions, indexing

## Extracted Knowledge Tree

- [[Database System]] - system for storing, querying, and managing structured data. `area` `source: Chapter 1`
  - [[View of Data]] - abstraction levels for how data is seen. `concept` `source: Ch01.3`
  - [[Database Language]] - languages for defining and querying data. `topic` `source: Ch01.4`
  - [[Database Design]] - process of designing data structure. `practice` `source: Ch01.5`
  - [[Database Engine]] - components that execute storage and query work. `topic` `source: Ch01.6`
  - [[Database Architecture]] - application/database deployment structure. `topic` `source: Ch01.7`
- [[Relational Model]] - table-based model using relations, schemas, and keys. `area` `source: Part One Ch02`
  - [[Relation]] - table-like set of tuples. `concept` `source: Ch02.1`
  - [[Database Schema]] - formal structure of database objects. `artifact` `source: Ch02.2`
  - [[Key]] - attribute(s) used to identify records. `concept` `source: Ch02.3`
  - [[Schema Diagram]] - visual representation of schema. `artifact` `source: Ch02.4`
  - [[Relational Algebra]] - formal operations over relations. `concept` `source: Ch02.6`
- [[SQL]] - standard language for defining and querying relational databases. `area` `source: Ch03-Ch05`
  - [[Data Definition]] - SQL statements that define schema objects. `practice` `source: Ch03.2`
  - [[Query]] - request to retrieve data. `concept/practice` `source: Ch03`
  - [[Join]] - operation combining rows from relations. `concept` `source: Ch04.1`
  - [[View]] - named query presented as a virtual table. `artifact` `source: Ch04.2`
  - [[Transaction]] - unit of work with consistency guarantees. `concept` `source: Ch04.3`
  - [[Integrity Constraint]] - rule that valid database states must satisfy. `concept` `source: Ch04.4`
  - [[Index]] - structure that speeds up data access. `concept/artifact` `source: Ch04.6/Part Five`
  - [[Trigger]] - database action fired by an event. `concept` `source: Ch05.3`
- [[Database Design]] - modeling and structuring data for good relational design. `practice` `source: Part Two`
  - [[ERD]] - diagram for entities and relationships. `artifact` `source: Ch06`
  - [[Entity]] - thing represented in a data model. `concept` `source: Ch06.2`
  - [[Relationship]] - association between entities. `concept` `source: Ch06.2`
  - [[Mapping Cardinality]] - relationship count constraints. `concept` `source: Ch06.4`
  - [[Primary Key]] - key chosen to identify records. `concept` `source: Ch06.5`
  - [[Foreign Key]] - attribute referencing another relation. `concept` `source: Ch06/Ch04`
  - [[Normalization]] - decomposition to reduce redundancy and anomalies. `practice` `source: Ch07.3`
  - [[Functional Dependency]] - constraint used in normalization. `concept` `source: Ch07.2`
- [[Transaction Management]] - ensuring correct concurrent and recoverable database operations. `area` `source: Part Seven`
  - [[Concurrency Control]] - techniques for safe concurrent transactions. `practice` `source: Ch18`
  - [[Recovery System]] - restoring database after failures. `practice` `source: Ch19`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Database System|Database]] | [[Database System]] | area | durable data management system | Ch01 | MOC/node |
| [[Database Schema]] | [[Relational Model]] | artifact | database structure definition | Ch02.2 | candidate node |
| [[ERD]] | [[Database Design]] | artifact | entity relationship diagram | Ch06 | existing node |
| [[SQL]] | [[Database System]] | language/topic | relational query language | Ch03-Ch05 | candidate node |
| [[Index]] | [[SQL]] | artifact/concept | access structure for faster lookup | Ch04.6/Part Five | existing node |
| [[Transaction]] | [[SQL]] | concept | atomic unit of database work | Ch04.3/Part Seven | candidate node |
| [[Normalization]] | [[Database Design]] | practice | reduce redundancy through decomposition | Ch07 | candidate node |

## Notes

- Strong source for Data and Database MOC.
