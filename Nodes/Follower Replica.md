# Follower Replica

Aliases: Follower Replica, read replica

Type: Database Internals

## Context / Ngữ cảnh

Follower Replica xuất hiện trong replicated database khi một node nhận change từ primary/leader và thường phục vụ read, backup hoặc failover.

## Boundary / Ranh giới

### Nó là gì

Follower Replica là replica đi theo primary bằng cách nhận log/change stream và replay/apply để giữ dữ liệu gần giống primary.

### Nó không phải là gì

Follower Replica không phải nguồn ghi chính trong mô hình primary-replica bình thường. Write thường đi vào primary; follower có thể read-only hoặc chỉ được promote khi failover.

## Core Mechanism / Cơ chế lõi

Primary tạo log/change. Follower nhận stream, ghi lại và apply theo thứ tự. Follower có thể bị lag, có thể phục vụ read stale và có thể được promote nếu primary fail.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế read scaling, backup trên replica, failover, replication delay, stale read hoặc debug app ghi nhầm vào read-only replica.

## Output / Artifact nên có

- Replica role/topology
- Replication lag metric
- Read routing rule
- Promotion/failover procedure
- Backup/reporting workload note

## Decision Checklist / Câu hỏi kiểm tra

- Follower dùng để đọc, backup hay failover?
- Lag tối đa chấp nhận được là bao nhiêu?
- App có route read stale-sensitive sang follower không?
- Follower có đủ resource để replay và query không?
- Promote follower có an toàn không?

## Failure Modes / Cách nó gây lỗi

- Read từ follower trả dữ liệu cũ.
- Reporting query nặng làm replica lag tăng.
- Follower được promote khi chưa bắt kịp log.
- App cố write vào read-only follower.
- Backup trên follower tưởng không ảnh hưởng nhưng làm replay chậm.

## Khi nào chưa cần hoặc dễ over-engineer

- Workload nhỏ chưa cần read scaling/HA có thể chưa cần follower.
- Không nên thêm follower nếu chưa có monitoring lag và routing rule rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Primary Replica]] vì follower nhận change từ primary.
- [[Replication Delay]] vì follower có thể bị lag.
- [[Synchronous Replication]] vì follower có thể là sync/async replica.
- [[Backup]] vì follower thường được dùng để giảm tải backup khỏi primary.

## Liên quan rộng

- Read replica
- Failover
- Stale read

## Keywords / Từ khóa tìm kiếm

- Follower Replica
- read replica
- follower database
- replica lag
- read-only replica
- failover promotion
- follower replica debugging

## Source trace

- PostgreSQL documentation
- Designing Data-Intensive Applications
