# Hash Join

Aliases: Hash Join, hash join

Type: Database Internals

## Context / Ngữ cảnh

Hash Join xuất hiện trong query plan khi database nối hai input bằng cách build hash table trên một phía rồi probe bằng phía còn lại.

## Boundary / Ranh giới

### Nó là gì

Hash Join là join strategy phù hợp với equality join, thường hiệu quả khi không có index tốt hoặc khi cần join tập dữ liệu lớn.

### Nó không phải là gì

Hash Join không phải index. Nó là thuật toán execution tại thời điểm query chạy và có thể cần memory lớn để build hash table.

## Core Mechanism / Cơ chế lõi

Executor chọn build side nhỏ hơn, đọc rows và tạo hash table theo join key. Sau đó đọc probe side, hash join key và tìm match trong hash table để emit result.

## Project Role / Vai trò trong dự án

Dùng node này khi đọc EXPLAIN plan, debug join chậm, memory spill, row estimate sai hoặc so sánh hash join với nested loop/merge join.

## Output / Artifact nên có

- EXPLAIN/ANALYZE plan
- Build/probe side row count
- Hash table memory usage
- Spill/batch metric nếu có
- Join condition and selectivity

## Decision Checklist / Câu hỏi kiểm tra

- Join condition có phải equality không?
- Build side có đủ nhỏ để fit memory không?
- Row estimate có sát actual không?
- Hash join có spill ra disk không?
- Có index/nested loop tốt hơn cho case này không?

## Failure Modes / Cách nó gây lỗi

- Build side quá lớn làm spill ra disk.
- Row estimate sai làm planner chọn build side tệ.
- Memory setting thấp làm hash join chậm.
- Join key skew làm bucket không đều.
- Hash join dùng cho query trả rất ít row trong khi index lookup tốt hơn.

## Khi nào chưa cần hoặc dễ over-engineer

- Query nhỏ hoặc đã đủ nhanh thì chưa cần ép join strategy.
- Không nên disable/force join algorithm nếu chưa hiểu statistics và data distribution.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Query Plan]] vì hash join là node trong execution plan.
- [[Nested Loop Join]] vì đây là strategy join thường được so sánh.
- [[Page Cache]] vì spill/read pattern ảnh hưởng I/O.
- [[Performance Optimization]] vì join strategy ảnh hưởng query latency.

## Liên quan rộng

- Join algorithm
- Hash table
- Query execution

## Keywords / Từ khóa tìm kiếm

- Hash Join
- hash join
- hash table join
- build side
- probe side
- hash join spill
- hash join debugging

## Source trace

- PostgreSQL documentation
- Database System Concepts
