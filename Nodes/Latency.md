# Latency

Aliases: response time, độ trễ

Type: Performance / Scalability

## Context / Ngữ cảnh

Latency xuất hiện khi cần biết user hoặc downstream service phải chờ bao lâu để một operation hoàn tất.

## Boundary / Ranh giới

### Nó là gì

Latency là thời gian từ lúc request/work bắt đầu đến khi nhận được response/result, thường đo bằng percentile thay vì chỉ average.

### Nó không phải là gì

Nó không phải throughput, không phải availability, và average latency không đủ mô tả trải nghiệm người dùng.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đo path end-to-end hoặc từng segment: network, queue, compute, database, external call. Tail latency thường quyết định cảm nhận của user.

## Project Role / Vai trò trong dự án

Latency giúp đặt NFR, SLO và performance budget. Nó chỉ ra user journey nào cần tối ưu và tầng nào đang làm chậm request.

## Output / Artifact nên có

- Latency metric theo p50/p95/p99
- Breakdown theo service/database/external dependency
- Target latency cho flow quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Đang đo end-to-end hay internal segment?
- Percentile nào phản ánh user impact?
- Latency tăng do compute, queue, DB hay network?
- Target có gắn với NFR/SLO không?
- Optimization có trade-off với correctness/cost không?

## Failure Modes / Cách nó gây lỗi

- Chỉ nhìn average nên bỏ qua tail latency
- Tối ưu nhầm segment không nằm trên critical path
- Không phân biệt latency client thấy và latency server đo
- Cache/async làm nhanh hơn nhưng sai freshness hoặc consistency

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tối ưu latency khi flow không critical và chưa có baseline
- Dễ over-engineer nếu giảm vài ms không tác động user/business

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Nonfunctional Requirement]] vì latency thường là quality target cần đo
- [[Benchmark]] vì latency target cần baseline đo được
- [[Queue]] vì queueing delay có thể làm tail latency tăng mạnh

## Liên quan rộng

- Response time
- User experience
- Tail latency

## Keywords / Từ khóa tìm kiếm

- Latency
- response time
- request latency
- p95 latency
- p99 latency
- service latency
- network delay
- user perceived delay
- độ trễ
- thời gian phản hồi

## Source trace

- Designing Data-Intensive Applications Ch01
- Google SRE Books
