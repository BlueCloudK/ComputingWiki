# Searching Algorithm

Aliases: search algorithm, thuật toán tìm kiếm

Type: Computer Foundation

## Context / Ngữ cảnh

Searching Algorithm xuất hiện khi cần tìm phần tử, path hoặc state trong dữ liệu.

## Boundary / Ranh giới

### Nó là gì

Searching Algorithm là cách duyệt hoặc giảm search space để tìm item thỏa điều kiện.

### Nó không phải là gì

Nó không phải database query optimizer và không luôn là binary search.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là tận dụng order, index, hash, graph frontier hoặc heuristic để tìm nhanh hơn scan mù.

## Project Role / Vai trò trong dự án

Node này giúp chọn giữa linear scan, binary search, hash lookup hoặc graph search.

## Output / Artifact nên có

- Search strategy note: scan, binary, hash, graph, index
- Precondition note như sorted/indexed/visited set
- Complexity note cho lookup path quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Dữ liệu có sorted hoặc indexed chưa?
- Cần exact match, range search, nearest hay path?
- Search space có cycle hoặc duplicate không?

## Failure Modes / Cách nó gây lỗi

- Dùng binary search trên data chưa sorted
- Linear scan trên collection tăng nhanh
- Không ghi precondition nên caller dùng sai

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần phân tích nếu collection nhỏ và không tăng
- Dễ over-engineer nếu thêm index khi scan đơn giản đủ nhanh

## Gồm những gì

- [[Binary Search]]
- [[Graph Traversal]]

## Nối mạnh

- [[Data Structures]] vì structure quyết định cách search hiệu quả
- [[Big O Notation]] vì search cần so growth cost

## Liên quan rộng

- Lookup
- Path finding

## Keywords / Từ khóa tìm kiếm

- Searching Algorithm
- search algorithm
- lookup algorithm
- linear search
- binary search
- search complexity
- thuật toán tìm kiếm

## Source trace

- Algorithms Map
- CLRS
