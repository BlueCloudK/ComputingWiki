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

- [[Heap]] vì heap là implementation phổ biến
- [[Queue]] vì priority queue biến thể từ queue theo policy

## Liên quan rộng

- Scheduling
- Top-k

## Source trace

- CLRS
- Algorithms Map
