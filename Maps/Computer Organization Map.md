# Computer Organization Map

## Source Info

- Source: `D:\Learning\Book for IT\Computer Organization and Architecture.pdf`
- Version: local PDF
- Type: Computer organization and architecture textbook
- Use for: hardware and architecture foundations

## Extracted Knowledge Tree

- [[Computer Organization and Architecture]] - how computer hardware is structured and behaves. `area` `source: contents`
  - [[Organization and Architecture]] - distinction between visible architecture and implementation organization. `concept` `source: Ch01.1`
  - [[Structure and Function]] - computer parts and what they do. `concept` `source: Ch01.2`
  - [[Embedded Systems]] - computing systems built into larger devices. `area` `source: Ch01.5`
  - [[Computer Performance]] - measures and models of hardware performance. `area` `source: Ch02`
    - [[Amdahl Law]] - limit of speedup from partial improvement. `concept` `source: Ch02.3`
    - [[Little Law]] - relationship among throughput, latency, and concurrency. `concept` `source: Ch02.3`
    - [[Benchmark]] - repeatable measurement workload. `practice/artifact` `source: Ch02.6`
  - [[Computer Function and Interconnection]] - top-level components and how they connect. `area` `source: Ch03`
  - [[Memory System]] - hierarchy and behavior of memory/storage. `area` `source: Ch04-Ch06`
    - [[Cache Memory]] - small fast memory near CPU. `concept` `source: Ch04`
    - [[Internal Memory]] - main memory and semiconductor memory. `topic` `source: Ch05`
    - [[External Memory]] - disks, SSDs, optical/tape storage. `topic` `source: Ch06`
  - [[Input Output]] - communication with external devices. `area` `source: Ch07`
  - [[Processor]] - CPU organization and execution. `area` `source: later chapters`
  - [[Instruction Set]] - operations visible to machine code. `topic` `source: later chapters`
  - [[Parallel Organization]] - hardware organization for parallelism. `area` `source: later chapters`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Computer Architecture]] | [[Computer Organization and Architecture]] | area | hardware-visible system structure | Ch01 | candidate node |
| [[CPU]] | [[Processor]] | component | executes instructions | Ch03/later | candidate node |
| [[Cache]] | [[Memory System]] | concept/component | fast memory for repeated access | Ch04 | candidate node |
| [[Memory]] | [[Memory System]] | area | storage hierarchy for data/instructions | Ch04-Ch06 | candidate node |
| [[Benchmark]] | [[Computer Performance]] | practice | repeatable performance measurement | Ch02.6 | existing node |

## Notes

- PDF had no outline; extracted from contents pages.
