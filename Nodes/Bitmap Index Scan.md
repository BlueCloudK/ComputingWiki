# Bitmap Index Scan

Aliases: Bitmap Index Scan, bitmap heap scan

Type: Database Internals

## Context / Ngữ cảnh

Bitmap Index Scan xuất hiện trong query plan khi database dùng index để tạo bitmap các row/page candidate rồi đọc heap/table theo bitmap đó.

## Boundary / Ranh giới

### Nó là gì

Bitmap Index Scan là execution strategy dùng index để đánh dấu vị trí row phù hợp, thường hữu ích khi query match nhiều row hoặc cần kết hợp nhiều index.

### Nó không phải là gì

Bitmap Index Scan không phải một loại index riêng trong mọi database. Nó thường là cách planner sử dụng index trong execution plan.

## Core Mechanism / Cơ chế lõi

Database scan index để tạo bitmap tuple/page candidate, có thể combine bitmap bằng AND/OR, rồi đọc table page theo bitmap để lấy row thật và recheck condition nếu cần.

## Project Role / Vai trò trong dự án

Dùng node này khi đọc EXPLAIN plan, debug query chậm, hiểu vì sao planner không dùng index scan trực tiếp hoặc vì sao query vẫn đọc nhiều heap page.

## Output / Artifact nên có

- EXPLAIN/ANALYZE plan
- Index condition
- Heap block/page read metric
- Recheck condition note
- Before/after query/index comparison

## Decision Checklist / Câu hỏi kiểm tra

- Bitmap scan đang dùng index nào?
- Số row/page candidate có quá lớn không?
- Có recheck condition nhiều không?
- Bitmap scan tốt hơn seq scan/index scan trực tiếp không?
- Statistic có cũ không?

## Failure Modes / Cách nó gây lỗi

- Planner chọn bitmap scan nhưng row estimate sai.
- Bitmap quá lớn làm memory/temp cost tăng.
- Heap recheck nhiều làm query chậm.
- Index condition không selective đủ.
- Statistic stale khiến plan chọn sai.

## Khi nào chưa cần hoặc dễ over-engineer

- Không cần tối ưu khi query đã đủ nhanh và plan ổn định.
- Không nên ép planner bằng hint/rule nếu chưa hiểu data distribution.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Query Plan]] vì bitmap scan là node trong execution plan.
- [[Index]] vì bitmap scan dựa trên index condition.
- [[Nonclustered Index]] vì secondary index có thể là nguồn bitmap.
- [[Performance Optimization]] vì hiểu plan giúp tối ưu query đúng chỗ.

## Liên quan rộng

- EXPLAIN ANALYZE
- Query execution
- Index selectivity

## Keywords / Từ khóa tìm kiếm

- Bitmap Index Scan
- bitmap heap scan
- EXPLAIN ANALYZE
- index condition
- heap recheck
- query plan debugging

## Source trace

- PostgreSQL documentation
- Database System Concepts
