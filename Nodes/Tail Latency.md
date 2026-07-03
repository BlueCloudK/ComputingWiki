# Tail Latency

Aliases: p95/p99 latency, độ trễ đuôi

Type: Performance / Scalability

## Context / Ngữ cảnh

Tail Latency xuất hiện khi một phần nhỏ request chậm gây trải nghiệm xấu hoặc cascade trong hệ thống.

## Boundary / Ranh giới

### Nó là gì

Tail Latency là latency ở percentile cao như p95, p99 hoặc p999 thay vì average.

### Nó không phải là gì

Nó không phải average latency và không luôn do một bottleneck duy nhất.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là outlier từ queueing, GC, lock, slow dependency, retry hoặc noisy neighbor kéo percentile cao lên.

## Project Role / Vai trò trong dự án

Node này giúp SLO/performance nhìn đúng user bị chậm nhất thay vì trung bình đẹp.

## Output / Artifact nên có

- p95/p99/p999 latency dashboard
- Slow-request breakdown by dependency
- SLO alert tied to tail percentile

## Decision Checklist / Câu hỏi kiểm tra

- Percentile nào phản ánh user pain?
- Outlier đến từ queue, DB, GC hay network?
- Retry có làm tail latency tệ hơn không?

## Failure Modes / Cách nó gây lỗi

- Average xanh nhưng p99 làm user timeout
- Một dependency chậm kéo cả request fan-out
- Queue buildup tạo tail spike

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu traffic nhỏ và không có user-facing latency target
- Dễ over-engineer nếu percentile nhiễu do sample quá ít

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Latency]] vì tail latency là cách đo latency quan trọng
- [[Saturation]] vì saturation thường làm tail latency tăng mạnh

## Liên quan rộng

- Percentiles
- User experience

## Source trace

- Google SRE Books
- DDIA Ch01
