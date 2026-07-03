# Kernel

Aliases: operating system kernel, nhân hệ điều hành

Type: Operating System

## Context / Ngữ cảnh

Kernel là lõi OS quản lý tài nguyên và cung cấp privileged services cho process.

## Boundary / Ranh giới

### Nó là gì

Kernel là phần OS chạy với quyền cao để quản lý CPU, memory, device và system calls.

### Nó không phải là gì

Nó không phải toàn bộ OS UI/tooling.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là chạy ở privileged mode để arbitrate resource và expose controlled interface.

## Project Role / Vai trò trong dự án

Hiểu kernel giúp debug permission, performance, driver và system-call level issues.

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

- [[System Call]] vì process gọi kernel qua system call
- [[Kernel Mode]] vì kernel thường chạy ở privileged mode

## Liên quan rộng

- OS internals

## Source trace

- Operating Systems Map
