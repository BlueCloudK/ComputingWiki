# Execution Plan

Aliases: Execution Plan, query execution plan

Type: Database Internals

## Context / Ngữ cảnh

Execution Plan xuất hiện khi database optimizer chọn cách thực thi query: scan bảng nào, dùng index nào, join theo thứ tự nào và chạy operator nào.

## Boundary / Ranh giới

### Nó là gì

Execution Plan là cây/graph operator mà database executor sẽ chạy để lấy dữ liệu, join, filter, sort, aggregate và trả result.

### Nó không phải là gì

Execution Plan không phải SQL text. Cùng một SQL có thể có nhiều plan khác nhau tùy statistics, index, parameter, data size và config.

## Core Mechanism / Cơ chế lõi

Optimizer ước lượng cost dựa trên statistics và chọn plan gồm operator như sequential scan, index scan, nested loop, hash join, sort hoặc aggregate. Executor chạy plan và tạo actual rows/time/buffer nếu dùng analyze.

## Project Role / Vai trò trong dự án

Dùng node này khi debug query chậm, đọc EXPLAIN, kiểm tra vì sao index không dùng, join sai strategy hoặc performance thay đổi sau data growth.

## Output / Artifact nên có

- EXPLAIN / EXPLAIN ANALYZE
- Estimated vs actual rows
- Operator tree
- Buffer/I/O stats
- Candidate fix: index, rewrite query, update stats

## Decision Checklist / Câu hỏi kiểm tra

- Plan dùng operator nào?
- Estimated rows có lệch actual không?
- Bottleneck nằm ở scan, join, sort hay I/O?
- Index/statistics có phù hợp không?
- Plan khác giữa dev và production vì data khác không?

## Failure Modes / Cách nó gây lỗi

- Statistics stale làm optimizer chọn plan sai.
- Estimated rows lệch khiến join strategy tệ.
- Sequential scan trên bảng lớn không mong muốn.
- Sort/hash join spill ra disk.
- Chỉ nhìn cost mà không xem actual time/buffer.

## Khi nào chưa cần hoặc dễ over-engineer

- Query nhỏ/chạy hiếm và đủ nhanh thì chưa cần tối ưu plan.
- Không nên ép planner bằng hint/config nếu chưa hiểu statistics và data distribution.

## Gồm những gì

- [[Sequential Scan]]
- [[Nested Loop Join]]
- [[Hash Join]]

## Nối mạnh

- [[Query Plan]] vì execution plan là biểu diễn cụ thể của query plan.
- [[Sequential Scan]] vì scan là operator phổ biến trong plan.
- [[Nested Loop Join]] vì nested loop là join strategy trong plan.
- [[Hash Join]] vì hash join là join strategy trong plan.
- [[Index]] vì index quyết định access path trong plan.

## Liên quan rộng

- Query optimizer
- EXPLAIN ANALYZE
- Cost estimation

## Keywords / Từ khóa tìm kiếm

- Execution Plan
- query execution plan
- EXPLAIN ANALYZE
- estimated rows
- actual rows
- query operator
- execution plan debugging

## Source trace

- PostgreSQL documentation
- Database System Concepts
