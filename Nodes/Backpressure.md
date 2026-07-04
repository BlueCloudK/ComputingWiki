# Backpressure

Aliases: flow control pressure, điều tiết ngược

Type: Performance / Scalability

## Context / Ngữ cảnh

Backpressure xuất hiện khi producer gửi work nhanh hơn consumer, queue, service hoặc downstream dependency có thể xử lý. Nếu không điều tiết, workload sẽ tích lũy thành queue backlog, memory pressure, timeout, retry storm hoặc outage dây chuyền.

## Boundary / Ranh giới

### Nó là gì

Backpressure là cơ chế làm upstream chậm lại, bị giới hạn, bị reject, bị drop có kiểm soát hoặc degrade khi downstream quá tải. Nó giúp hệ thống fail có kiểm soát thay vì nhận vô hạn request/job rồi chết vì cạn tài nguyên.

### Nó không phải là gì

Backpressure không chỉ là tăng queue size. Queue lớn hơn chỉ trì hoãn lỗi nếu service rate vẫn thấp hơn arrival rate. Backpressure cũng không thay thế capacity planning hoặc tối ưu bottleneck gốc; nó là guardrail để bảo vệ hệ thống khi tải vượt capacity.

## Core Mechanism / Cơ chế lõi

Hệ thống đo hoặc suy ra sức xử lý thật qua queue length, lag, latency, error rate, saturation hoặc token/buffer capacity. Khi vượt ngưỡng, nó có thể block producer, trả 429/503, giảm tốc consumer, drop low-priority work, shed load, dùng bounded queue, pull model, circuit breaker hoặc overload response.

## Project Role / Vai trò trong dự án

Backpressure là node cần mở khi queue backlog tăng, retry làm dependency tệ hơn, API bị flood, stream consumer chậm hoặc worker memory tăng. Nó giúp team quyết định bound ở đâu, tín hiệu overload trả cho ai, drop/retry thế nào và metric nào chứng minh hệ thống đang tự bảo vệ.

## Output / Artifact nên có

- Backpressure policy: threshold, action, priority, response code, retry guidance
- Bounded queue/buffer config và max in-flight work
- Metric: queue depth, consumer lag, reject/drop count, saturation, retry rate, latency p95/p99
- Load/soak test cho overload path
- Runbook cho downstream slow, queue full, producer spike và retry storm

## Decision Checklist / Câu hỏi kiểm tra

- Producer có thể tạo work nhanh hơn consumer không?
- Queue/buffer có bound rõ không, hay tăng vô hạn?
- Khi full/quá tải thì block, reject, drop hay degrade?
- Response trả upstream/client có `Retry-After` hoặc guidance không?
- Work nào ưu tiên giữ, work nào được drop/defer?
- Retry policy có jitter/backoff để không làm overload tệ hơn không?
- Metric nào báo backpressure đang kích hoạt và có false positive không?

## Failure Modes / Cách nó gây lỗi

- Queue unbounded làm memory tăng tới OOM.
- Không reject sớm nên request chờ lâu rồi timeout đồng loạt.
- Retry không backoff/jitter làm downstream đã chậm càng bị đánh mạnh.
- Drop data âm thầm không audit làm mất job/event quan trọng.
- Backpressure quá mạnh hoặc key sai làm user hợp lệ bị chặn nhiều.
- Chỉ backpressure ở app layer nhưng gateway/producer vẫn tiếp tục tạo tải không kiểm soát.

## Khi nào chưa cần hoặc dễ over-engineer

- Workload thấp, bounded tự nhiên và không có downstream đắt có thể dùng policy đơn giản.
- Không nên thêm flow-control phức tạp nếu chưa biết bottleneck và SLO.
- Không nên dùng backpressure để che bug như connection leak, slow query hoặc deadlock chưa sửa.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Queue Backlog]] vì backlog là tín hiệu cần backpressure.
- [[Rate Limiting]] vì rate limit là một cách điều tiết upstream request.
- [[Resource Exhaustion]] vì backpressure ngăn workload làm cạn tài nguyên.
- [[Retry]] vì retry policy phải phối hợp với backpressure để tránh khuếch đại tải.
- [[Thundering Herd]] vì herd effect cần jitter/backpressure để làm phẳng spike.

## Liên quan rộng

- Flow control
- Load shedding
- Overload handling
- Stream processing

## Keywords / Từ khóa tìm kiếm

- Backpressure
- flow control
- flow control pressure
- điều tiết ngược
- queue pressure
- producer consumer rate
- overload protection
- slow consumer
- bounded queue
- load shedding
- reject early
- Retry-After
- max in flight
- backpressure debugging
- chống quá tải pipeline

## Source trace

- Designing Data-Intensive Applications
- Google SRE Books
