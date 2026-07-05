# Database Vacuum Lag

Aliases: Database Vacuum Lag, vacuum lag

Type: Database Internals

## Context / Ngữ cảnh

Database Vacuum Lag xuất hiện khi database dùng MVCC và cleanup dead tuples/version cũ không theo kịp tốc độ write/update/delete.

## Boundary / Ranh giới

### Nó là gì

Database Vacuum Lag là tình trạng quá trình vacuum/cleanup bị chậm, khiến dead row/version cũ tích tụ, table/index bloat tăng và query/storage performance giảm.

### Nó không phải là gì

Vacuum lag không phải chỉ là database “đầy disk”. Nó là signal rằng cleanup lifecycle phía storage/MVCC đang bị tụt sau workload thật.

## Core Mechanism / Cơ chế lõi

Transaction update/delete tạo version cũ. Vacuum cần biết version nào không còn transaction nào cần đọc, rồi reclaim space hoặc đánh dấu có thể reuse. Long transaction, workload write cao hoặc config yếu có thể làm vacuum tụt lại.

## Project Role / Vai trò trong dự án

Dùng node này khi debug table bloat, query chậm dần, autovacuum không theo kịp, disk tăng bất thường hoặc PostgreSQL workload update-heavy.

## Output / Artifact nên có

- Dead tuple / bloat metric
- Long transaction list
- Vacuum/autovacuum log
- Table/index growth trend
- Remediation plan: tune, batch, vacuum, reindex nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Dead tuple tăng ở bảng nào?
- Có long-running transaction giữ version cũ không?
- Autovacuum có chạy nhưng không theo kịp không?
- Bloat ảnh hưởng query/index nào?
- Cleanup có cần maintenance window không?

## Failure Modes / Cách nó gây lỗi

- Long transaction chặn cleanup.
- Write-heavy workload tạo dead tuple nhanh hơn vacuum.
- Table/index bloat làm query đọc nhiều page hơn.
- Vacuum chạy lúc peak gây I/O cạnh tranh.
- Chỉ tăng disk mà không xử lý nguyên nhân transaction/workload.

## Khi nào chưa cần hoặc dễ over-engineer

- Bảng nhỏ, ít update có thể chưa cần tối ưu vacuum.
- Không nên chạy VACUUM FULL/reindex nặng nếu chưa hiểu lock, downtime và nguyên nhân bloat.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Storage Layout]] vì dead tuple/bloat là vấn đề physical storage.
- [[Page Cache]] vì bloat làm đọc nhiều page hơn và giảm cache efficiency.
- [[Transaction]] vì long transaction có thể giữ version cũ.
- [[Performance Optimization]] vì vacuum lag ảnh hưởng latency và I/O.

## Liên quan rộng

- MVCC cleanup
- Autovacuum
- Table bloat
- Dead tuple

## Keywords / Từ khóa tìm kiếm

- Database Vacuum Lag
- vacuum lag
- autovacuum lag
- dead tuples
- table bloat
- long transaction
- vacuum lag debugging

## Source trace

- PostgreSQL documentation
- Designing Data-Intensive Applications
