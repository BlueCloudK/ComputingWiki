# Thread Starvation

Aliases: thread pool starvation, thiếu thread xử lý

Type: Failure Pattern

## Context / Ngữ cảnh

Thread Starvation xuất hiện khi worker/thread pool không còn thread rảnh để xử lý request/job mới đúng hạn. Nó thường gặp trong web server, background worker, executor pool, Java/.NET backend, blocking I/O trong async runtime hoặc task queue dùng worker pool cố định.

## Boundary / Ranh giới

### Nó là gì

Thread Starvation là failure pattern trong đó thread bị block, giữ quá lâu hoặc pool size quá thấp so với workload, làm task mới phải chờ trong queue dù CPU có thể chưa full. Triệu chứng thường là request latency tăng, queue wait cao, timeout, health check fail hoặc app có vẻ “đơ” nhưng không crash.

### Nó không phải là gì

Thread Starvation không phải mọi CPU bottleneck. CPU 100% do computation nặng là CPU saturation; thread starvation có thể xảy ra cả khi CPU thấp vì thread đang chờ I/O, lock, database connection, remote API hoặc sleep/blocking call. Nó cũng khác deadlock, dù deadlock có thể làm thread bị giữ mãi.

## Core Mechanism / Cơ chế lõi

Request/job lấy thread từ pool. Nếu thread gọi blocking I/O, chờ lock, chờ connection, sync-over-async hoặc xử lý lâu, pool không trả thread đủ nhanh. Task mới xếp hàng, timeout tăng, retry tăng và có thể kéo theo connection pool saturation, queue backlog hoặc health check failure.

## Project Role / Vai trò trong dự án

Thread Starvation là node cần mở khi p95/p99 latency tăng, request queue dài, thread pool active/max cao, app không nhận request mới hoặc worker xử lý chậm dù dependency mới là nguyên nhân thật. Nó giúp team debug thread dump, blocking call, async boundary, pool size, lock wait và downstream timeout.

## Output / Artifact nên có

- Thread pool dashboard: active thread, queued task, completed task rate, queue wait time
- Thread dump/profile khi sự cố xảy ra
- Blocking call inventory: DB, HTTP, filesystem, lock, sleep, sync-over-async
- Timeout/cancellation policy cho dependency call
- Load/soak test để thấy pool behavior dưới concurrency thật

## Decision Checklist / Câu hỏi kiểm tra

- Thread pool active có chạm max và queue task có tăng không?
- CPU thấp nhưng latency cao có phải vì thread đang block không?
- Thread dump cho thấy thread đang chờ lock, DB connection, HTTP call hay sleep?
- Có sync-over-async hoặc blocking I/O trong async request path không?
- Pool dùng chung cho request nhanh và job dài không?
- Timeout/cancellation có giải phóng thread khi dependency chậm không?
- Tăng pool size có thật sự giúp hay chỉ che bottleneck downstream?

## Failure Modes / Cách nó gây lỗi

- Blocking remote call giữ thread lâu làm request mới không được xử lý.
- Chờ database connection trong thread pool làm thread và connection pool cùng cạn.
- Job dài dùng chung executor với request realtime làm API latency tăng.
- Sync-over-async gây deadlock/starvation trong runtime async.
- Health check cũng cần thread nên service bị đánh dấu unhealthy dù process sống.
- Retry sau timeout tạo thêm request và làm pool starvation nặng hơn.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ ít concurrency có thể chưa cần tuning pool sâu, nhưng vẫn nên tránh blocking không cần thiết.
- Không nên tăng thread pool mù nếu bottleneck thật là database/API/lock.
- Không nên chuyển mọi thứ sang async nếu team chưa hiểu cancellation, backpressure và thread usage thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Resource Exhaustion]] vì thread pool cạn là một dạng cạn tài nguyên.
- [[Queue Backlog]] vì task chờ thread tạo backlog trong executor/request queue.
- [[Connection Pool Saturation]] vì thread và DB connection pool thường bão hòa cùng nhau.
- [[Timeout]] vì timeout/cancellation giúp thread không bị giữ vô hạn.
- [[Deadlock]] vì deadlock có thể làm thread bị block vĩnh viễn.

## Liên quan rộng

- Runtime performance
- Web server concurrency
- Executor design
- Async programming

## Keywords / Từ khóa tìm kiếm

- Thread Starvation
- thread pool starvation
- thiếu thread xử lý
- worker pool starvation
- executor queue
- queued task
- blocking call
- sync over async
- thread dump
- request queue
- pool active threads
- pool max threads
- thread starvation debugging
- async blocking
- worker starvation

## Source trace

- .NET ThreadPool documentation
- Java concurrency documentation
