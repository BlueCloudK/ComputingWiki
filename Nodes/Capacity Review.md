# Capacity Review

Aliases: Capacity Review, capacity planning review

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Capacity Review xuất hiện khi hệ thống cần kiểm tra tài nguyên hiện tại có đủ chịu traffic, dữ liệu, queue backlog, storage growth hoặc workload mới không.

## Boundary / Ranh giới

### Nó là gì

Capacity Review là hoạt động đánh giá capacity dựa trên workload forecast, current utilization, bottleneck, scaling policy và failure margin.

### Nó không phải là gì

Capacity Review không chỉ là nhìn CPU/RAM hiện tại. Nó phải xét peak, growth, dependency limit, queue, database, network và rollback/surge scenario.

## Core Mechanism / Cơ chế lõi

Team thu metric lịch sử, dự báo growth, xác định bottleneck, so với limit/SLO, rồi quyết định scale up/out, optimize, shard, cache, rate limit hoặc đặt alert mới.

## Project Role / Vai trò trong dự án

Dùng node này trước release lớn, event traffic, migration, load test, cloud cost review hoặc khi hệ thống gần saturation.

## Output / Artifact nên có

- Current utilization report
- Forecast workload
- Bottleneck list
- Scaling decision
- Alert/SLO threshold update
- Risk và action owner

## Decision Checklist / Câu hỏi kiểm tra

- Bottleneck hiện tại là CPU, memory, DB, queue hay network?
- Peak traffic cao hơn average bao nhiêu?
- Dependency nào có hard limit?
- Scaling policy có test chưa?
- Cost tăng bao nhiêu nếu scale?

## Failure Modes / Cách nó gây lỗi

- Chỉ nhìn average, bỏ qua peak.
- DB/queue bottleneck bị che bởi CPU app còn thấp.
- Autoscaling có nhưng dependency downstream không scale.
- Forecast không tính campaign/release lớn.
- Không có action owner sau review.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype ít user có thể chỉ cần metric cơ bản.
- Không nên capacity plan quá chi tiết nếu workload chưa có signal thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Monitoring]] vì capacity review dựa trên metric lịch sử.
- [[Resource Exhaustion]] vì capacity thiếu dẫn tới exhaustion.
- [[Load Balancer]] vì scaling/traffic distribution ảnh hưởng capacity.
- [[Queue Backlog]] vì backlog là signal capacity không đủ.

## Liên quan rộng

- Capacity planning
- Load testing
- Scaling strategy

## Keywords / Từ khóa tìm kiếm

- Capacity Review
- capacity planning
- resource utilization
- bottleneck analysis
- traffic forecast
- capacity review debugging

## Source trace

- Google SRE Books
- Designing Data-Intensive Applications
