# Sequential Scan

Aliases: Sequential Scan, table scan

Type: Database Internals

## Context / Ngữ cảnh

Sequential Scan xuất hiện trong query plan khi database đọc tuần tự toàn bộ table hoặc một phần lớn table thay vì dùng index lookup trực tiếp.

## Boundary / Ranh giới

### Nó là gì

Sequential Scan là access path trong đó executor đọc các page/row của table theo thứ tự vật lý và filter row theo điều kiện query.

### Nó không phải là gì

Sequential Scan không luôn xấu. Với table nhỏ, filter không selective hoặc query cần phần lớn rows, sequential scan có thể nhanh hơn index scan.

## Core Mechanism / Cơ chế lõi

Executor đọc page từ heap/table storage, kiểm tra visibility và predicate cho từng row, rồi trả row match. Cost phụ thuộc table size, page cache, bloat, predicate selectivity và I/O.

## Project Role / Vai trò trong dự án

Dùng node này khi đọc EXPLAIN plan, debug query chậm, index không được dùng, table bloat hoặc benchmark cold/warm cache khác nhau.

## Output / Artifact nên có

- EXPLAIN/ANALYZE plan
- Rows scanned vs rows returned
- Buffer/page read stats
- Predicate selectivity
- Index/bloat comparison

## Decision Checklist / Câu hỏi kiểm tra

- Table lớn hay nhỏ?
- Query trả phần lớn rows không?
- Predicate có index phù hợp không?
- Statistics có stale không?
- Scan đang đọc từ cache hay disk?

## Failure Modes / Cách nó gây lỗi

- Table lớn bị scan toàn bộ cho query trả ít row.
- Index thiếu hoặc không selective.
- Statistics sai làm planner chọn scan nhầm.
- Bloat làm scan đọc nhiều page hơn cần.
- Dev data nhỏ nên scan ổn, production data lớn thì chậm.

## Khi nào chưa cần hoặc dễ over-engineer

- Table nhỏ và query hiếm chạy thì sequential scan có thể chấp nhận được.
- Không nên ép index scan nếu planner chọn sequential scan hợp lý theo data distribution.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Query Plan]] vì sequential scan là node trong execution plan.
- [[Storage Layout]] vì scan đọc table theo layout vật lý.
- [[Page Cache]] vì cache quyết định cold/warm scan cost.
- [[Read Amplification]] vì scan nhiều page thừa làm read amplification cao.

## Liên quan rộng

- Table scan
- Predicate selectivity
- Buffer reads

## Keywords / Từ khóa tìm kiếm

- Sequential Scan
- table scan
- seq scan
- EXPLAIN ANALYZE
- predicate selectivity
- buffer reads
- sequential scan debugging

## Source trace

- PostgreSQL documentation
- Database System Concepts
