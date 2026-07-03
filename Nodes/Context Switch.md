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

- [[Thread]] vì thread switching là dạng context switch
- [[Scheduling]] vì scheduler quyết định switch

## Liên quan rộng

- Concurrency overhead

## Source trace

- Operating Systems Map
