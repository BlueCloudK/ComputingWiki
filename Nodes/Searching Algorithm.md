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

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

## Gồm những gì

- [[Binary Search]]
- [[Graph Traversal]]

## Nối mạnh

- [[Data Structures]] vì structure quyết định cách search hiệu quả
- [[Big O Notation]] vì search cần so growth cost

## Liên quan rộng

- Lookup
- Path finding

## Source trace

- Algorithms Map
- CLRS
