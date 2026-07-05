# Tracing Garbage Collector

Aliases: Tracing Garbage Collector, tracing GC

Type: Programming Languages Deep

## Context / Ngữ cảnh

Tracing Garbage Collector xuất hiện trong runtime/language implementation khi memory không được free thủ công mà runtime cần tự tìm object còn sống và thu hồi object không còn reachable.

## Boundary / Ranh giới

### Nó là gì

Tracing Garbage Collector là cơ chế GC bắt đầu từ tập root, đi theo reference graph để mark object còn reachable, rồi thu hồi phần heap không được mark.

### Nó không phải là gì

Tracing Garbage Collector không phải reference counting. Nó không giảm counter ngay khi reference biến mất mà chạy theo phase/collection cycle.

## Core Mechanism / Cơ chế lõi

GC xác định root như stack, global, register hoặc runtime handle. Từ root, collector trace qua object reference, mark object còn sống, sau đó sweep/compact/copy object chết tùy thuật toán.

## Project Role / Vai trò trong dự án

Dùng node này khi hiểu runtime memory, debug pause time, memory leak trong managed language, object retention hoặc tradeoff giữa throughput và latency.

## Output / Artifact nên có

- Root set model
- Heap/object graph note
- Collection algorithm note
- Pause/latency metric
- Leak/retention investigation

## Decision Checklist / Câu hỏi kiểm tra

- Root nào đang giữ object sống?
- Object bị leak thật hay chỉ bị retained lâu?
- GC pause có ảnh hưởng latency không?
- Collector có compact/copy không?
- Metric heap before/after collection ra sao?

## Failure Modes / Cách nó gây lỗi

- Object còn reachable ngoài ý muốn nên không được collect.
- Pause time cao làm request/UI lag.
- Finalizer/weak reference dùng sai làm behavior khó đoán.
- Heap fragmentation nếu không compact.
- Tuning GC theo cảm tính mà không có metric.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ chưa có memory/latency issue có thể chỉ cần biết cơ chế tổng quát.
- Không nên tune GC trước khi có heap profile và pause metric.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Memory Management]] vì tracing GC là cơ chế quản lý memory tự động.
- [[Runtime]] vì GC chạy trong runtime.
- [[Memory Leak]] vì object retained qua root/reference graph gây leak trong managed language.
- [[Performance Optimization]] vì GC pause/throughput ảnh hưởng performance.

## Liên quan rộng

- Mark and sweep
- Heap compaction
- Runtime implementation

## Keywords / Từ khóa tìm kiếm

- Tracing Garbage Collector
- tracing GC
- mark and sweep
- root set
- object graph
- GC pause
- heap retention
- tracing GC debugging

## Source trace

- Crafting Interpreters
- Engineering a Compiler
