# MySQL

Aliases: MySQL, MySQL database

Type: Database / Tool

## Context / Ngữ cảnh

MySQL là relational database phổ biến cho web/backend application, thường dùng với InnoDB, SQL, indexing và replication.

## Boundary / Ranh giới

### Nó là gì

Nó là database engine quản lý table, index, transaction, lock, replication và query execution cho dữ liệu quan hệ.

### Nó không phải là gì

Nó không tự bảo đảm performance nếu schema, index, isolation hoặc connection pool bị thiết kế sai.

## Core Mechanism / Cơ chế lõi

MySQL nhận SQL, optimizer chọn execution plan, storage engine như InnoDB xử lý page, index, lock, transaction và redo/undo log.

## Project Role / Vai trò trong dự án

Node này giúp debug query chậm, deadlock, migration, isolation issue, replication delay và connection exhaustion trong backend.

## Output / Artifact nên có

- Schema và migration history
- Index plan cho query chính
- Backup/replication và restore procedure

## Decision Checklist / Câu hỏi kiểm tra

- Storage engine có phải InnoDB và hỗ trợ transaction cần thiết không?
- Query có dùng index hay full scan ngoài ý muốn?
- Isolation level có phù hợp với write conflict không?
- Replication lag có ảnh hưởng read-after-write không?

## Failure Modes / Cách nó gây lỗi

- Collation/charset lệch làm compare hoặc sort sai
- Gap lock/deadlock làm transaction fail bất ngờ
- Read replica lag trả dữ liệu cũ cho user

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần sharding/replication phức tạp khi một instance đáp ứng tải
- Dễ over-engineer nếu tối ưu query trước khi đo slow query log

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Database Index]] vì index quyết định phần lớn performance query
- [[Transaction]] vì InnoDB transaction là boundary data correctness quan trọng

## Liên quan rộng

- Relational database
- Web backend
- Replication

## Keywords / Từ khóa tìm kiếm

- MySQL
- MySQL database
- InnoDB
- SQL database
- replication lag
- slow query log
- gap lock
- database migration

## Source trace

- MySQL official documentation
