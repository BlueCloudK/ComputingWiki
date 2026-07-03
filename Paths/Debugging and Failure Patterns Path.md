# Debugging and Failure Patterns Path

## Mục tiêu

Path này giúp người đọc đi từ symptom tới telemetry, failure pattern, mitigation và postmortem.

## Khi nào dùng path này

- Khi production có lỗi nhưng chưa rõ layer nào.
- Khi cần phân biệt performance, concurrency, dependency và data failure.
- Khi viết runbook hoặc postmortem.

## 1. Thu signal

- [[Logging]] — text event để hiểu hệ thống đã làm gì.
- [[Monitoring]] — metric và state theo thời gian.
- [[Alert]] — signal gọi người vào xử lý.
- [[Error Rate]] — biết lỗi tăng ở đâu và khi nào.
- [[Trace ID]] — nối request qua nhiều log/service.
- [[Distributed Tracing]] — nhìn đường đi request qua nhiều service.

## 2. Xác định failure scope

- [[Incident]] — sự kiện service ảnh hưởng user hoặc operation.
- [[Partial Failure]] — chỉ một phần hệ thống fail trong distributed system.
- [[Dependency Failure]] — lỗi đến từ service/library/third-party phụ thuộc.
- [[Cascading Failure]] — lỗi lan và khuếch đại qua nhiều component.
- [[Saturation]] — resource gần hoặc vượt ngưỡng chịu tải.

## 3. Runtime và resource failures

- [[Timeout]] — operation mất quá lâu và bị cắt.
- [[Retry]] — thử lại operation thất bại.
- [[Retry Storm]] — retry làm overload nặng hơn.
- [[Memory Leak]] — memory tăng dần không được giải phóng.
- [[Connection Leak]] — connection không được trả lại pool.
- [[Thread Starvation]] — thread không đủ để xử lý workload.
- [[Resource Exhaustion]] — hết CPU, memory, connection, disk hoặc quota.

## 4. Data và concurrency failures

- [[Race Condition]] — kết quả phụ thuộc timing không kiểm soát.
- [[Deadlock]] — các actor chờ nhau mãi.
- [[Lock Contention]] — nhiều transaction/thread tranh lock.
- [[Data Corruption]] — dữ liệu sai, hỏng hoặc mất integrity.
- [[Stale Cache]] — cache trả dữ liệu cũ quá lâu.
- [[N Plus One Query]] — query lặp làm latency tăng mạnh.

## 5. Debug artifacts

- [[Stack Trace]] — call stack tại thời điểm exception.
- [[Heap Dump]] — snapshot memory để tìm leak.
- [[Thread Dump]] — snapshot thread để debug deadlock/starvation.
- [[Core Dump]] — snapshot process khi crash sâu.
- [[Incident Timeline]] — timeline event, deploy, alert và action.
- [[Root Cause Analysis]] — tìm nguyên nhân hệ thống, không chỉ blame symptom.

## 6. Mitigation và learning

- [[Circuit Breaker]] — chặn dependency failure lan rộng.
- [[Backpressure]] — giảm input khi downstream quá tải.
- [[Brownout]] — giảm chất lượng có kiểm soát để giữ core service sống.
- [[Rollback]] — quay lại version/config trước.
- [[Postmortem]] — ghi lại lesson và action sau incident.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- Runbook
- Debug hypothesis
- Incident commander
- Safe mitigation
- Log sampling

## Related paths

- [[Backend Engineering Path]]
- [[DevOps Deployment Path]]
- [[Cloud Infrastructure Path]]
- [[Database Engineering Path]]
