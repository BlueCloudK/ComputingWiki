# Lock Wait Time

Aliases: Lock Wait Time, lock wait duration

Type: Database Internals

## Context / Ngữ cảnh

Lock Wait Time xuất hiện khi transaction/query phải chờ lock do transaction khác đang giữ resource như row, table, index page hoặc metadata lock.

## Boundary / Ranh giới

### Nó là gì

Lock Wait Time là thời gian một session/query bị block trong khi chờ lock tương thích được cấp.

### Nó không phải là gì

Lock Wait Time không phải toàn bộ query latency. Query có thể chậm vì CPU, I/O, plan sai hoặc network; lock wait chỉ là phần thời gian chờ concurrency control.

## Core Mechanism / Cơ chế lõi

Transaction yêu cầu lock. Lock manager kiểm tra compatibility. Nếu resource đang bị lock bởi holder không tương thích, requester phải chờ tới khi holder commit, rollback hoặc release lock.

## Project Role / Vai trò trong dự án

Dùng node này khi debug query treo, migration bị block, lock contention, deadlock, idle transaction hoặc latency spike không giải thích được bằng query plan.

## Output / Artifact nên có

- Waiting session/query
- Lock holder session/query
- Locked resource
- Wait duration trend
- Mitigation: kill holder, shorten transaction, index, batch, retry

## Decision Checklist / Câu hỏi kiểm tra

- Session nào đang chờ lock?
- Session nào đang giữ lock?
- Resource bị lock là gì?
- Holder đang active hay idle in transaction?
- Có deadlock hoặc timeout policy không?

## Failure Modes / Cách nó gây lỗi

- Transaction idle giữ lock quá lâu.
- Migration lấy lock mạnh làm block production traffic.
- Update thiếu index khóa nhiều row hơn dự kiến.
- App timeout nhưng transaction vẫn còn mở.
- Chỉ tối ưu SQL mà bỏ qua lock holder thật.

## Khi nào chưa cần hoặc dễ over-engineer

- Workload ít writer và không có lock wait đáng kể thì chưa cần tối ưu sâu.
- Không nên thay isolation/lock hint nếu chưa có wait graph và holder query.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Database Lock]] vì lock wait đến từ lock compatibility.
- [[Exclusive Lock]] vì writer lock thường gây blocking.
- [[Shared Lock]] vì reader lock có thể chặn writer tùy engine/isolation.
- [[Deadlock]] vì lock wait cycle có thể thành deadlock.

## Liên quan rộng

- Blocking query
- Lock contention
- Idle transaction

## Keywords / Từ khóa tìm kiếm

- Lock Wait Time
- lock wait duration
- blocking query
- lock contention
- idle in transaction
- lock timeout
- lock wait debugging

## Source trace

- PostgreSQL documentation
- Database System Concepts
