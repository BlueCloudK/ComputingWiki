# Context Switch

Aliases: task switch, chuyển ngữ cảnh

Type: Operating System

## Context / Ngữ cảnh

Context Switch xuất hiện khi CPU chuyển từ process/thread này sang process/thread khác.

## Boundary / Ranh giới

### Nó là gì

Context Switch là việc lưu execution context hiện tại và restore context khác.

### Nó không phải là gì

Nó không phải switching business context.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là save/restore register, program counter, stack và scheduler metadata.

## Project Role / Vai trò trong dự án

Node này giúp hiểu overhead concurrency, scheduling và performance khi quá nhiều thread/task.

## Output / Artifact nên có

- Context-switch metric hoặc trace
- Thread/process count note
- Concurrency design note khi overhead đáng kể

## Decision Checklist / Câu hỏi kiểm tra

- Có quá nhiều thread/process active không?
- Switch rate có tăng cùng latency không?
- Workload CPU-bound hay IO-bound?

## Failure Modes / Cách nó gây lỗi

- Tăng concurrency làm context switch overhead cao hơn throughput
- Lock contention khiến switch nhiều nhưng work ít
- Nhầm context switch với application context

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu concurrency thấp hoặc không có performance symptom
- Dễ over-engineer nếu giảm thread trước khi đo switch/CPU evidence

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Thread]] vì thread switching là dạng context switch
- [[Scheduling]] vì scheduler quyết định switch

## Liên quan rộng

- Concurrency overhead

## Source trace

- Operating Systems Map
