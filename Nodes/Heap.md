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

- Heap invariant: min-heap/max-heap và comparator
- Operation note cho push, pop, peek, heapify
- Test cho priority ordering và duplicate priority

## Decision Checklist / Câu hỏi kiểm tra

- Cần lấy min/max lặp lại hay cần toàn bộ list sorted?
- Comparator có ổn định khi priority bằng nhau không?
- Có cần update/delete arbitrary element không?

## Failure Modes / Cách nó gây lỗi

- Nhầm heap với sorted array nên iterate ra thứ tự sai
- Comparator sai làm pop priority sai
- Update priority mà không re-heapify

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần heap nếu chỉ sort một lần
- Dễ over-engineer nếu collection nhỏ hoặc priority không có ý nghĩa thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Priority Queue]] vì heap thường hiện thực priority queue
- [[Dijkstra Algorithm]] vì Dijkstra thường dùng priority queue/heap

## Liên quan rộng

- Scheduler
- Top-k

## Keywords / Từ khóa tìm kiếm

- Heap
- binary heap
- min heap
- max heap
- heap property
- priority queue implementation
- cây heap

## Source trace

- CLRS
- Algorithms Map
