# Database Engineering Path

## Mục tiêu

Path này giúp người đọc đi từ modeling dữ liệu tới query, transaction, migration, performance và recovery.

## Khi nào dùng path này

- Khi thiết kế schema hoặc data access layer.
- Khi debug query chậm, transaction lỗi hoặc migration rủi ro.
- Khi cần hiểu database như một system vận hành.

## 1. Modeling và schema

- [[Data Model]] — mô hình hóa dữ liệu và quan hệ.
- [[Relational Model]] — nền của database quan hệ.
- [[Entity]] — đối tượng dữ liệu chính.
- [[Relationship]] — quan hệ giữa entity.
- [[Database Schema]] — cấu trúc table, column, key và constraint.
- [[Primary Key]] — định danh row.
- [[Foreign Key]] — giữ quan hệ giữa bảng.

## 2. Query và access

- [[SQL]] — ngôn ngữ truy vấn phổ biến.
- [[Query]] — thao tác đọc/ghi dữ liệu.
- [[Join]] — kết hợp dữ liệu từ nhiều relation.
- [[View]] — query được đặt tên để dùng lại.
- [[Materialized View]] — view lưu kết quả sẵn.
- [[ORM]] — data access qua object/application model.

## 3. Integrity và transaction

- [[ACID]] — tính chất transaction quan trọng.
- [[Transaction]] — nhóm thao tác commit/rollback cùng nhau.
- [[Isolation Level]] — mức transaction nhìn thấy thay đổi của nhau.
- [[MVCC]] — concurrency bằng version dữ liệu.
- [[Integrity Constraint]] — rule bảo vệ dữ liệu.
- [[Referential Integrity]] — đảm bảo reference giữa bảng hợp lệ.

## 4. Performance

- [[Database Index]] — tăng tốc lookup/query.
- [[B Tree]] — cấu trúc index phổ biến.
- [[Composite Index]] — index nhiều cột.
- [[Query Plan]] — kế hoạch database dùng để chạy query.
- [[Query Optimizer]] — chọn query plan dựa trên cost/statistics.
- [[Lock Contention]] — lock làm transaction chờ nhau.
- [[Connection Pooling]] — quản lý connection hiệu quả.

## 5. Change và operation

- [[Database Migration]] — thay đổi schema/data theo version.
- [[Online Migration]] — migration khi service vẫn chạy.
- [[Migration Rollback]] — quay lui khi migration lỗi.
- [[Backup Strategy]] — chiến lược backup dữ liệu.
- [[Backup Restore]] — phục hồi từ backup.
- [[Point In Time Recovery]] — restore về thời điểm cụ thể.
- [[Disaster Recovery]] — phục hồi sau sự cố lớn.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- Query anti-pattern
- Database vacuum
- Index selectivity
- Schema registry
- Database observability

## Related paths

- [[Backend Engineering Path]]
- [[Debugging and Failure Patterns Path]]
- [[API Design Path]]
- [[Cloud Infrastructure Path]]
