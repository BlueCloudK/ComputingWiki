# PostgreSQL

Aliases: Postgres, PostgreSQL, PostgreSQL database

Type: Database / Tool

## Context / Ngữ cảnh

PostgreSQL là relational database open-source dùng nhiều cho application backend, analytics nhẹ, transaction và data integrity.

## Boundary / Ranh giới

### Nó là gì

Nó là database engine hỗ trợ SQL, ACID transaction, indexing, MVCC, replication, extension và nhiều kiểu dữ liệu.

### Nó không phải là gì

Nó không tự sửa schema xấu, query thiếu index, connection pool sai hoặc backup strategy thiếu kiểm tra.

## Core Mechanism / Cơ chế lõi

PostgreSQL xử lý query qua planner/executor, dùng MVCC cho concurrency, WAL cho durability và index/statistics để tối ưu truy vấn.

## Project Role / Vai trò trong dự án

Node này giúp debug slow query, lock, migration, transaction isolation, connection pool, replication lag và backup/restore.

## Output / Artifact nên có

- Schema/migration rõ
- Index và query plan cho endpoint quan trọng
- Backup, restore và vacuum/maintenance plan

## Decision Checklist / Câu hỏi kiểm tra

- Query quan trọng có `EXPLAIN` và index phù hợp không?
- Transaction isolation có phù hợp với race condition cần tránh không?
- Connection pool có khớp limit database không?
- Backup đã được restore thử chưa?

## Failure Modes / Cách nó gây lỗi

- Missing index làm latency tăng khi data lớn
- Long transaction giữ lock hoặc làm vacuum lag
- Pool quá lớn làm database hết connection

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tuning sâu khi dataset nhỏ và query rõ ràng
- Dễ over-engineer nếu thêm extension/partitioning trước khi đo bottleneck thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[ACID]] vì PostgreSQL thường được chọn vì transaction và consistency mạnh
- [[Query Optimizer]] vì planner quyết định performance của truy vấn

## Liên quan rộng

- Relational database
- Backend persistence
- Data integrity

## Keywords / Từ khóa tìm kiếm

- PostgreSQL
- Postgres
- relational database
- MVCC
- WAL
- query planner
- EXPLAIN ANALYZE
- database index

## Source trace

- PostgreSQL official documentation
