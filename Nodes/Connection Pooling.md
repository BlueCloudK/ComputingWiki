# Connection Pooling

Aliases: database connection pool, pool kết nối, connection pool

Type: Backend / Database

## Context / Ngữ cảnh

Connection Pooling xuất hiện khi application cần nói chuyện với database hoặc service ngoài nhiều lần mà không muốn mở connection mới cho mỗi request. Trong backend production, connection pool là lớp kiểm soát concurrency giữa app và database, ảnh hưởng trực tiếp tới latency, throughput và khả năng chịu tải.

## Boundary / Ranh giới

### Nó là gì

Connection Pooling là cơ chế giữ sẵn một số connection để tái sử dụng. App checkout connection từ pool, dùng để query/transaction, rồi trả lại pool. Pool thường có cấu hình như max pool size, min idle, checkout timeout, idle timeout, max lifetime và leak detection.

### Nó không phải là gì

Connection Pooling không làm database nhanh vô hạn. Tăng pool size không đồng nghĩa tăng throughput nếu database đã bão hòa CPU/IO/lock. Nó cũng không thay thế query optimization, index, transaction design hoặc caching; pool chỉ điều tiết số connection đang được dùng.

## Core Mechanism / Cơ chế lõi

Pool giới hạn số connection đồng thời và hàng đợi request chờ connection rảnh. Nếu pool quá nhỏ, request bị chờ hoặc timeout dù database còn khỏe. Nếu pool quá lớn, database bị quá tải, context switching tăng, lock contention nặng hơn. Nếu code không trả connection về pool, pool bị leak và cuối cùng mọi request chờ connection.

## Project Role / Vai trò trong dự án

Connection Pooling là node cần mở khi debug backend chậm, request timeout, database connection spike, thread bị block hoặc lỗi “too many connections”. Nó giúp team quyết định pool size, timeout, transaction scope, monitoring metric và cách tách nguyên nhân giữa app bottleneck và database bottleneck.

## Output / Artifact nên có

- Pool configuration: max pool size, min idle, checkout timeout, idle timeout, max lifetime
- Metric dashboard: active connections, idle connections, pending waiters, checkout time, timeout count
- Load test note cho pool size tương ứng với app instance count và database limit
- Leak detection setting hoặc test cho path không đóng/return connection
- Runbook cho lỗi pool exhausted, too many connections và database saturation

## Decision Checklist / Câu hỏi kiểm tra

- Tổng connection tối đa = pool size x số app instances có vượt database max connections không?
- Checkout timeout có ngắn hơn request timeout tổng không?
- Transaction có giữ connection quá lâu vì gọi API ngoài hoặc xử lý business logic trong transaction không?
- Có metric active/idle/pending/checkout time để phân biệt pool thiếu hay query chậm không?
- Có connection leak detection không?
- Pool size được kiểm chứng bằng load test hay chỉ đoán?
- Khi scale horizontally, pool config có tự nhân lên làm database quá tải không?

## Failure Modes / Cách nó gây lỗi

- Pool quá nhỏ làm request xếp hàng chờ connection và timeout dù database chưa quá tải.
- Pool quá lớn làm database vượt max connection hoặc giảm performance vì quá nhiều session đồng thời.
- Connection leak khiến active connection tăng dần rồi app treo ở checkout.
- Transaction giữ connection lâu làm pool cạn dưới tải cao.
- Health check hoặc background job dùng chung pool với request chính làm user traffic bị nghẽn.
- Retry khi pool đang cạn tạo thêm áp lực và làm timeout lan rộng.

## Khi nào chưa cần hoặc dễ over-engineer

- Script nhỏ hoặc job chạy một lần có thể mở/đóng connection đơn giản nếu không có concurrency cao.
- App nhỏ một instance có thể dùng default pool config ban đầu, nhưng vẫn cần biết database max connections.
- Không nên tuning pool liên tục khi nguyên nhân thật là query thiếu index, lock contention hoặc external call trong transaction.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Connection Pool Saturation]] vì pool bị cạn là failure mode trực tiếp của connection pooling.
- [[Database Transaction]] vì transaction giữ connection càng lâu thì pool càng dễ cạn.
- [[Timeout]] vì checkout timeout và request timeout quyết định user thấy lỗi nhanh hay bị treo.
- [[Load Test]] vì pool size cần được kiểm chứng dưới concurrency thật.

## Liên quan rộng

- Database reliability
- Backend performance
- Capacity planning
- Query optimization

## Keywords / Từ khóa tìm kiếm

- Connection Pooling
- database connection pool
- connection pool
- pool kết nối
- max pool size
- checkout timeout
- active connections
- idle connections
- connection leak
- too many connections
- pool exhausted
- HikariCP
- database concurrency
- connection wait time

## Source trace

- HikariCP documentation
- PostgreSQL connection documentation
