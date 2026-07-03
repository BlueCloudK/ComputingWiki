# Backpressure

Aliases: flow control pressure, điều tiết ngược

Type: Performance / Scalability

## Context / Ngữ cảnh

Backpressure xuất hiện khi producer gửi work nhanh hơn consumer hoặc downstream có thể xử lý, làm queue, memory hoặc latency tăng nguy hiểm.

## Boundary / Ranh giới

### Nó là gì

Backpressure là cơ chế để downstream báo hoặc ép upstream chậm lại, buffer có kiểm soát, drop, reject hoặc degrade khi quá tải.

### Nó không phải là gì

Nó không phải chỉ là queue lớn hơn, không thay thế capacity planning, và không tự sửa bottleneck gốc.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là điều tiết flow dựa trên sức xử lý thật: bounded queue, pull model, rate limit, retry policy, circuit breaker hoặc overload response.

## Project Role / Vai trò trong dự án

Backpressure giúp hệ thống fail có kiểm soát thay vì sập dây chuyền. Nó quan trọng trong stream processing, job queue, API gateway và service-to-service calls.

## Output / Artifact nên có

- Bounded queue hoặc overload policy
- Retry/drop/degrade rule
- Metric cho queue depth, lag, reject và saturation

## Decision Checklist / Câu hỏi kiểm tra

- Producer có thể tạo work nhanh hơn consumer không?
- Queue có bound và alert không?
- Khi full thì drop, reject, block hay degrade?
- Retry có làm overload tệ hơn không?
- User/downstream nhận tín hiệu gì khi bị backpressure?

## Failure Modes / Cách nó gây lỗi

- Queue unbounded làm memory tăng đến crash
- Retry loop làm downstream càng quá tải
- Drop data âm thầm không audit
- Backpressure quá mạnh làm user hợp lệ bị chặn không lý do rõ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần backpressure phức tạp nếu producer/consumer luôn cùng tốc độ thấp
- Dễ over-engineer nếu thêm flow control mà chưa biết bottleneck hoặc failure mode

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Throughput]] vì backpressure xử lý mismatch giữa arrival rate và processing rate
- [[Queue]] vì queue thường là nơi backpressure biểu hiện rõ nhất
- [[Overload Handling]] vì backpressure là một cách chống quá tải
- [[Stream Processing]] vì stream cần điều tiết flow liên tục

## Liên quan rộng

- Flow control
- Load shedding
- Retry policy

## Source trace

- Designing Data-Intensive Applications
- Google SRE Books
