# Join Order

Aliases: Join Order, join ordering

Type: Database Internals

## Context / Ngữ cảnh

Join Order xuất hiện khi một query join nhiều bảng và database optimizer phải chọn bảng nào join trước để giảm số row trung gian và chi phí execution.

## Boundary / Ranh giới

### Nó là gì

Join Order là thứ tự optimizer/executor kết hợp các relation trong query plan.

### Nó không phải là gì

Join Order không chỉ là thứ tự bảng viết trong SQL. Optimizer thường có thể reorder join dựa trên statistics, constraint và cost model.

## Core Mechanism / Cơ chế lõi

Optimizer ước lượng cardinality/selectivity của từng relation và join predicate, sau đó chọn thứ tự join có chi phí thấp nhất hoặc đủ tốt trong không gian search.

## Project Role / Vai trò trong dự án

Dùng node này khi debug query join nhiều bảng bị chậm, row estimate lệch, join explosion, plan thay đổi sau data growth hoặc index/statistics không đủ tốt.

## Output / Artifact nên có

- EXPLAIN/ANALYZE plan
- Join tree/order
- Estimated vs actual rows per join
- Join predicate/selectivity note
- Candidate index/statistics/query rewrite

## Decision Checklist / Câu hỏi kiểm tra

- Join nào làm row trung gian phình lớn?
- Estimated rows có lệch actual không?
- Predicate có selective không?
- Statistics/index có đủ để optimizer chọn đúng không?
- Query có outer join/constraint làm hạn chế reorder không?

## Failure Modes / Cách nó gây lỗi

- Optimizer join bảng lớn quá sớm làm intermediate result phình.
- Statistics stale làm chọn join order sai.
- Predicate correlation không được model đúng.
- Outer join hoặc function predicate hạn chế khả năng reorder.
- Dev data nhỏ nên plan ổn, production data lớn thì vỡ.

## Khi nào chưa cần hoặc dễ over-engineer

- Query ít bảng, dữ liệu nhỏ và latency ổn thì chưa cần đào sâu.
- Không nên ép join order nếu chưa hiểu statistics và actual row count.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Execution Plan]] vì join order là phần quan trọng của execution plan.
- [[Query Plan]] vì optimizer chọn join order trong query plan.
- [[Hash Join]] vì join order quyết định build/probe side.
- [[Nested Loop Join]] vì outer/inner side phụ thuộc join order.

## Liên quan rộng

- Query optimizer
- Cardinality estimation
- Join explosion

## Keywords / Từ khóa tìm kiếm

- Join Order
- join ordering
- query optimizer
- join tree
- cardinality estimation
- join explosion
- join order debugging

## Source trace

- PostgreSQL documentation
- Database System Concepts
