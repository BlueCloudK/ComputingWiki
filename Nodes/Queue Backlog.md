# Queue Backlog

Aliases: queue buildup, hàng đợi tồn đọng

Type: Failure Pattern

## Context / Ngữ cảnh

Queue Backlog xuất hiện khi tốc độ message/job/request đi vào queue cao hơn tốc độ consumer xử lý trong một khoảng thời gian đủ dài. Nó thường gặp ở Kafka/RabbitMQ/SQS, background job queue, task scheduler, email worker, event processor, stream pipeline hoặc internal work queue.

## Boundary / Ranh giới

### Nó là gì

Queue Backlog là trạng thái hàng đợi tích lũy workload chưa xử lý. Dấu hiệu chính là queue length, consumer lag, oldest message age hoặc processing delay tăng. Backlog không luôn là lỗi ngay lập tức, nhưng trở thành failure khi latency vượt SLO, memory/disk đầy, message expire hoặc downstream bị trễ.

### Nó không phải là gì

Queue Backlog không phải chỉ là queue có nhiều message. Một queue batch có thể tích lũy rồi drain theo thiết kế. Vấn đề nằm ở xu hướng backlog tăng không kiểm soát, consumer xử lý chậm hơn arrival rate hoặc hệ thống không có kế hoạch catch-up/backpressure.

## Core Mechanism / Cơ chế lõi

Queue nhận workload với arrival rate, consumer xử lý với service rate. Nếu arrival rate > service rate, backlog tăng theo thời gian. Nguyên nhân có thể là traffic spike, consumer crash, downstream slow, poison message, retry loop, partition skew, lock/database chậm hoặc worker concurrency quá thấp.

## Project Role / Vai trò trong dự án

Queue Backlog là node cần mở khi job trễ, event xử lý muộn, notification/email gửi chậm, consumer lag tăng hoặc queue disk/memory đầy. Nó giúp team debug theo chuỗi: producer rate → queue length/age → consumer health → processing time → downstream dependency → retry/dead-letter behavior.

## Output / Artifact nên có

- Queue dashboard: queue length, oldest message age, consumer lag, processing rate, error/retry rate
- Capacity note: producer rate, consumer concurrency, average processing time, catch-up time
- Backpressure/admission policy khi queue vượt threshold
- Dead-letter/poison message runbook
- Load/soak test mô phỏng burst traffic và consumer slowdown

## Decision Checklist / Câu hỏi kiểm tra

- Backlog tăng do producer tăng, consumer giảm hay downstream chậm?
- Oldest message age có vượt SLO không?
- Consumer có đang crash/restart hoặc bị poison message block không?
- Partition/key có bị skew khiến một partition lag nặng không?
- Retry policy có làm message quay lại queue quá nhanh không?
- Có dead-letter queue và alert cho retry vượt ngưỡng không?
- Hệ thống có backpressure hoặc rate limit producer khi queue quá tải không?

## Failure Modes / Cách nó gây lỗi

- Message xử lý quá trễ làm user nhận notification/job result muộn.
- Queue đầy memory/disk làm producer fail hoặc broker bị áp lực.
- Poison message làm consumer lặp lỗi và chặn message phía sau.
- Retry storm làm backlog tăng nhanh hơn consumer có thể drain.
- Consumer scale-out nhưng partition/key skew khiến throughput không tăng tương ứng.
- Downstream database/API chậm làm worker giữ thread/connection lâu và backlog lan rộng.

## Khi nào chưa cần hoặc dễ over-engineer

- Batch queue có backlog theo chu kỳ là bình thường nếu catch-up time nằm trong SLO.
- Không nên scale consumer mù nếu bottleneck thật là downstream database/API.
- Không nên thêm queue vào mọi workflow nếu cần response đồng bộ và không có strategy xử lý trễ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Backpressure]] vì backlog cần cơ chế giảm tải producer hoặc giới hạn consumption.
- [[Retry]] vì retry sai có thể làm queue backlog nặng hơn.
- [[Resource Exhaustion]] vì queue tăng không kiểm soát có thể làm cạn memory/disk/quota.
- [[Thread Starvation]] vì worker thread bị block có thể làm consumer không drain được queue.

## Liên quan rộng

- Event-driven architecture
- Stream processing
- Background jobs
- Incident response

## Keywords / Từ khóa tìm kiếm

- Queue Backlog
- queue buildup
- hàng đợi tồn đọng
- consumer lag
- oldest message age
- queue length
- processing delay
- producer rate
- service rate
- dead letter queue
- poison message
- partition skew
- queue saturation
- catch up time
- queue backlog debugging

## Source trace

- Little's Law
- Apache Kafka documentation
