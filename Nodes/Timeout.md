# Timeout

Aliases: request timeout, operation timeout, hết thời gian chờ

Type: Failure Pattern

## Context / Ngữ cảnh

Timeout xuất hiện khi request, query, job hoặc network call không được phép chờ vô hạn khi dependency chậm, treo hoặc hỏng. Nó thường nằm ở HTTP client/server, database query, message processing, API gateway, background job, tool call hoặc distributed system boundary.

## Boundary / Ranh giới

### Nó là gì

Timeout là giới hạn thời gian cho một operation. Khi vượt quá giới hạn, caller ngừng chờ và xử lý lỗi, cancel hoặc chuyển sang fallback. Timeout giúp hệ thống fail fast, giải phóng resource và tránh một dependency chậm kéo sập toàn bộ request chain.

### Nó không phải là gì

Timeout không tự sửa dependency chậm. Nó cũng không giống retry: timeout cắt thời gian chờ, retry quyết định có thử lại hay không. Timeout quá ngắn gây false failure; timeout quá dài làm thread/connection/request bị giữ lâu và che giấu sự cố.

## Core Mechanism / Cơ chế lõi

Timeout thường hoạt động như deadline hoặc timer gắn với operation. Khi timer hết, caller trả lỗi hoặc cancel context. Trong hệ thống phân tán, timeout phải phối hợp với retry, circuit breaker, queue, transaction và client/server timeout chain; nếu mỗi layer timeout không khớp, lỗi sẽ khó debug hoặc tạo retry storm.

## Project Role / Vai trò trong dự án

Timeout ảnh hưởng tới API design, reliability, user experience và resource protection. Khi debug production, timeout giúp phân biệt dependency chậm, pool cạn, network issue, query chậm hoặc downstream overload. Khi thiết kế service, team phải đặt timeout theo SLO, latency budget và side effect của operation.

## Output / Artifact nên có

- Timeout policy theo dependency: HTTP, database, cache, queue, external API, tool call
- Latency budget cho request chain quan trọng
- Config timeout ở client, server, gateway, load balancer và database driver
- Metric/log cho timeout count, dependency latency, cancellation và retry count
- Test case cho slow dependency, hung connection và partial failure

## Decision Checklist / Câu hỏi kiểm tra

- Timeout của client có ngắn hơn server/gateway timeout theo cách hợp lý không?
- Operation timeout có khớp SLO và latency budget không?
- Khi timeout xảy ra, request có được cancel thật hay downstream vẫn tiếp tục chạy?
- Timeout có kích hoạt retry không, và retry có idempotent không?
- Có log/trace để biết timeout xảy ra ở layer nào không?
- Timeout có đang giữ transaction/connection quá lâu không?
- Có fallback hoặc user-facing error rõ ràng cho timeout không?

## Failure Modes / Cách nó gây lỗi

- Không có timeout làm request treo, thread/connection bị giữ và hệ thống cạn resource.
- Timeout quá ngắn làm operation hợp lệ bị fail dưới latency bình thường.
- Timeout quá dài làm user chờ lâu và failure lan rộng trước khi hệ thống giải phóng resource.
- Client timeout nhưng server vẫn xử lý side effect, dẫn tới duplicate khi client retry.
- Timeout ở gateway ngắn hơn service làm client thấy 504 dù service cuối cùng vẫn commit dữ liệu.
- Không log timeout theo dependency khiến team debug nhầm giữa network, database và app logic.

## Khi nào chưa cần hoặc dễ over-engineer

- Script nhỏ chạy một lần có thể dùng timeout đơn giản thay vì policy phức tạp.
- Không nên thêm retry/circuit breaker/fallback phức tạp trước khi biết operation có idempotent và failure mode rõ.
- Với operation offline batch, timeout có thể dài hơn user-facing API, nhưng vẫn không nên vô hạn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Retry]] vì timeout thường quyết định khi nào retry xảy ra.
- [[Backpressure]] vì timeout giúp tránh giữ tài nguyên vô hạn khi downstream quá tải.
- [[API Gateway]] vì gateway timeout ảnh hưởng trực tiếp client-facing 504/502.
- [[Latency]] vì timeout phải dựa trên latency budget và phân phối p95/p99.
- [[Idempotency]] vì retry sau timeout chỉ an toàn khi operation idempotent hoặc có dedupe.

## Liên quan rộng

- Reliability engineering
- Distributed systems
- Incident debugging
- External API integration

## Keywords / Từ khóa tìm kiếm

- Timeout
- request timeout
- operation timeout
- hết thời gian chờ
- client timeout
- server timeout
- gateway timeout
- database timeout
- connection timeout
- read timeout
- deadline
- cancellation
- 504 gateway timeout
- slow dependency
- timeout retry

## Source trace

- Google SRE Book
- HTTP client documentation
