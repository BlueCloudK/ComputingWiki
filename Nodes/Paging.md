# Paging

Aliases: memory paging, phân trang

Type: Operating System

## Context / Ngữ cảnh

Paging xuất hiện khi OS chia virtual memory thành page để map sang physical memory/storage.

## Boundary / Ranh giới

### Nó là gì

Paging là cơ chế memory management dùng page table để map virtual page sang frame.

### Nó không phải là gì

Nó không phải pagination API hoặc UI paging.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là page table mapping và page fault khi dữ liệu chưa sẵn.

## Project Role / Vai trò trong dự án

Node này giúp hiểu virtual memory, memory pressure và page replacement.

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

- [[Virtual Memory]] vì paging là cơ chế chính của virtual memory
- [[Page Replacement]] vì page replacement chọn page bị evict

## Liên quan rộng

- Memory management

## Source trace

- Operating Systems Map
