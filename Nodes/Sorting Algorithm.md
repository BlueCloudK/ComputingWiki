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

- [[Selection Sort]]
- [[Quicksort]]

## Nối mạnh

- [[Time Complexity]] vì sorting thường được so sánh bằng growth cost
- [[Data Structures]] vì structure ảnh hưởng sorting/access pattern

## Liên quan rộng

- Stable sort
- Merge sort

## Source trace

- Algorithms Map
- CLRS
