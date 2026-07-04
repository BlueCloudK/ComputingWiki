# Connection Pool Saturation

Aliases: Connection Pool Saturation, connection pool saturation, Connection Pool Exhaustion, pool exhaustion

Type: Database Internals

## Context / Ngữ cảnh

Connection Pool Saturation xuất hiện khi số request cần database connection vượt quá khả năng cấp connection của pool. Nó thường lộ ra dưới dạng request chậm, checkout timeout, thread bị chờ, API 5xx hoặc database/app nhìn có vẻ “treo” dù process vẫn chạy.

## Boundary / Ranh giới

### Nó là gì

Connection Pool Saturation là trạng thái pool không còn connection rảnh để cấp cho workload hiện tại. Request mới phải chờ trong queue, timeout khi checkout hoặc fail. Nguyên nhân có thể là pool quá nhỏ, query/transaction chậm, connection leak, database lock, traffic spike hoặc số app instances nhân tổng connection quá cao.

### Nó không phải là gì

Connection Pool Saturation không phải lúc nào cũng do pool size nhỏ. Tăng pool size có thể làm database quá tải hơn nếu nguyên nhân thật là query chậm, lock contention, transaction giữ connection lâu hoặc leak. Nó cũng khác với database max connections exhaustion, dù hai lỗi này có thể kéo nhau.

## Core Mechanism / Cơ chế lõi

App checkout connection từ pool trước khi query/transaction. Khi active connections chạm max pool size, request mới chờ. Nếu thời gian chờ vượt checkout timeout, app fail dù database có thể vẫn còn sống. Saturation thường là triệu chứng của throughput mismatch giữa incoming request, thời gian giữ connection và pool/database capacity.

## Project Role / Vai trò trong dự án

Connection Pool Saturation là node cần mở khi backend latency tăng đột biến, log có timeout khi lấy connection, pool active luôn bằng max hoặc database request xếp hàng. Nó giúp team debug theo chuỗi: traffic → pool active/pending → query time → transaction duration → lock/leak → database max connections.

## Output / Artifact nên có

- Pool dashboard: active, idle, pending/waiting, checkout time, timeout count
- Capacity note: pool size x app instances so với database max connections
- Trace/log cho transaction/query giữ connection lâu
- Load test hoặc soak test để phát hiện saturation dưới concurrency thật
- Runbook phân biệt pool saturation, connection leak, slow query và database overload

## Decision Checklist / Câu hỏi kiểm tra

- Active connections có thường xuyên chạm max pool size không?
- Pending/waiting requests và checkout time có tăng cùng latency không?
- Query hoặc transaction nào giữ connection lâu nhất?
- Có connection leak làm active không giảm sau khi workload giảm không?
- Tổng pool size của mọi app instance có vượt database max connections không?
- Checkout timeout có phù hợp với request timeout không?
- Tăng pool size có giúp throughput thật hay chỉ đẩy tải sang database?

## Failure Modes / Cách nó gây lỗi

- Pool cạn làm request chờ connection rồi timeout hàng loạt.
- Transaction dài giữ connection trong lúc gọi API ngoài hoặc xử lý logic nặng.
- Connection leak làm active connection tăng dần tới max và không hồi phục.
- Traffic spike khiến pool queue tăng, retry tiếp tục nhân tải và làm sự cố nặng hơn.
- Scale app instance nhưng giữ nguyên pool size mỗi instance làm tổng connection vượt database limit.
- Tuning pool size mà không sửa slow query/lock khiến database latency tăng thêm.

## Khi nào chưa cần hoặc dễ over-engineer

- App ít traffic có thể dùng default pool config nhưng vẫn cần biết database max connections.
- Không nên thêm queue/circuit breaker phức tạp trước khi có metric pool cơ bản.
- Không nên xử lý bằng cách tăng pool size mù nếu chưa đo query time, lock wait và transaction duration.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Connection Pooling]] vì saturation là failure mode trực tiếp của pool.
- [[Connection Leak]] vì leak có thể làm pool cạn dần.
- [[Timeout]] vì checkout timeout là tín hiệu user/app thường thấy.
- [[Database Lock]] vì lock làm transaction giữ connection lâu và gây saturation.
- [[Backpressure]] vì cần giới hạn tải khi pool đã bão hòa.

## Liên quan rộng

- Database Systems
- Data Intensive Systems
- Performance
- Debugging and Failure Patterns

## Keywords / Từ khóa tìm kiếm

- Connection Pool Saturation
- connection pool saturation
- Connection Pool Exhaustion
- pool exhaustion
- connection pool exhausted
- checkout timeout
- active connections
- idle connections
- pending connections
- pool wait time
- database connection pool
- HikariCP pool exhausted
- too many connections
- connection pool debugging

## Source trace

- HikariCP documentation
- PostgreSQL connection documentation
- Designing Data-Intensive Applications
