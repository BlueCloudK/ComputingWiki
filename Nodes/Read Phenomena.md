# Read Phenomena

Aliases: Read Phenomena, read anomalies

Type: Database Internals

## Context / Ngữ cảnh

Read Phenomena xuất hiện khi transaction đọc dữ liệu trong môi trường concurrent và kết quả đọc có thể thay đổi tùy isolation level, MVCC hoặc lock behavior.

## Boundary / Ranh giới

### Nó là gì

Read Phenomena là nhóm hiện tượng/anomaly khi transaction đọc thấy dữ liệu không ổn định hoặc không đúng kỳ vọng, như dirty read, non-repeatable read, phantom read hoặc lost update liên quan read-write.

### Nó không phải là gì

Read Phenomena không phải bug database mặc định. Nhiều hiện tượng là tradeoff có chủ ý của isolation level để đổi consistency lấy concurrency/performance.

## Core Mechanism / Cơ chế lõi

Khi nhiều transaction đọc/ghi cùng dữ liệu, engine dùng lock hoặc MVCC snapshot để quyết định transaction thấy version nào. Isolation level thấp hơn cho phép nhiều interleaving hơn và có thể lộ nhiều read phenomena hơn.

## Project Role / Vai trò trong dự án

Dùng node này khi chọn isolation level, debug dữ liệu đọc không nhất quán, thiết kế transaction cho booking/inventory/accounting hoặc test concurrent behavior.

## Output / Artifact nên có

- Transaction timeline
- Isolation level hiện tại
- Phenomenon observed
- Expected invariant
- Fix option: higher isolation, lock, atomic update, version check

## Decision Checklist / Câu hỏi kiểm tra

- Transaction cần invariant nào?
- Isolation level hiện tại cho phép hiện tượng gì?
- Timeline concurrent read/write ra sao?
- Có cần repeatable snapshot hoặc serializable không?
- Có thể dùng atomic update/constraint thay vì tăng isolation không?

## Failure Modes / Cách nó gây lỗi

- Chọn isolation mặc định mà không hiểu tradeoff.
- Test đơn luồng nên không thấy anomaly.
- Fix bằng lock quá rộng làm giảm concurrency.
- Tưởng read replica stale là isolation issue.
- Không ghi lại timeline nên debug chỉ dựa cảm giác.

## Khi nào chưa cần hoặc dễ over-engineer

- Read-only/reporting không cần invariant mạnh có thể dùng isolation mặc định.
- Không nên tăng toàn hệ thống lên isolation cao nếu chỉ một workflow cần bảo vệ.

## Gồm những gì

- [[Lost Update]]

## Nối mạnh

- [[Isolation Level]] vì isolation level quyết định hiện tượng nào có thể xảy ra.
- [[Transaction]] vì read phenomena xảy ra trong tương tác transaction.
- [[Lost Update]] vì lost update là anomaly quan trọng liên quan read-modify-write.
- [[Repeatable Read]] vì repeatable read ngăn một số hiện tượng đọc không ổn định.
- [[Read Committed]] vì read committed cho phép một số read phenomena phổ biến.

## Liên quan rộng

- Dirty read
- Non-repeatable read
- Phantom read
- MVCC snapshot

## Keywords / Từ khóa tìm kiếm

- Read Phenomena
- read anomalies
- dirty read
- non-repeatable read
- phantom read
- isolation level
- read phenomena debugging

## Source trace

- Database System Concepts
- PostgreSQL documentation
- Designing Data-Intensive Applications
