# Depth First Search

Aliases: DFS, tìm kiếm theo chiều sâu

Type: Computer Foundation

## Context / Ngữ cảnh

Depth First Search xuất hiện khi cần đi sâu theo một nhánh graph/tree trước khi quay lại nhánh khác.

## Boundary / Ranh giới

### Nó là gì

Depth First Search là graph traversal dùng stack hoặc recursion để mở rộng node sâu trước.

### Nó không phải là gì

Nó không phải BFS và không đảm bảo shortest path trong graph không trọng số.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là visit node, đánh dấu visited, rồi đệ quy/push neighbor theo stack discipline.

## Project Role / Vai trò trong dự án

Node này hữu ích cho cycle detection, topological reasoning, connected components và backtracking.

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

- [[Graph Traversal]] vì DFS là một traversal strategy
- [[Recursion]] vì DFS thường được viết bằng recursion

## Liên quan rộng

- Backtracking
- Cycle detection

## Source trace

- Algorithms Map
