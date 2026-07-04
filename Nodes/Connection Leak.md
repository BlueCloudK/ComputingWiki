# Connection Leak

Aliases: leak connection, rò rỉ kết nối

Type: Failure Pattern

## Context / Ngữ cảnh

Connection Leak xuất hiện khi database, HTTP, socket hoặc network connection được mở/checkout nhưng không được close hoặc trả về pool đúng lúc. Trong backend production, leak thường làm pool cạn dần, latency tăng và cuối cùng request fail vì không lấy được connection mới.

## Boundary / Ranh giới

### Nó là gì

Connection Leak là failure pattern trong đó connection vẫn bị giữ sau khi operation đã xong hoặc đã lỗi. Với connection pool, leak nghĩa là connection được checkout nhưng không return về pool. Với raw connection/socket/file handle, leak nghĩa là resource không được close/release đúng lifecycle.

### Nó không phải là gì

Connection Leak không phải mọi tình huống nhiều connection. Traffic cao hợp lệ có thể làm active connection tăng nhưng sẽ giảm khi workload giảm. Leak có dấu hiệu active connection tăng hoặc không hồi phục dù request đã kết thúc, thường do thiếu `finally`, `using`, context manager, close/dispose hoặc cancellation cleanup.

## Core Mechanism / Cơ chế lõi

Code lấy connection từ pool, chạy query/call, rồi phải release connection trong mọi path: success, error, timeout, cancellation. Nếu exception hoặc branch return sớm bỏ qua cleanup, connection bị giữ. Leak nhỏ dưới traffic đều sẽ tích lũy tới khi pool/max connection bị cạn.

## Project Role / Vai trò trong dự án

Connection Leak là node cần mở khi pool active tăng dần, checkout timeout xuất hiện, service phải restart mới hết lỗi, hoặc database thấy connection idle lâu bất thường. Nó giúp team kiểm tra lifecycle cleanup, transaction boundary, driver behavior, pool leak detection và path lỗi hiếm.

## Output / Artifact nên có

- Leak detection config: threshold, stack trace, pool warning log
- Metric: active/idle/pending connections, checkout time, connection age, timeout count
- Code checklist cho cleanup: finally/using/context manager/dispose/close
- Test case cho exception path, timeout/cancellation và early return
- Runbook phân biệt leak, long query, transaction giữ connection lâu và traffic spike

## Decision Checklist / Câu hỏi kiểm tra

- Connection có được release trong mọi path success/error/timeout không?
- Có transaction/session nào không commit/rollback/close không?
- Active connections có giảm sau khi workload dừng không?
- Pool có bật leak detection hoặc log stack checkout lâu không?
- Có code path return sớm trước cleanup không?
- HTTP/socket/file connection có timeout và close đúng không?
- Framework/ORM có lifecycle riêng cần dùng đúng context/session scope không?

## Failure Modes / Cách nó gây lỗi

- Missing `finally`/`using` làm connection không được trả về pool sau exception.
- Transaction không commit/rollback khiến connection bị giữ và lock có thể còn tồn tại.
- Stream/result set chưa consume/close làm driver giữ connection.
- Cancellation/timeout không cleanup resource làm connection treo.
- Leak chỉ xảy ra ở edge case nên test happy path không phát hiện.
- Restart service tạm thời giải phóng connection nhưng lỗi quay lại khi traffic chạy tiếp.

## Khi nào chưa cần hoặc dễ over-engineer

- App dùng framework/ORM quản lý session đúng chuẩn có thể chưa cần custom cleanup layer.
- Không nên tăng pool size để che leak; nó chỉ kéo dài thời gian trước khi pool cạn.
- Không nên kết luận leak nếu active connection tăng theo traffic và giảm về baseline sau đó.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Connection Pooling]] vì leak thường làm connection không trở về pool.
- [[Connection Pool Saturation]] vì leak là nguyên nhân phổ biến gây pool cạn.
- [[Timeout]] vì checkout timeout thường là triệu chứng user thấy khi leak đã tích lũy.
- [[Database Transaction]] vì transaction không đóng đúng có thể giữ connection và lock.

## Liên quan rộng

- Resource management
- Backend reliability
- Database operations
- Runtime debugging

## Keywords / Từ khóa tìm kiếm

- Connection Leak
- leak connection
- rò rỉ kết nối
- database connection leak
- connection pool leak
- connection not closed
- connection not returned
- leak detection
- HikariCP leak detection
- checkout timeout
- active connection leak
- idle connection stuck
- resource cleanup
- finally block
- using statement

## Source trace

- HikariCP documentation
- PostgreSQL connection documentation
