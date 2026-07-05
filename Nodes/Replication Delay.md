# Replication Delay

Aliases: Replication Delay, replication lag

Type: Database Internals

## Context / Ngữ cảnh

Replication Delay xuất hiện khi replica không bắt kịp primary, làm dữ liệu đọc từ replica cũ hơn dữ liệu đã ghi trên primary.

## Boundary / Ranh giới

### Nó là gì

Replication Delay là độ trễ giữa thời điểm change được commit/ghi trên primary và thời điểm change đó được replica nhận, replay hoặc apply xong.

### Nó không phải là gì

Replication Delay không chỉ là network latency. Nó còn có thể đến từ write volume, disk I/O, replay chậm, lock, long transaction hoặc replica resource yếu.

## Core Mechanism / Cơ chế lõi

Primary tạo log/change stream. Replica nhận stream, ghi lại và replay/apply theo thứ tự. Nếu replica xử lý chậm hơn tốc độ change đến, lag tăng và read trên replica có thể stale.

## Project Role / Vai trò trong dự án

Dùng node này khi debug read-after-write inconsistency, replica stale, failover risk, reporting query chậm làm replica tụt hoặc alert replication lag.

## Output / Artifact nên có

- Replication lag metric
- Primary/replica topology
- Replay/apply position
- Workload causing lag
- Mitigation plan: throttle, scale, route read, failover rule

## Decision Checklist / Câu hỏi kiểm tra

- Lag đo bằng thời gian, byte/log position hay transaction count?
- Replica dùng cho read path nào?
- User có cần read-after-write consistency không?
- Lag tăng do network, disk, CPU hay query trên replica?
- Failover có an toàn khi replica chưa bắt kịp không?

## Failure Modes / Cách nó gây lỗi

- User vừa ghi xong nhưng đọc replica không thấy dữ liệu.
- Replica lag lớn nhưng vẫn được dùng cho critical read.
- Failover promote replica thiếu dữ liệu.
- Reporting query nặng làm replay/apply chậm.
- Alert chỉ nhìn replica up/down, không nhìn lag.

## Khi nào chưa cần hoặc dễ over-engineer

- App một database node chưa có replica thì chưa cần xử lý replication delay.
- Không nên route read sang replica nếu product cần consistency mạnh mà không có lag guard.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Primary Replica]] vì delay xảy ra giữa primary và replica.
- [[Follower Replica]] vì follower có thể tụt sau primary.
- [[Replication Stream]] vì delay phản ánh stream/replay chưa bắt kịp.
- [[Synchronous Replication]] vì sync mode giảm một số lag đổi lại latency/availability.

## Liên quan rộng

- Replica lag
- Stale read
- Failover safety

## Keywords / Từ khóa tìm kiếm

- Replication Delay
- replication lag
- stale replica
- read after write
- replica replay lag
- failover lag
- replication delay debugging

## Source trace

- PostgreSQL documentation
- Designing Data-Intensive Applications
