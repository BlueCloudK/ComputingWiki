# Retry

Aliases: retry logic, thử lại request, retry operation

Type: Failure Pattern

## Context / Ngữ cảnh

Retry xuất hiện khi một operation thất bại tạm thời và caller có thể thử lại mà không làm sai dữ liệu. Nó thường dùng với network call, external API, database transient error, queue consumer, background job hoặc tool call tới dependency không ổn định.

## Boundary / Ranh giới

### Nó là gì

Retry là chính sách thử lại operation sau lỗi có khả năng tạm thời. Một retry policy tốt phải xác định lỗi nào được retry, retry tối đa bao nhiêu lần, backoff/jitter ra sao, có retry budget không và operation có idempotent hay không.

### Nó không phải là gì

Retry không phải cách sửa mọi lỗi. Lỗi validation, permission denied, bad request, bug logic hoặc dữ liệu sai thường không nên retry. Retry cũng không thay thế timeout, circuit breaker, backpressure hoặc thiết kế idempotency; nếu dùng sai, nó làm hệ thống quá tải nhanh hơn.

## Core Mechanism / Cơ chế lõi

Retry thường chạy theo vòng: operation fail, phân loại lỗi, chờ theo backoff, rồi thử lại nếu còn attempt/budget. Exponential backoff và jitter giúp tránh nhiều client retry cùng lúc. Với operation có side effect, retry cần idempotency key hoặc dedupe để tránh tạo đơn hàng/giao dịch/email nhiều lần.

## Project Role / Vai trò trong dự án

Retry ảnh hưởng trực tiếp tới reliability, latency, cost và data correctness. Khi thiết kế integration hoặc background job, team phải quyết định retry ở layer nào, timeout bao lâu, lỗi nào retry được, retry có làm duplicate side effect không và metric nào cho biết retry đang cứu hệ thống hay đang làm sự cố nặng hơn.

## Output / Artifact nên có

- Retry policy theo dependency: retryable error, max attempts, backoff, jitter, retry budget
- Idempotency/deduplication note cho operation có side effect
- Metric: retry count, retry success rate, final failure rate, latency sau retry
- Test case cho transient failure, permanent failure, timeout rồi retry và duplicate request
- Runbook khi retry storm hoặc dependency outage xảy ra

## Decision Checklist / Câu hỏi kiểm tra

- Lỗi nào được retry, lỗi nào phải fail ngay?
- Operation có idempotent không, hoặc có idempotency key/dedupe không?
- Timeout mỗi attempt và timeout tổng có rõ không?
- Retry có exponential backoff và jitter không?
- Retry nằm ở client, gateway, queue worker hay nhiều layer cùng lúc?
- Có retry budget để tránh retry vô hạn khi dependency outage không?
- Metric có phân biệt request thành công ngay và thành công sau retry không?

## Failure Modes / Cách nó gây lỗi

- Retry lỗi không retryable làm che bug thật và tăng tải vô ích.
- Retry không jitter làm nhiều client cùng thử lại, tạo thundering herd.
- Retry nhiều layer cùng lúc làm số request nhân lên rất nhanh.
- Retry operation không idempotent gây duplicate payment, duplicate order hoặc gửi email nhiều lần.
- Retry sau timeout nhưng server cũ vẫn commit side effect làm client tưởng fail nhưng dữ liệu đã đổi.
- Không có retry budget khiến dependency outage biến thành retry storm.

## Khi nào chưa cần hoặc dễ over-engineer

- Operation local, nhanh và deterministic thường không cần retry phức tạp.
- Không nên thêm retry trước khi có timeout rõ ràng.
- Không nên retry operation ghi dữ liệu nếu chưa có idempotency hoặc recovery path.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Timeout]] vì timeout thường là tín hiệu kích hoạt retry.
- [[Idempotency]] vì retry side effect chỉ an toàn khi operation idempotent hoặc có dedupe.
- [[Backpressure]] vì retry sai có thể phá backpressure và làm overload nặng hơn.
- [[Thundering Herd]] vì retry đồng loạt có thể tạo herd effect.

## Liên quan rộng

- Reliability engineering
- External API integration
- Queue processing
- Incident response

## Keywords / Từ khóa tìm kiếm

- Retry
- retry logic
- thử lại request
- retry operation
- retry policy
- retryable error
- non retryable error
- exponential backoff
- jitter
- retry budget
- retry storm
- duplicate side effect
- idempotency key
- transient failure
- retry debugging

## Source trace

- Google SRE Book
- AWS Builders Library
