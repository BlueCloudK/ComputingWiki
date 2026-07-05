# Synchronous Replication

Aliases: Synchronous Replication, sync replication

Type: Database Internals

## Context / Ngữ cảnh

Synchronous Replication xuất hiện khi database cần đảm bảo write chỉ được xem là commit sau khi replica nhất định đã nhận hoặc xác nhận thay đổi.

## Boundary / Ranh giới

### Nó là gì

Synchronous Replication là replication mode trong đó primary chờ replica acknowledge theo policy trước khi trả commit thành công cho client.

### Nó không phải là gì

Synchronous Replication không tự đảm bảo hệ thống luôn available. Nếu replica chậm hoặc mất kết nối, commit latency có thể tăng hoặc write path bị block tùy cấu hình.

## Core Mechanism / Cơ chế lõi

Primary ghi transaction log, gửi change tới synchronous replica và chờ acknowledgement ở mức configured như received, flushed hoặc applied. Khi điều kiện đạt, primary mới hoàn tất commit với client.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế durability/RPO, HA database, failover, write latency tradeoff hoặc debug commit chậm do replica/network.

## Output / Artifact nên có

- Replication topology
- Sync replica policy
- Commit latency metric
- Replication lag/ack status
- Failover and degradation rule

## Decision Checklist / Câu hỏi kiểm tra

- Commit cần chờ bao nhiêu replica?
- Ack ở mức receive, flush hay apply?
- Replica chậm thì write path xử lý ra sao?
- RPO/RTO mục tiêu là gì?
- Failover có tránh mất acknowledged transaction không?

## Failure Modes / Cách nó gây lỗi

- Replica chậm làm commit latency tăng.
- Replica down làm write bị block nếu policy quá chặt.
- Network jitter tạo spike latency.
- Tưởng sync replication thay thế backup.
- Failover chọn node chưa đủ đồng bộ theo kỳ vọng.

## Khi nào chưa cần hoặc dễ over-engineer

- Workload chấp nhận mất vài giây dữ liệu có thể dùng async replication để giảm latency.
- Không nên bật sync replication nếu chưa đo latency và có plan khi replica mất kết nối.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Primary Replica]] vì sync replication thường diễn ra giữa primary và replica.
- [[Replication Stream]] vì change được truyền qua replication stream.
- [[Transaction]] vì commit behavior bị ảnh hưởng trực tiếp.
- [[Split Brain]] vì failover/primary role sai có thể gây consistency issue.

## Liên quan rộng

- High availability
- Durability
- Replication lag
- Failover

## Keywords / Từ khóa tìm kiếm

- Synchronous Replication
- sync replication
- synchronous commit
- replica acknowledgement
- replication lag
- commit latency
- synchronous replication debugging

## Source trace

- PostgreSQL documentation
- Designing Data-Intensive Applications
