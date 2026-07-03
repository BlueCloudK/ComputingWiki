# Priority Queue

Aliases: priority queue, hàng đợi ưu tiên

Type: Computer Foundation

## Context / Ngữ cảnh

Priority Queue xuất hiện khi work/item cần xử lý theo priority thay vì FIFO.

## Boundary / Ranh giới

### Nó là gì

Priority Queue là abstract data type cho phép insert item và lấy item có priority cao nhất/thấp nhất.

### Nó không phải là gì

Nó không phải queue FIFO thường và không quy định implementation duy nhất.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là lưu priority cùng item và duy trì cấu trúc để pop theo priority hiệu quả.

## Project Role / Vai trò trong dự án

Node này giúp scheduling, graph algorithms, job processing và top-k queries.

## Output / Artifact nên có

- Priority definition và tie-break rule
- Queue operation note: enqueue, peek, dequeue, update
- Test cho ordering khi priority bằng nhau

## Decision Checklist / Câu hỏi kiểm tra

- Priority lấy từ field nào và có thể đổi không?
- Tie-break cần deterministic không?
- Có starvation nếu item priority thấp chờ mãi không?

## Failure Modes / Cách nó gây lỗi

- Priority stale khiến job xử lý sai thứ tự
- Tie-break không rõ làm output thay đổi mỗi lần chạy
- Dùng priority queue khi FIFO mới đúng business

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu FIFO đủ
- Dễ over-engineer nếu thêm priority nhưng không có rule business rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Heap]] vì heap là implementation phổ biến
- [[Queue]] vì priority queue biến thể từ queue theo policy

## Liên quan rộng

- Scheduling
- Top-k

## Source trace

- CLRS
- Algorithms Map
