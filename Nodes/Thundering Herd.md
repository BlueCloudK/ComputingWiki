# Thundering Herd

Aliases: herd effect, stampede request

Type: Failure Pattern

## Context / Ngữ cảnh

Thundering Herd xuất hiện khi nhiều client, worker, thread hoặc service cùng thức dậy/gọi lại/cạnh tranh cùng một resource gần như đồng thời, tạo spike tải đột ngột. Nó thường gặp khi cache hết hạn cùng lúc, retry đồng bộ, lock release đánh thức nhiều worker, cron chạy cùng giờ hoặc service restart hàng loạt.

## Boundary / Ranh giới

### Nó là gì

Thundering Herd là failure pattern trong đó nhiều actor cùng hành động tại một thời điểm và làm resource bị quá tải. Vấn đề chính không chỉ là traffic cao, mà là traffic/cạnh tranh được đồng bộ hóa thay vì phân tán theo thời gian.

### Nó không phải là gì

Thundering Herd không phải mọi traffic spike. Nếu traffic tăng đều theo nhu cầu thật, đó là capacity/scaling problem. Herd effect thường có nguyên nhân đồng bộ như cùng TTL, cùng retry schedule, cùng lock wakeup, cùng deploy/restart hoặc cùng timer.

## Core Mechanism / Cơ chế lõi

Nhiều actor chờ cùng điều kiện hoặc dùng cùng lịch. Khi điều kiện mở ra, tất cả chạy cùng lúc: cùng gọi database, cùng rebuild cache, cùng retry dependency, cùng acquire lock hoặc cùng accept connection. Không có jitter, backoff, request coalescing, rate limit hoặc backpressure thì spike vượt capacity và kéo theo timeout/retry tiếp.

## Project Role / Vai trò trong dự án

Thundering Herd là node cần mở khi hệ thống có spike theo chu kỳ, sau cache expiry, sau deploy, sau dependency recover hoặc sau lock release. Nó giúp team kiểm tra TTL jitter, retry jitter, cron staggering, singleflight, distributed lock, rate limit và warmup strategy.

## Output / Artifact nên có

- Herd source analysis: cache TTL, retry schedule, cron, lock, deploy/restart, connection wakeup
- Mitigation policy: jitter, exponential backoff, request coalescing, rate limit, backpressure
- Metric: synchronized spike timing, retry count, cache miss burst, lock contention, upstream QPS
- Load test mô phỏng nhiều client/worker cùng thức dậy
- Runbook cho dependency recovery hoặc cache flush tránh spike đồng loạt

## Decision Checklist / Câu hỏi kiểm tra

- Có nhiều client/worker dùng cùng TTL, timer hoặc retry interval không?
- Retry có exponential backoff và jitter không?
- Cache key hot có request coalescing/singleflight không?
- Cron/job có chạy đồng loạt ở cùng phút/giờ không?
- Khi lock release, có đánh thức quá nhiều worker cùng tranh lock không?
- Dependency vừa recover có bị tất cả client retry cùng lúc không?
- Có rate limit/backpressure để cắt spike trước khi dependency sập không?

## Failure Modes / Cách nó gây lỗi

- Cache hết hạn cùng lúc làm tất cả request cùng rebuild và đánh database.
- Retry không jitter làm client cùng gọi lại dependency đúng một thời điểm.
- Cron fleet chạy cùng giờ làm database/API bị spike tải.
- Lock release hoặc event broadcast đánh thức quá nhiều worker cùng tranh resource.
- Service restart sau deploy làm tất cả instance warm cache/connect DB cùng lúc.
- Herd gây timeout, timeout lại kích retry, tạo vòng khuếch đại tải.

## Khi nào chưa cần hoặc dễ over-engineer

- Hệ thống ít client/worker hoặc traffic thấp có thể chỉ cần retry/backoff cơ bản.
- Không nên thêm distributed coordination phức tạp nếu jitter/stagger đơn giản đã đủ.
- Không nên xem mọi spike là herd nếu không có bằng chứng actor bị đồng bộ hóa.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Retry]] vì retry không jitter là nguồn thundering herd phổ biến.
- [[Cache Stampede]] vì cache stampede là một dạng herd quanh hot key/cache miss.
- [[Backpressure]] vì cần chặn herd trước khi dependency quá tải.
- [[Rate Limiting]] vì rate limit giúp làm phẳng spike đồng loạt.
- [[Timeout]] vì timeout/retry có thể khuếch đại herd effect.

## Liên quan rộng

- Reliability engineering
- Traffic shaping
- Cache design
- Distributed systems

## Keywords / Từ khóa tìm kiếm

- Thundering Herd
- herd effect
- stampede request
- wakeup storm
- retry storm
- jitter
- exponential backoff
- synchronized retry
- cache expiry alignment
- lock contention
- cron staggering
- request coalescing
- singleflight
- traffic spike
- thundering herd debugging

## Source trace

- Linux accept documentation
- Caching pattern references
- Google SRE Book
