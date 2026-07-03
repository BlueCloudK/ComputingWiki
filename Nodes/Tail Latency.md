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

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

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
