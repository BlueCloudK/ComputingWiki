# Shared Lock

Aliases: Shared Lock, read lock

Type: Database Internals

## Context / Ngữ cảnh

Shared Lock xuất hiện khi database cần cho phép nhiều transaction đọc cùng một resource nhưng vẫn kiểm soát xung đột với writer.

## Boundary / Ranh giới

### Nó là gì

Shared Lock là lock mode thường dùng cho đọc, cho phép nhiều holder cùng giữ lock nếu chúng tương thích, nhưng thường chặn exclusive lock trên cùng resource.

### Nó không phải là gì

Shared Lock không phải snapshot isolation. Snapshot isolation có thể cho đọc không block writer theo MVCC; shared lock là cơ chế lock-based concurrency cụ thể.

## Core Mechanism / Cơ chế lõi

Transaction yêu cầu shared lock khi cần đọc ổn định hoặc enforce consistency. Lock manager cấp shared lock nếu không có lock không tương thích; writer cần exclusive lock phải chờ shared lock được release.

## Project Role / Vai trò trong dự án

Dùng node này khi debug reader/writer blocking, lock wait, isolation behavior, migration bị block hoặc query đọc lâu làm writer chậm.

## Output / Artifact nên có

- Lock compatibility table
- Holder/waiter session list
- Resource bị lock
- Query đang giữ lock
- Isolation level/context

## Decision Checklist / Câu hỏi kiểm tra

- Shared lock đang giữ trên resource nào?
- Writer nào đang chờ exclusive lock?
- Lock được giữ tới statement end hay transaction end?
- Isolation level có cần shared lock không?
- Query đọc có thể ngắn hơn hoặc dùng snapshot không?

## Failure Modes / Cách nó gây lỗi

- Query đọc lâu làm writer bị block.
- Transaction mở nhưng idle vẫn giữ lock.
- Hiểu nhầm MVCC nên không biết lock nào đang chặn.
- Shared/exclusive compatibility bị bỏ qua khi debug deadlock.
- Migration cần exclusive lock nhưng bị reader giữ quá lâu.

## Khi nào chưa cần hoặc dễ over-engineer

- Workload ít concurrency có thể chưa cần tối ưu lock sâu.
- Không nên thay isolation hoặc lock mode nếu chưa có lock wait graph.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Database Lock]] vì shared lock là lock mode cơ bản.
- [[Exclusive Lock]] vì compatibility giữa shared/exclusive quyết định blocking.
- [[Transaction]] vì lock lifetime thường gắn với transaction.
- [[Isolation Level]] vì isolation ảnh hưởng lock/MVCC behavior.

## Liên quan rộng

- Read lock
- Lock compatibility
- Reader writer blocking

## Keywords / Từ khóa tìm kiếm

- Shared Lock
- read lock
- lock compatibility
- reader writer lock
- lock wait
- isolation level
- shared lock debugging

## Source trace

- Database System Concepts
- PostgreSQL documentation
