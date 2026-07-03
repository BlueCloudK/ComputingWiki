# Heap

Aliases: binary heap, heap

Type: Computer Foundation

## Context / Ngữ cảnh

Heap xuất hiện khi cần lấy phần tử min/max lặp lại nhanh mà không cần sort toàn bộ.

## Boundary / Ranh giới

### Nó là gì

Heap là data structure giữ heap property để truy cập priority cao nhất hoặc thấp nhất hiệu quả.

### Nó không phải là gì

Nó không phải memory heap của runtime và không phải sorted array.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là tree gần hoàn chỉnh biểu diễn bằng array, với bubble up/down để giữ heap property.

## Project Role / Vai trò trong dự án

Node này giúp dùng priority queue, scheduling và graph algorithms như Dijkstra đúng hơn.

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

- [[Priority Queue]] vì heap thường hiện thực priority queue
- [[Dijkstra Algorithm]] vì Dijkstra thường dùng priority queue/heap

## Liên quan rộng

- Scheduler
- Top-k

## Source trace

- CLRS
- Algorithms Map
