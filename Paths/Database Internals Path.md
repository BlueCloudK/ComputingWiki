# Database Internals Path

## Mục tiêu

Path này giúp người đọc đi qua Database Internals theo thứ tự học hoặc làm project.

## Khi nào dùng path này

- Khi cần hiểu hoặc mở rộng vùng Database Internals.
- Khi thiết kế, debug, deploy hoặc audit hệ thống liên quan.
- Khi muốn đi theo route thay vì mở node ngẫu nhiên.

## 1. Storage engine

- [[Storage Engine]] — node nền để đi qua stage storage engine.
- [[Buffer Pool]] — node nền để đi qua stage storage engine.
- [[Page Cache]] — node nền để đi qua stage storage engine.
- [[Database Page]] — node nền để đi qua stage storage engine.
- [[Heap File]] — node nền để đi qua stage storage engine.

## 2. Indexes and planning

- [[Index Selectivity]] — node nền để đi qua stage indexes and planning.
- [[Cardinality Estimate]] — node nền để đi qua stage indexes and planning.
- [[Cost Based Optimizer]] — node nền để đi qua stage indexes and planning.
- [[Execution Plan]] — node nền để đi qua stage indexes and planning.
- [[Index Scan]] — node nền để đi qua stage indexes and planning.

## 3. Concurrency and transactions

- [[Two Phase Locking]] — node nền để đi qua stage concurrency and transactions.
- [[Deadlock Detection]] — node nền để đi qua stage concurrency and transactions.
- [[Read Phenomena]] — node nền để đi qua stage concurrency and transactions.
- [[Phantom Read]] — node nền để đi qua stage concurrency and transactions.
- [[Write Skew]] — node nền để đi qua stage concurrency and transactions.

## 4. Logs and recovery

- [[Transaction Log]] — node nền để đi qua stage logs and recovery.
- [[Checkpoint]] — node nền để đi qua stage logs and recovery.
- [[Crash Recovery]] — node nền để đi qua stage logs and recovery.
- [[Redo Log]] — node nền để đi qua stage logs and recovery.
- [[Undo Log]] — node nền để đi qua stage logs and recovery.

## 5. Replication and scaling

- [[Primary Replica]] — node nền để đi qua stage replication and scaling.
- [[Replication Slot]] — node nền để đi qua stage replication and scaling.
- [[Synchronous Replication]] — node nền để đi qua stage replication and scaling.
- [[Asynchronous Replication]] — node nền để đi qua stage replication and scaling.
- [[Failover]] — node nền để đi qua stage replication and scaling.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- Case studies
- Vendor-specific services
- Tool-specific commands

## Related paths

- [[Backend Engineering Path]]
- [[Cloud Infrastructure Path]]
- [[Debugging and Failure Patterns Path]]
