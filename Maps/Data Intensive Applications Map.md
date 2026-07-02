# Data Intensive Applications Map

## Source Info

- Source: `D:\Learning\Book for IT\Designing Data-Intensive Applications The Big Ideas Behind Reliable, Scalable, and Maintainable Systems by Martin Kleppmann (z-lib.org).pdf`
- Version: local PDF
- Type: Data systems book
- Use for: reliability, scalability, maintainability, distributed data systems

## Extracted Knowledge Tree

- [[Data Intensive Application]] - application whose main complexity comes from data volume, data flow, or data correctness. `area` `source: book outline`
  - [[Reliability]] - continuing to work correctly despite faults. `quality` `source: Ch01`
  - [[Scalability]] - ability to handle increased load. `quality` `source: Ch01`
    - [[Load]] - demand placed on a system. `concept` `source: Ch01`
    - [[Performance]] - response time/throughput behavior under load. `quality` `source: Ch01`
  - [[Maintainability]] - ease of operating, understanding, and changing the system. `quality` `source: Ch01`
    - [[Operability]] - ease of running the system. `quality` `source: Ch01`
    - [[Simplicity]] - reducing accidental complexity. `quality` `source: Ch01`
    - [[Evolvability]] - ease of making changes. `quality` `source: Ch01`
  - [[Data Model]] - way data is structured and queried. `area` `source: Ch02`
    - [[Relational Model]] - data represented as relations/tables. `model` `source: Ch02`
    - [[Document Model]] - data represented as nested documents. `model` `source: Ch02`
    - [[Graph Data Model]] - data represented as nodes and relationships. `model` `source: Ch02`
  - [[Storage and Retrieval]] - how databases store and fetch data. `area` `source: Ch03`
    - [[Hash Index]] - index based on hash lookup. `concept` `source: Ch03`
    - [[LSM Tree]] - log-structured merge tree storage/index approach. `concept` `source: Ch03`
    - [[B Tree]] - balanced tree index structure. `concept` `source: Ch03`
  - [[Encoding and Evolution]] - data formats and compatibility over time. `area` `source: Ch04`
    - [[Protocol Buffers]] - schema-based binary encoding. `technology/concept` `source: Ch04`
    - [[Avro]] - schema-based data serialization format. `technology/concept` `source: Ch04`
    - [[REST]] - service communication style. `concept` `source: Ch04`
    - [[RPC]] - remote procedure call communication style. `concept` `source: Ch04`
    - [[Message Passing]] - dataflow through asynchronous messages. `concept` `source: Ch04`
  - [[Distributed Data]] - data systems spread across machines. `area` `source: Part II`
    - [[Replication]] - copying data across nodes. `practice/concept` `source: Ch05`
    - [[Partitioning]] - splitting data across partitions. `practice/concept` `source: Ch06`
    - [[Distributed Transaction]] - transaction spanning distributed components. `concept` `source: Ch07`
    - [[Consistency]] - guarantees about visible data values/order. `concept` `source: Ch09`
    - [[Consensus]] - agreement among distributed nodes. `concept` `source: Ch09`
  - [[Derived Data]] - data produced from other data through processing. `area` `source: Part III`
    - [[Batch Processing]] - processing bounded datasets. `practice` `source: Ch10`
    - [[Stream Processing]] - processing ongoing event streams. `practice` `source: Ch11`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Reliability]] | [[Data Intensive Application]] | quality | continue working despite faults | Ch01 | candidate node |
| [[Scalability]] | [[Data Intensive Application]] | quality | cope with increased load | Ch01 | candidate node |
| [[Maintainability]] | [[Data Intensive Application]] | quality | ease of operation/change | Ch01 | candidate node |
| [[Replication]] | [[Distributed Data]] | concept/practice | keep copies across nodes | Ch05 | later node |
| [[Partitioning]] | [[Distributed Data]] | concept/practice | split data across partitions | Ch06 | later node |
| [[Consistency]] | [[Distributed Data]] | concept | guarantees about data views | Ch09 | later node |
| [[Stream Processing]] | [[Derived Data]] | practice | process continuous events | Ch11 | later node |

## Notes

- Advanced backend/data source; keep as reference unless project needs it.
