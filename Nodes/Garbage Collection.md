# Garbage Collection

Aliases: Garbage Collection, GC

Type: Programming Languages Deep

## Context / Ngữ cảnh

Garbage Collection xuất hiện trong language/runtime khi memory được quản lý tự động thay vì developer phải free object thủ công.

## Boundary / Ranh giới

### Nó là gì

Garbage Collection là cơ chế runtime phát hiện object/resource memory không còn cần thiết và thu hồi vùng nhớ đó để tái sử dụng.

### Nó không phải là gì

Garbage Collection không có nghĩa là không thể memory leak. Nếu object vẫn còn reachable từ root/reference graph, GC sẽ giữ nó lại dù app không còn cần nữa.

## Core Mechanism / Cơ chế lõi

Runtime theo dõi allocation và reference. Collector chạy theo thuật toán như tracing, generational, mark-sweep hoặc compacting để xác định object còn sống, thu hồi object chết và đôi khi di chuyển object để giảm fragmentation.

## Project Role / Vai trò trong dự án

Dùng node này khi debug memory leak, GC pause, heap growth, latency spike, object retention hoặc hiểu tradeoff giữa throughput và responsiveness của runtime.

## Output / Artifact nên có

- Heap profile
- GC log/metric
- Allocation hotspot
- Retained object path
- Before/after memory comparison

## Decision Checklist / Câu hỏi kiểm tra

- Heap tăng do leak hay do workload thật?
- Object nào đang giữ reference lâu nhất?
- GC pause có ảnh hưởng latency/UI không?
- Allocation hotspot nằm ở module nào?
- Runtime/collector đang dùng mode nào?

## Failure Modes / Cách nó gây lỗi

- Object còn referenced nên GC không thể thu hồi.
- GC pause làm request/UI lag.
- Allocation quá nhiều tạo áp lực GC.
- Tuning GC theo cảm tính không có metric.
- Finalizer/weak reference dùng sai làm behavior khó đoán.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ chưa có memory/latency issue chỉ cần hiểu mô hình tổng quát.
- Không nên tune GC trước khi có heap profile và GC metric.

## Gồm những gì

- [[Tracing Garbage Collector]]

## Nối mạnh

- [[Memory Management]] vì garbage collection là một mô hình quản lý memory.
- [[Runtime]] vì GC là trách nhiệm của runtime.
- [[Memory Leak]] vì leak trong managed runtime thường là object bị giữ reference.
- [[Tracing Garbage Collector]] vì tracing GC là nhóm collector phổ biến.

## Liên quan rộng

- Heap allocation
- GC pause
- Object retention
- Runtime performance

## Keywords / Từ khóa tìm kiếm

- Garbage Collection
- GC
- heap profile
- GC pause
- object retention
- memory leak
- garbage collection debugging

## Source trace

- Crafting Interpreters
- Engineering a Compiler
