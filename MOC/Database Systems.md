# Database Systems

Aliases: database system, hệ quản trị dữ liệu, DBMS, database management system, hệ quản trị cơ sở dữ liệu

Type: Data / Database

## Context / Ngữ cảnh

Database Systems xuất hiện khi hệ thống cần lưu, truy vấn, migrate, kiểm soát consistency hoặc hiểu dữ liệu qua thời gian. Nó thường nằm trong database schema, data model, query path hoặc integration payload.

## Boundary / Ranh giới

### Nó là gì

Database Systems là một phần của cách dữ liệu được biểu diễn, ràng buộc, truy cập hoặc giữ đúng trong hệ thống.

### Nó không phải là gì

Nó không chỉ là nơi cất data; nếu thiếu schema, constraint, transaction hoặc migration strategy thì code rất dễ phải vá dữ liệu sai.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi xoay quanh model/schema, relationship, constraint, transaction, index và migration. Những thứ này quyết định dữ liệu có nhất quán, truy vấn có nhanh và thay đổi có an toàn không.

## Project Role / Vai trò trong dự án

Database Systems là MOC điều hướng: dùng để đi từ vùng lớn xuống node cụ thể, không thay thế node chi tiết. Khi review graph, trang này giúp chọn đúng nhánh cần đọc và tránh link rộng làm rối.

## Output / Artifact nên có

- Schema/model hoặc migration note rõ thay đổi dữ liệu
- Constraint/index/transaction decision nếu ảnh hưởng consistency/performance
- Checklist backup, audit hoặc data validation cho dữ liệu quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Schema có biểu diễn đúng relationship và cardinality không?
- Migration có plan rollback/backfill và kiểm tra dữ liệu sau chạy không?
- Transaction boundary có đủ giữ consistency không?
- Query chính có index và baseline performance chưa?
- Dữ liệu quan trọng có backup/history/audit đủ truy vết không?

## Failure Modes / Cách nó gây lỗi

- Schema sai làm code phải vá vòng quanh
- Migration mất dữ liệu hoặc gây downtime
- Transaction/consistency yếu làm dữ liệu lệch giữa service
- Query thiếu index làm production chậm khi data tăng

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần model phức tạp khi dữ liệu nhỏ, ít quan hệ và dễ migrate
- Dễ over-engineer nếu normalize/partition/cache trước khi có query pattern thật

## Gồm những gì

- [[Database System]]
- [[Relational Model]]
- [[Database Schema]]
- [[SQL]]
- [[Query]]
- [[Join]]
- [[View]]
- [[Trigger]]
- [[Index]]
- [[Transaction Management]]
- [[Concurrency Control]]
- [[Recovery System]]
- [[ACID]]
- [[Isolation Level]]
- [[Read Committed]]
- [[Repeatable Read]]
- [[Serializable]]
- [[MVCC]]
- [[Database Lock]]
- [[Query Optimizer]]
- [[Query Plan]]
- [[Database Migration]]
- [[Backup Strategy]]
- [[Write Ahead Log]]
- [[Connection Pooling]]
- [[Database Index]]
- [[Composite Index]]
- [[Covering Index]]
- [[Unique Constraint]]
- [[Check Constraint]]
- [[Stored Procedure]]
- [[Materialized View]]
- [[Query Execution]]
- [[Query Planner]]
- [[Database Statistics]]
- [[Lock Contention]]
- [[Optimistic Locking]]
- [[Pessimistic Locking]]
- [[Read Replica]]
- [[Replication Lag]]
- [[Database Sharding]]
- [[Horizontal Partitioning]]
- [[Vertical Partitioning]]
- [[Denormalization]]
- [[Schema Evolution]]
- [[Online Migration]]
- [[Migration Rollback]]
- [[Backup Restore]]
- [[Point In Time Recovery]]
- [[Disaster Recovery]]
- [[Data Retention]]
- [[Archival]]
- [[Data Consistency]]
- [[Referential Integrity]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database
- Backend
- Data migration
- Observability

## Keywords / Từ khóa tìm kiếm

- Database Systems
- database systems design
- database systems validation
- xử lý dữ liệu
- Database Systems MOC
- database systems map
- mục lục kiến thức
- nhánh kiến thức
- database system
- hệ quản trị dữ liệu
- DBMS
- database management system
- hệ quản trị cơ sở dữ liệu
- data model
- query design

## Source trace

- Database Systems Map
