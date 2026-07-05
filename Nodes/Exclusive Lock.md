# Exclusive Lock

Aliases: Exclusive Lock, write lock

Type: Database Internals

## Context / Ngữ cảnh

Exclusive Lock xuất hiện khi database cần ngăn transaction khác đọc/ghi xung đột trong lúc một transaction đang thay đổi row, page, table hoặc resource.

## Boundary / Ranh giới

### Nó là gì

Exclusive Lock là lock mode cho phép holder có quyền ghi độc quyền trên resource và thường chặn các lock không tương thích từ transaction khác.

### Nó không phải là gì

Exclusive Lock không phải isolation level. Isolation level quy định hành vi transaction tổng thể; lock là một cơ chế engine dùng để enforce concurrency control.

## Core Mechanism / Cơ chế lõi

Transaction yêu cầu exclusive lock trước khi update/delete hoặc thay đổi resource. Lock manager kiểm tra compatibility, cấp lock nếu được, hoặc bắt transaction chờ cho tới khi lock holder commit/rollback/release.

## Project Role / Vai trò trong dự án

Dùng node này khi debug lock wait, deadlock, transaction lâu, migration bị block, update chậm hoặc concurrency issue trong database.

## Output / Artifact nên có

- Lock wait graph/session list
- Resource bị lock
- Transaction holder/waiter
- Query đang giữ lock
- Mitigation: shorten transaction, index, batch, retry

## Decision Checklist / Câu hỏi kiểm tra

- Transaction nào đang giữ exclusive lock?
- Resource bị lock là row, table hay index/page?
- Lock giữ trong bao lâu?
- Query nào đang chờ?
- Có thể giảm phạm vi hoặc thời gian transaction không?

## Failure Modes / Cách nó gây lỗi

- Transaction mở quá lâu giữ lock làm nghẽn hệ thống.
- Migration lấy exclusive lock trên table lớn gây downtime.
- Update thiếu index làm lock nhiều row hơn dự kiến.
- Deadlock khi nhiều transaction giữ/chờ lock chéo nhau.
- App timeout nhưng transaction chưa rollback đúng lúc.

## Khi nào chưa cần hoặc dễ over-engineer

- Workload nhỏ ít concurrency có thể chưa cần tối ưu lock sâu.
- Không nên chỉnh isolation/lock hint nếu chưa có lock wait metric và query plan.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Database Lock]] vì exclusive lock là một lock mode quan trọng.
- [[Shared Lock]] vì shared/exclusive compatibility quyết định reader/writer blocking.
- [[Transaction]] vì lock lifetime thường gắn với transaction.
- [[Deadlock]] vì exclusive lock thường tham gia deadlock.

## Liên quan rộng

- Write lock
- Lock wait
- Concurrency control

## Keywords / Từ khóa tìm kiếm

- Exclusive Lock
- write lock
- lock wait
- blocking transaction
- deadlock
- database lock
- exclusive lock debugging

## Source trace

- Database System Concepts
- PostgreSQL documentation
