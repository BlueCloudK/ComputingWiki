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

- Traversal strategy: BFS, DFS hoặc custom frontier
- Visited/cycle rule
- Reachability/path test case

## Decision Checklist / Câu hỏi kiểm tra

- Graph có cycle hoặc multi-edge không?
- Cần shortest path, reachability hay ordering?
- Visited key là node id, object identity hay state tuple?

## Failure Modes / Cách nó gây lỗi

- Quên visited gây infinite loop
- Dùng DFS khi cần shortest path unweighted
- Traversal order không deterministic làm test flaky

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần graph traversal nếu data thật chỉ là list/tree nhỏ
- Dễ over-engineer nếu biến relation đơn giản thành graph model phức tạp

## Gồm những gì

- [[Breadth First Search]]
- [[Depth First Search]]

## Nối mạnh

- [[Graph]] vì traversal chạy trên graph
- [[Searching Algorithm]] vì traversal là search trên graph

## Liên quan rộng

- Reachability
- Dependency traversal

## Keywords / Từ khóa tìm kiếm

- Graph Traversal
- graph search
- DFS
- BFS
- visited set
- traverse graph
- duyệt đồ thị

## Source trace

- Algorithms Map
