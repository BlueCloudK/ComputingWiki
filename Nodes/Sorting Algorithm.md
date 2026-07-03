# Sorting Algorithm

Aliases: sorting, thuật toán sắp xếp

Type: Computer Foundation

## Context / Ngữ cảnh

Sorting Algorithm xuất hiện khi dữ liệu cần được đưa về một thứ tự để search, display, group hoặc xử lý tiếp.

## Boundary / Ranh giới

### Nó là gì

Sorting Algorithm là thuật toán sắp xếp phần tử theo comparator hoặc key.

### Nó không phải là gì

Nó không phải data structure và không đảm bảo query nhanh nếu access pattern cần index.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là so sánh, hoán đổi, chia nhỏ hoặc merge để tạo order với time/space trade-off khác nhau.

## Project Role / Vai trò trong dự án

Node này giúp chọn library/API sort hoặc thuật toán phù hợp khi input lớn, stability hoặc memory quan trọng.

## Output / Artifact nên có

- Sort key/comparator note
- Stability requirement nếu output cần giữ thứ tự tương đương
- Complexity note cho input size lớn

## Decision Checklist / Câu hỏi kiểm tra

- Có cần stable sort không?
- Comparator có total order và deterministic không?
- Input size có làm O(n^2) nguy hiểm không?

## Failure Modes / Cách nó gây lỗi

- Comparator không transitive làm sort sai/ngẫu nhiên
- Dùng sort đắt trên hot path trong khi cần index
- Mất thứ tự cũ vì không để ý stability

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tự chọn thuật toán nếu library sort đã đủ
- Dễ over-engineer nếu tối ưu sorting không nằm critical path

## Gồm những gì

- [[Selection Sort]]
- [[Quicksort]]

## Nối mạnh

- [[Time Complexity]] vì sorting thường được so sánh bằng growth cost
- [[Data Structures]] vì structure ảnh hưởng sorting/access pattern

## Liên quan rộng

- Stable sort
- Merge sort

## Keywords / Từ khóa tìm kiếm

- Sorting Algorithm
- sorting
- thuật toán sắp xếp
- algorithm
- Computer Foundation
- thuật toán
- cấu trúc dữ liệu

## Source trace

- Algorithms Map
- CLRS
