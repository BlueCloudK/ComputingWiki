# Data and Database

Aliases: database systems, data systems, dữ liệu và database

Type: Data / Database

## Context / Ngữ cảnh

Data and Database xuất hiện khi hệ thống cần lưu, truy vấn, migrate, kiểm soát consistency hoặc hiểu dữ liệu qua thời gian. Nó thường nằm trong database schema, data model, query path hoặc integration payload.

## Boundary / Ranh giới

### Nó là gì

Data and Database là một phần của cách dữ liệu được biểu diễn, ràng buộc, truy cập hoặc giữ đúng trong hệ thống.

### Nó không phải là gì

Nó không chỉ là nơi cất data; nếu thiếu schema, constraint, transaction hoặc migration strategy thì code rất dễ phải vá dữ liệu sai.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi xoay quanh model/schema, relationship, constraint, transaction, index và migration. Những thứ này quyết định dữ liệu có nhất quán, truy vấn có nhanh và thay đổi có an toàn không.

## Project Role / Vai trò trong dự án

Data and Database là MOC điều hướng: dùng để đi từ vùng lớn xuống node cụ thể, không thay thế node chi tiết. Khi review graph, trang này giúp chọn đúng nhánh cần đọc và tránh link rộng làm rối.

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

- [[ERD]]
- [[Database Schema]]
- [[SQL]]
- [[Index]]
- [[Transaction]]
- [[Normalization]]
- [[Database Systems]]
- [[Data Intensive Systems]]
- [[Data Engineering]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database
- Backend
- Data migration
- Observability

## Keywords / Từ khóa tìm kiếm

- Data and Database
- data and database design
- data and database validation
- xử lý dữ liệu
- Data and Database MOC
- data and database map
- mục lục kiến thức
- nhánh kiến thức
- database systems
- data systems
- dữ liệu và database
- data model
- query design
- data consistency
- pipeline dữ liệu

## Source trace

- Database Systems Map
- Data Intensive Applications Map
