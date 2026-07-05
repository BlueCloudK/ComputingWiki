# Nested Loop Join

Aliases: Nested Loop Join, nested loop join

Type: Database Internals

## Context / Ngữ cảnh

Nested Loop Join xuất hiện trong query plan khi database nối hai input bằng cách lặp qua outer rows và tìm matching rows ở inner side.

## Boundary / Ranh giới

### Nó là gì

Nested Loop Join là join strategy trong query execution. Với mỗi row từ outer input, database dò inner input bằng scan hoặc index lookup để tìm row khớp join condition.

### Nó không phải là gì

Nested Loop Join không tự xấu. Nó tốt khi outer input nhỏ hoặc inner side có index phù hợp; nó tệ khi hai phía lớn và lookup lặp quá nhiều.

## Core Mechanism / Cơ chế lõi

Planner chọn outer/inner input. Executor lấy từng row outer, chạy inner lookup theo join condition, emit cặp row match. Chi phí xấp xỉ outer rows nhân chi phí inner lookup.

## Project Role / Vai trò trong dự án

Dùng node này khi đọc EXPLAIN plan, debug query join chậm, index thiếu, row estimate sai hoặc N+1-like pattern trong SQL plan.

## Output / Artifact nên có

- EXPLAIN/ANALYZE plan
- Outer/inner row count
- Join condition
- Inner access path: index scan hay seq scan
- Before/after index/query comparison

## Decision Checklist / Câu hỏi kiểm tra

- Outer input có nhỏ không?
- Inner lookup có dùng index không?
- Row estimate có sát actual không?
- Join condition có selective không?
- Có join strategy khác tốt hơn không?

## Failure Modes / Cách nó gây lỗi

- Outer rows lớn làm inner lookup lặp rất nhiều.
- Inner side thiếu index nên mỗi row outer gây scan lớn.
- Statistic sai làm planner chọn nested loop nhầm.
- Filter apply quá muộn khiến join xử lý nhiều row thừa.
- Query chạy nhanh ở dev data nhỏ nhưng chậm ở production data lớn.

## Khi nào chưa cần hoặc dễ over-engineer

- Query nhỏ/chạy hiếm và đủ nhanh thì chưa cần ép plan.
- Không nên disable join strategy nếu chưa hiểu row estimate và data distribution.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Query Plan]] vì nested loop join là node trong execution plan.
- [[Index]] vì inner lookup thường cần index để nested loop hiệu quả.
- [[N Plus One Query]] vì cả hai đều có pattern lặp lookup nhiều lần.
- [[Performance Optimization]] vì join strategy ảnh hưởng query latency.

## Liên quan rộng

- Join algorithm
- Query execution
- Row estimate

## Keywords / Từ khóa tìm kiếm

- Nested Loop Join
- nested loop join
- join algorithm
- EXPLAIN ANALYZE
- index lookup
- row estimate
- nested loop join debugging

## Source trace

- PostgreSQL documentation
- Database System Concepts
