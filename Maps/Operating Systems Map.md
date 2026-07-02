# Operating Systems Map

## Source Info

- Source: `D:\Learning\Book for IT\ModernOperatingSystems4thEdition.pdf`
- Version: 4th edition
- Type: Operating systems textbook
- Use for: OS concepts and runtime foundations

## Extracted Knowledge Tree

- [[Operating System]] - software layer that manages hardware resources and provides services to programs. `area` `source: Ch01`
  - [[Operating System Concepts]] - basic abstractions exposed by an OS. `topic` `source: Ch01.5`
    - [[Process]] - running program with its own execution context. `concept` `source: Ch01.5/Ch02.1`
    - [[Address Space]] - memory abstraction available to a process. `concept` `source: Ch01.5/Ch03`
    - [[File]] - persistent named data object. `concept` `source: Ch01.5/Ch04`
    - [[Input Output]] - interaction with devices. `area` `source: Ch01.5/Ch05`
    - [[Protection]] - mechanisms controlling access and isolation. `concept` `source: Ch01.5/security chapter`
  - [[System Call]] - interface through which programs request OS services. `concept` `source: Ch01.6`
  - [[Operating System Structure]] - internal organization of OS components. `area` `source: Ch01.7`
    - [[Monolithic System]] - OS structure with many services in one kernel. `architecture` `source: Ch01.7`
    - [[Microkernel]] - OS structure with minimal kernel and user-space services. `architecture` `source: Ch01.7`
    - [[Virtual Machine]] - abstraction that emulates a machine. `concept` `source: Ch01.7`
  - [[Processes and Threads]] - execution and concurrency abstractions. `area` `source: Ch02`
    - [[Thread]] - lightweight execution path within a process. `concept` `source: Ch02.2`
    - [[Interprocess Communication]] - communication between processes. `concept/practice` `source: Ch02.3`
    - [[Race Condition]] - bug caused by timing-dependent shared access. `concept` `source: Ch02.3`
    - [[Mutex]] - mutual exclusion synchronization primitive. `concept` `source: Ch02.3`
    - [[Scheduling]] - choosing which task runs next. `practice` `source: Ch02.4`
  - [[Memory Management]] - allocation and abstraction of memory. `area` `source: Ch03`
    - [[Virtual Memory]] - memory abstraction backed by paging/storage. `concept` `source: Ch03.3`
    - [[Page Replacement]] - policy for choosing pages to evict. `practice` `source: Ch03.4`
  - [[File System]] - organization and management of persistent files. `area` `source: Ch04`
  - [[Deadlock]] - state where tasks wait forever for each other. `concept` `source: later chapter`
  - [[Virtualization]] - running systems on virtual machine abstractions. `area` `source: later chapter`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Operating System]] | [[Computing Foundations]] | area | manages resources and programs | Ch01 | candidate node |
| [[Process]] | [[Processes and Threads]] | concept | running program context | Ch02.1 | candidate node |
| [[Thread]] | [[Processes and Threads]] | concept | lightweight execution path | Ch02.2 | candidate node |
| [[Memory Management]] | [[Operating System]] | area | manages memory allocation/abstraction | Ch03 | candidate node |
| [[File System]] | [[Operating System]] | area | manages persistent files | Ch04 | candidate node |
| [[Concurrency]] | [[Processes and Threads]] | concept | multiple tasks interacting/executing | Ch02 | candidate node |

## Notes

- Useful when project debugging touches OS/runtime behavior.
