# Primary Replica

Aliases: Primary Replica, primary database

Type: Database Internals

## Context / Ngữ cảnh

Primary Replica xuất hiện trong replicated database khi một node là nơi nhận write chính và các replica khác sao chép dữ liệu từ nó.

## Boundary / Ranh giới

### Nó là gì

Primary Replica là database node giữ vai trò authoritative cho write path trong mô hình primary-replica replication.

### Nó không phải là gì

Primary Replica không đồng nghĩa với “node nhanh nhất”. Nó là vai trò replication/consistency; read/write routing, failover và durability mới quyết định behavior thật.

## Core Mechanism / Cơ chế lõi

Client hoặc proxy gửi write tới primary. Primary ghi transaction log/data, rồi replication stream gửi thay đổi tới replica. Khi primary lỗi, hệ thống có thể promote replica khác nếu đáp ứng rule failover.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế read/write split, failover, replication lag, backup, database maintenance hoặc debug app ghi nhầm vào replica read-only.

## Output / Artifact nên có

- Primary/replica topology
- Write routing rule
- Replication lag metric
- Failover/promotion procedure
- Backup/maintenance note

## Decision Checklist / Câu hỏi kiểm tra

- Node nào đang là primary thật?
- App/proxy route write tới đâu?
- Replica lag có chấp nhận được không?
- Failover có tự động hay thủ công?
- Sau promotion, client reconnect thế nào?

## Failure Modes / Cách nó gây lỗi

- App ghi nhầm vào replica read-only.
- Split brain làm nhiều node tưởng là primary.
- Replica lag làm read-after-write không thấy dữ liệu mới.
- Failover promote node chưa bắt kịp log.
- Backup chạy trên primary làm ảnh hưởng write workload.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ có một database node có thể chưa cần primary-replica topology.
- Không nên thêm replica nếu chưa có monitoring lag và failover plan.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Replication Stream]] vì primary gửi change stream tới replica.
- [[Split Brain]] vì primary role sai có thể gây split brain.
- [[Transaction]] vì write durability bắt đầu từ transaction trên primary.
- [[Backup]] vì backup strategy cần biết primary/replica role.

## Liên quan rộng

- Database replication
- Failover
- Read replica

## Keywords / Từ khóa tìm kiếm

- Primary Replica
- primary database
- primary replica
- read replica
- failover
- replication lag
- primary replica debugging

## Source trace

- Designing Data-Intensive Applications
- PostgreSQL documentation
