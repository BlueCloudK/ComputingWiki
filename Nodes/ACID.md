# ACID

Aliases: atomicity consistency isolation durability, tính chất ACID

Type: Database Systems

## Context / Ngữ cảnh

ACID xuất hiện khi database transaction cần đảm bảo thay đổi dữ liệu đáng tin cậy dù có lỗi, rollback, crash hoặc nhiều transaction chạy đồng thời. Nó là nền để hiểu vì sao một thao tác ghi tiền, đơn hàng, inventory hoặc trạng thái nghiệp vụ phải được xử lý trong transaction đúng.

## Boundary / Ranh giới

### Nó là gì

ACID là bốn tính chất của transaction: Atomicity đảm bảo tất cả hoặc không gì được commit; Consistency giữ constraint/invariant hợp lệ; Isolation kiểm soát transaction đồng thời nhìn thấy nhau thế nào; Durability đảm bảo dữ liệu đã commit không mất sau crash theo guarantee của database.

### Nó không phải là gì

ACID không tự động làm mọi workflow phân tán an toàn. Nếu một nghiệp vụ ghi qua nhiều database/service/message broker, transaction local ACID không đủ để đảm bảo toàn hệ thống nhất quán. ACID cũng không thay thế thiết kế constraint, isolation level, idempotency hoặc compensation logic.

## Core Mechanism / Cơ chế lõi

Database thường dùng write-ahead log, lock/MVCC, constraint check và commit protocol để đạt ACID trong phạm vi transaction. Isolation level quyết định trade-off giữa correctness và concurrency. Atomic commit giúp rollback khi lỗi giữa chừng; durability phụ thuộc vào log/fsync/replication config và cách database xác nhận commit.

## Project Role / Vai trò trong dự án

ACID giúp team quyết định đoạn code nào phải nằm trong transaction, lỗi nào cần rollback, isolation level nào đủ, và invariant nào nên đẩy xuống database constraint. Khi debug lỗi dữ liệu, ACID là khung để hỏi: transaction có commit một phần không, có race condition không, constraint có bị bỏ qua không, commit đã durable chưa.

## Output / Artifact nên có

- Transaction boundary note cho use case quan trọng
- Invariant/constraint list: unique, foreign key, check constraint, balance/inventory rule
- Isolation level decision cho workload có concurrency cao
- Test case cho rollback, concurrent update, duplicate request và crash/retry path
- Monitoring/log cho deadlock, lock wait, serialization failure và transaction duration

## Decision Checklist / Câu hỏi kiểm tra

- Nghiệp vụ này có cần all-or-nothing trong một transaction không?
- Invariant nào được database constraint bảo vệ, invariant nào chỉ nằm ở app code?
- Isolation level hiện tại có tránh được race condition quan trọng không?
- Transaction có giữ lock quá lâu vì gọi API ngoài hoặc xử lý logic dài không?
- Retry sau transaction failure có idempotent không?
- Commit thành công có đồng nghĩa downstream message/event đã gửi chưa?
- Có test concurrent update hoặc double-submit không?

## Failure Modes / Cách nó gây lỗi

- Transaction boundary quá nhỏ làm một phần dữ liệu commit còn phần khác fail.
- Transaction boundary quá lớn giữ lock lâu, tăng contention và timeout.
- Isolation quá yếu gây lost update, non-repeatable read hoặc phantom read trong use case nhạy cảm.
- Tin ACID local nhưng workflow phân tán vẫn mất nhất quán giữa service/database.
- Không có constraint database nên app bug có thể ghi dữ liệu phá invariant.
- Retry transaction không idempotent tạo duplicate side effect.

## Khi nào chưa cần hoặc dễ over-engineer

- Read-only query hoặc log/analytics không quan trọng có thể không cần transaction mạnh.
- Không nên tăng isolation lên mức cao nhất nếu chưa có invariant cần bảo vệ và đã đo lock/contention.
- Với workflow phân tán, ép ACID toàn cục có thể phức tạp hơn event/compensation/outbox phù hợp.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Database Transaction]] vì ACID mô tả guarantee cốt lõi của transaction.
- [[Isolation Level]] vì isolation là phần ACID có nhiều trade-off nhất khi concurrency cao.
- [[Database Lock]] vì lock/MVCC là cơ chế để bảo vệ isolation và consistency.
- [[Rollback]] vì atomicity phụ thuộc vào khả năng rollback khi transaction fail.

## Liên quan rộng

- Data correctness
- Concurrency control
- Distributed transaction
- Backend reliability

## Keywords / Từ khóa tìm kiếm

- ACID
- atomicity consistency isolation durability
- tính chất ACID
- database transaction
- transaction atomicity
- transaction isolation
- transaction durability
- consistency constraint
- isolation level
- lost update
- serializable
- transaction rollback
- database correctness
- concurrent transaction

## Source trace

- Database System Concepts
- PostgreSQL transaction documentation
