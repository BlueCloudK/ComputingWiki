# Space Complexity

Aliases: memory cost, độ phức tạp bộ nhớ

Type: Computer Foundation

## Context / Ngữ cảnh

Space Complexity xuất hiện khi memory usage tăng theo input và có thể gây OOM, GC pressure hoặc cost.

## Boundary / Ranh giới

### Nó là gì

Space Complexity mô tả lượng memory phụ mà algorithm/data structure cần theo input size.

### Nó không phải là gì

Nó không phải memory leak analysis và không thay thế profiling.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đếm extra storage như arrays, recursion stack, cache hoặc intermediate result.

## Project Role / Vai trò trong dự án

Node này giúp chọn giữa memory-heavy speedup và low-memory algorithm.

## Output / Artifact nên có

- Extra-memory estimate cho structure/intermediate result
- Recursion stack hoặc cache-size note
- Memory pressure test nếu input lớn

## Decision Checklist / Câu hỏi kiểm tra

- Algorithm cần extra storage theo n là gì?
- Recursion depth có tạo stack risk không?
- Cache/intermediate có lifecycle và eviction không?

## Failure Modes / Cách nó gây lỗi

- Tối ưu time bằng cache không bound
- Bỏ qua recursion stack trong input sâu
- Copy collection lớn nhiều lần trong pipeline

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu memory dư và input nhỏ
- Dễ over-engineer nếu giảm memory làm code phức tạp trong khi bottleneck là IO

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Memory Model]] vì memory behavior ảnh hưởng runtime
- [[Big O Notation]] vì space cũng dùng growth notation

## Liên quan rộng

- Memory pressure
- Algorithm analysis

## Keywords / Từ khóa tìm kiếm

- Space Complexity
- memory complexity
- auxiliary space
- Big O space
- memory usage
- độ phức tạp bộ nhớ

## Source trace

- Algorithms Map
- CLRS
