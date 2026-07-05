# Transaction

Aliases: database transaction, giao dịch database

Type: Data / Database

## Context / Ngữ cảnh

Transaction xuất hiện khi nhiều thao tác đọc/ghi dữ liệu cần được xem như một đơn vị logic: hoặc cùng thành công, hoặc hệ thống không để lại trạng thái nửa vời. Nó thường dùng trong order/payment, inventory, account balance, booking, state transition, audit trail và workflow có invariant quan trọng.

## Boundary / Ranh giới

### Nó là gì

Transaction là boundary trong database hoặc hệ thống dữ liệu để gom các thao tác thành một đơn vị commit/rollback. Transaction tốt giúp bảo vệ invariant như “không trừ tiền nếu không tạo order”, “không bán quá tồn kho”, hoặc “audit log đi cùng thay đổi chính”.

### Nó không phải là gì

Transaction không tự giải quyết mọi race condition. Nếu isolation level yếu, check-then-act sai, lock thiếu hoặc transaction kéo dài quá lâu, dữ liệu vẫn có thể sai hoặc performance sập. Transaction cũng không tự mở rộng qua nhiều service; distributed transaction có boundary khác và cost cao hơn.

## Core Mechanism / Cơ chế lõi

Transaction bắt đầu, thực hiện nhiều statement, rồi commit nếu mọi thứ hợp lệ hoặc rollback khi lỗi. ACID mô tả kỳ vọng: atomicity, consistency, isolation, durability. Cơ chế thật dựa trên lock, MVCC, write-ahead log, isolation level, constraint và conflict handling của database engine.

## Project Role / Vai trò trong dự án

Transaction là node cần mở khi thiết kế service ghi dữ liệu quan trọng, debug data inconsistency, lost update, double-submit, lock wait, deadlock hoặc rollback không như mong đợi. Nó giúp team xác định transaction boundary, invariant nào cần bảo vệ và nơi nào cần constraint/lock/idempotency.

## Output / Artifact nên có

- Transaction boundary note: bắt đầu ở đâu, commit ở đâu, rollback path nào
- Invariant cần bảo vệ và constraint/lock đi kèm
- Isolation level decision cho transaction quan trọng
- Test concurrency cho double-submit, lost update, conflict và rollback
- Monitoring/debug note: lock wait, deadlock, transaction duration, retry count

## Decision Checklist / Câu hỏi kiểm tra

- Những thao tác nào phải cùng commit hoặc cùng rollback?
- Invariant nào cần giữ đúng sau transaction?
- Isolation level hiện tại có đủ cho race condition này không?
- Có cần row lock, unique constraint hoặc atomic update không?
- Transaction có gọi network/third-party chậm bên trong không?
- Transaction duration có quá dài gây lock wait hoặc connection pool saturation không?
- Khi conflict/deadlock xảy ra, app có retry an toàn không?

## Failure Modes / Cách nó gây lỗi

- Transaction boundary quá nhỏ làm dữ liệu chính commit nhưng audit/history không ghi.
- Transaction boundary quá lớn giữ lock lâu và gây timeout/pool saturation.
- Check-then-act dưới isolation yếu gây lost update hoặc oversell.
- Gọi third-party trong transaction làm lock bị giữ trong lúc chờ network.
- Rollback app code nhưng side effect ngoài database đã xảy ra.
- Không retry deadlock/serialization failure làm user gặp lỗi ngẫu nhiên dưới tải cao.

## Khi nào chưa cần hoặc dễ over-engineer

- Read-only query hoặc write đơn giản một statement có constraint đủ có thể không cần transaction phức tạp.
- Không nên giữ transaction mở qua UI step hoặc remote API call dài.
- Không nên dùng distributed transaction nếu có thể thiết kế idempotency, outbox hoặc eventual consistency rõ hơn.

## Gồm những gì

- [[Rollback]]

## Nối mạnh

- [[ACID]] vì transaction là nơi ACID có ý nghĩa thực tế.
- [[Isolation Level]] vì isolation quyết định transaction nhìn thấy thay đổi của nhau ra sao.
- [[Database Lock]] vì lock thường bảo vệ row/resource trong transaction.
- [[Database Migration]] vì migration có thể chạy trong hoặc ngoài transaction tùy database.
- [[Retry]] vì conflict/deadlock/serialization failure thường cần retry an toàn.

## Liên quan rộng

- Data correctness
- Concurrency control
- Backend workflow
- Database reliability

## Keywords / Từ khóa tìm kiếm

- Transaction
- database transaction
- giao dịch database
- commit
- rollback
- ACID
- transaction boundary
- lost update
- deadlock retry
- lock wait
- isolation level
- atomic update
- transaction duration
- transaction debugging

## Source trace

- Database System Concepts
- PostgreSQL transaction documentation
