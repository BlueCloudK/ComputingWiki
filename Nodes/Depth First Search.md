# Depth First Search

Aliases: DFS, tìm kiếm theo chiều sâu, depth-first traversal, duyệt sâu

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

- DFS traversal rule và neighbor ordering
- Recursion/stack depth note
- Cycle detection hoặc backtracking test

## Decision Checklist / Câu hỏi kiểm tra

- Graph/tree có độ sâu tối đa bao nhiêu?
- Visited được đánh dấu trước hay sau khi explore?
- Có cần path reconstruction hoặc chỉ cần visit?

## Failure Modes / Cách nó gây lỗi

- Stack overflow với graph sâu
- Đánh dấu visited sai làm bỏ sót node hoặc lặp vô hạn
- Dùng DFS rồi tưởng có shortest path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần DFS nếu BFS/library traversal đã rõ
- Dễ over-engineer nếu viết DFS custom cho structure nhỏ không có cycle

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Graph Traversal]] vì DFS là một traversal strategy
- [[Recursion]] vì DFS thường được viết bằng recursion

## Liên quan rộng

- Backtracking
- Cycle detection

## Keywords / Từ khóa tìm kiếm

- Depth First Search
- DFS
- recursive graph search
- stack traversal
- visited set
- tree traversal
- duyệt sâu

## Source trace

- Algorithms Map
