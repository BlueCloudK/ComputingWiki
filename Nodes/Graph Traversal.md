# Graph Traversal

Aliases: graph search, duyệt đồ thị

Type: Computer Foundation

## Context / Ngữ cảnh

Graph Traversal xuất hiện khi cần đi qua node/edge để tìm reachability, path hoặc dependency.

## Boundary / Ranh giới

### Nó là gì

Graph Traversal là nhóm thuật toán duyệt graph theo frontier như BFS hoặc DFS.

### Nó không phải là gì

Nó không phải graph database, visualization, hay weighted shortest-path algorithm đầy đủ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là giữ visited set và frontier để tránh lặp rồi mở rộng neighbor theo strategy.

## Project Role / Vai trò trong dự án

Node này giúp debug dependency graph, routing, workflow và tree/graph algorithms.

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

- [[Breadth First Search]]
- [[Depth First Search]]

## Nối mạnh

- [[Graph]] vì traversal chạy trên graph
- [[Searching Algorithm]] vì traversal là search trên graph

## Liên quan rộng

- Reachability
- Dependency traversal

## Source trace

- Algorithms Map
