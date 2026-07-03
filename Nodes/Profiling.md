# Profiling

Aliases: locate bottleneck, profiling

Type: Performance / Scalability

## Context / Ngữ cảnh

Profiling xuất hiện khi tốc độ, throughput, resource usage hoặc khả năng chịu tải ảnh hưởng tới user, cost hoặc reliability.

## Boundary / Ranh giới

### Nó là gì

Profiling là cách nhìn hệ thống qua metric và bottleneck thay vì cảm giác nhanh/chậm.

### Nó không phải là gì

Nó không phải tối ưu mọi thứ; nếu không có baseline, workload và threshold thì tối ưu dễ sai chỗ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đo metric, tạo benchmark/load test đại diện, tìm bottleneck và chốt trade-off giữa performance, cost và complexity.

## Project Role / Vai trò trong dự án

Profiling ảnh hưởng tới việc chọn index/cache/queue/scale/refactor và quyết định khi nào tối ưu là đáng làm.

## Output / Artifact nên có

- Metric/baseline rõ p95 latency, throughput, error rate hoặc resource usage
- Benchmark hoặc load test mô phỏng workload chính
- Decision note về bottleneck, threshold và trade-off cost/complexity

## Decision Checklist / Câu hỏi kiểm tra

- Metric nào chứng minh vấn đề performance thật?
- Workload test có giống usage production không?
- Bottleneck nằm ở CPU, memory, I/O, database, network hay lock?
- Threshold pass/fail là bao nhiêu và ai chấp nhận?
- Tối ưu này làm tăng cost/complexity ở đâu?

## Failure Modes / Cách nó gây lỗi

- Benchmark không giống production nên kết luận sai
- Tối ưu sớm làm code phức tạp mà chưa giải bottleneck thật
- Cache/index/scale làm tăng cost hoặc inconsistency
- Không đo baseline nên không biết thay đổi có hiệu quả không

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tối ưu sâu khi chưa có metric hoặc user impact
- Dễ over-engineer nếu scale architecture trước khi workload chứng minh cần

## Gồm những gì

- [[Bottleneck]]
- [[Benchmark]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Capacity planning
- Operations
- Database tuning
- Cost control

## Keywords / Từ khóa tìm kiếm

- Profiling
- locate bottleneck
- Performance
- Scalability

## Source trace

- Performance maps
