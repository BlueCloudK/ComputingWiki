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

- Chưa tách nhánh

## Nối mạnh

- [[Memory Model]] vì memory behavior ảnh hưởng runtime
- [[Big O Notation]] vì space cũng dùng growth notation

## Liên quan rộng

- Memory pressure
- Algorithm analysis

## Source trace

- Algorithms Map
- CLRS
