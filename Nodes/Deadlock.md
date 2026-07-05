# Deadlock

Aliases: deadlock, bế tắc

Type: Tooling / Implementation Detail

## Context / Ngữ cảnh

Deadlock xuất hiện khi hai hoặc nhiều process/thread/transaction cùng chờ tài nguyên của nhau và không bên nào có thể tiếp tục. Nó thường gặp trong database transaction, mutex/lock trong code, distributed lock, thread pool hoặc hệ thống có nhiều resource bị acquire theo thứ tự không nhất quán.

## Boundary / Ranh giới

### Nó là gì

Deadlock là trạng thái chờ vòng tròn: A giữ resource 1 và chờ resource 2, B giữ resource 2 và chờ resource 1. Trong database, deadlock thường xảy ra khi hai transaction lock row/table theo thứ tự ngược nhau. Trong code, deadlock thường liên quan mutex, monitor, channel, future hoặc blocking call.

### Nó không phải là gì

Deadlock không phải mọi tình huống app chậm hoặc treo. Thread starvation, infinite loop, slow query, lock contention và queue backlog có triệu chứng giống treo nhưng cơ chế khác. Deadlock cần có vòng chờ tài nguyên hoặc dependency khiến các bên không thể tự tiến lên.

## Core Mechanism / Cơ chế lõi

Deadlock hình thành khi có đủ điều kiện: mutual exclusion, hold-and-wait, no preemption và circular wait. Hệ thống có thể phòng tránh bằng lock ordering, timeout, try-lock, transaction nhỏ hơn hoặc detection rồi abort một bên. Database thường phát hiện deadlock và rollback một transaction để phá vòng chờ.

## Project Role / Vai trò trong dự án

Deadlock là node cần mở khi production có transaction aborted, request treo, thread dump cho thấy lock wait, database báo deadlock detected hoặc worker dừng xử lý. Nó giúp team tìm resource nào bị lock, thứ tự acquire ra sao và retry/timeout nào cần có.

## Output / Artifact nên có

- Deadlock trace: transaction/thread nào giữ lock nào và chờ lock nào
- Lock acquisition order convention nếu code có nhiều lock/resource
- Transaction/query log hoặc thread dump lúc lỗi
- Retry policy cho deadlock/serialization failure nếu operation idempotent
- Test concurrency hoặc reproduction scenario cho hai actor chạy song song

## Decision Checklist / Câu hỏi kiểm tra

- Có vòng chờ resource thật không, hay chỉ là slow/blocking operation?
- Các transaction/thread acquire lock theo thứ tự nào?
- Transaction có giữ lock trong lúc gọi network/API/file I/O không?
- Database/app có timeout và retry an toàn không?
- Có thể enforce lock ordering hoặc giảm phạm vi transaction/critical section không?
- Thread dump/deadlock log có đủ để thấy owner/waiter không?
- Retry có idempotent không hay gây duplicate side effect?

## Failure Modes / Cách nó gây lỗi

- Hai transaction update row theo thứ tự ngược nhau và database rollback một transaction.
- Code giữ mutex rồi gọi function khác cũng cố lấy mutex đó.
- Transaction giữ database lock trong lúc chờ remote API, làm deadlock/lock wait tăng.
- App không retry deadlock nên user gặp lỗi ngẫu nhiên dưới concurrency cao.
- Retry thiếu idempotency làm deadlock recovery tạo duplicate operation.
- Thread dump/log không đủ context nên team nhầm deadlock với performance issue khác.

## Khi nào chưa cần hoặc dễ over-engineer

- Single-threaded flow hoặc CRUD đơn giản ít lock có thể chưa cần deadlock analysis sâu.
- Không nên thêm lock phức tạp nếu có thể dùng atomic database operation hoặc unique constraint.
- Không nên xử lý deadlock bằng cách tăng timeout mù; cần hiểu vòng chờ và lock order.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Mutex]] vì deadlock trong code thường xuất hiện quanh mutex/lock.
- [[Scheduling]] vì thread scheduling có thể làm deadlock/lock wait lộ ra dưới concurrency.
- [[Database Lock]] vì database deadlock là dạng deadlock phổ biến trong backend.
- [[Transaction]] vì deadlock thường xảy ra giữa nhiều transaction giữ lock.
- [[Retry]] vì deadlock victim thường cần retry an toàn.

## Liên quan rộng

- Concurrency control
- Runtime debugging
- Database reliability
- Thread dump analysis

## Keywords / Từ khóa tìm kiếm

- Deadlock
- deadlock
- bế tắc
- circular wait
- lock ordering
- deadlock detected
- database deadlock
- mutex deadlock
- thread dump deadlock
- lock wait
- transaction deadlock
- retry deadlock
- concurrency bug
- deadlock debugging

## Source trace

- Operating Systems concepts
- PostgreSQL explicit locking documentation
