# Database Internals

Aliases: database internals, storage engine, query engine, nội bộ database

Type: MOC

## Context / Ngữ cảnh

Database Internals là vùng kiến thức về storage engine, query execution, indexing, concurrency, transaction log, replication và operational behavior của database.

## Boundary / Ranh giới

### Nó là gì

Đây là MOC điều hướng cho các node thuộc Database Internals.

### Nó không phải là gì

Nó không phải tutorial dài hoặc danh sách tool rời rạc; mục tiêu là map khái niệm để đi tiếp trong graph.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là gom node theo boundary, workflow, artifact, failure mode và operational signal.

## Project Role / Vai trò trong dự án

MOC này giúp chọn node cần đọc khi thiết kế, debug, deploy hoặc audit một phần hệ thống.

## Output / Artifact nên có

- Pack map
- Navigation links
- Source trace cấp vùng

## Decision Checklist / Câu hỏi kiểm tra

- Node mới có thuộc pack này thật không?
- Node đó có source trace và boundary rõ không?
- Link có giúp navigation hay chỉ làm graph nhiễu?

## Failure Modes / Cách nó gây lỗi

- Pack quá rộng làm người đọc không biết đi đâu
- Link quá nhiều làm graph nhiễu
- Node quá tool-specific nhưng không có cơ chế ổn định phía sau

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần chia sâu hơn nếu node chưa được dùng trong path hoặc project workflow
- Dễ over-engineer nếu biến MOC thành course hoặc tutorial

## Gồm những gì

- [[Storage Engine]]
- [[Buffer Pool]]
- [[Page Cache]]
- [[Database Page]]
- [[Heap File]]
- [[Tuple]]
- [[Row Store]]
- [[Column Store]]
- [[Storage Layout]]
- [[WAL Segment]]
- [[Transaction Log]]
- [[Redo Log]]
- [[Undo Log]]
- [[Checkpoint]]
- [[Crash Recovery]]
- [[Recovery Point Objective]]
- [[Recovery Time Objective]]
- [[Database Snapshot]]
- [[Vacuum]]
- [[Autovacuum]]
- [[Index Selectivity]]
- [[Cardinality Estimate]]
- [[Cost Based Optimizer]]
- [[Execution Plan]]
- [[Sequential Scan]]
- [[Index Scan]]
- [[Bitmap Index Scan]]
- [[Nested Loop Join]]
- [[Hash Join]]
- [[Merge Join]]
- [[Join Order]]
- [[Predicate Pushdown]]
- [[Projection Pushdown]]
- [[Covering Query]]
- [[Partial Index]]
- [[Expression Index]]
- [[Clustered Index]]
- [[Nonclustered Index]]
- [[Secondary Index]]
- [[Unique Index]]
- [[Two Phase Locking]]
- [[Shared Lock]]
- [[Exclusive Lock]]
- [[Row Lock]]
- [[Table Lock]]
- [[Gap Lock]]
- [[Intent Lock]]
- [[Deadlock Detection]]
- [[Lock Timeout]]
- [[Serialization Failure]]
- [[Dirty Read]]
- [[Non Repeatable Read]]
- [[Phantom Read]]
- [[Write Skew]]
- [[Lost Update]]
- [[Read Phenomena]]
- [[Snapshot Isolation]]
- [[Serializable Snapshot Isolation]]
- [[Optimistic Concurrency Control]]
- [[Pessimistic Concurrency Control]]
- [[Primary Replica]]
- [[Follower Replica]]
- [[Replication Slot]]
- [[Replication Stream]]
- [[Synchronous Replication]]
- [[Asynchronous Replication]]
- [[Replication Conflict]]
- [[Failover]]
- [[Leader Failover]]
- [[Split Brain Prevention]]
- [[Database Connection Limit]]
- [[Connection Pool Saturation]]
- [[Prepared Statement]]
- [[Query Cache]]
- [[Plan Cache]]
- [[Database Session]]
- [[Temporary Table]]
- [[Database Cursor]]
- [[Batch Write]]
- [[Bulk Load]]
- [[Data Compaction]]
- [[Tombstone]]
- [[Bloom Filter]]
- [[Memtable]]
- [[SSTable]]
- [[Write Amplification]]
- [[Read Amplification]]
- [[Compaction Strategy]]
- [[Hot Partition]]
- [[Database Hotspot]]
- [[Database Observability]]
- [[Slow Query Log]]
- [[Query Latency]]
- [[Lock Wait Time]]
- [[Replication Delay]]
- [[Database Vacuum Lag]]
- [[Index Bloat]]
- [[Table Bloat]]
- [[Database Maintenance Window]]
- [[Database Capacity Planning]]

## Nối mạnh


- Chưa có nối mạnh ngoài các node con trực tiếp
## Liên quan rộng

- Database Systems
- Data Intensive Systems
- Performance
- Debugging and Failure Patterns
- ComputingWiki expansion pack
- Project-oriented knowledge graph

## Keywords / Từ khóa tìm kiếm

- Database Internals
- database internals
- storage engine
- query engine
- nội bộ database

## Source trace

- Database System Concepts
- PostgreSQL documentation
- Designing Data-Intensive Applications
