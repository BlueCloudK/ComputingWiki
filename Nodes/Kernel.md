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

- Kernel/user boundary note
- System call hoặc driver path liên quan
- Privilege/resource limit evidence khi debug

## Decision Checklist / Câu hỏi kiểm tra

- Operation này cần kernel service nào?
- Failure là app-level exception hay kernel/resource denial?
- Driver/kernel version có liên quan không?

## Failure Modes / Cách nó gây lỗi

- Debug app logic trong khi lỗi là kernel resource limit
- Assume kernel behavior giống nhau giữa OS/version
- Chạy privileged quá mức để né permission error

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần cho feature logic bình thường
- Dễ over-engineer nếu đào kernel internals trước khi có syscall/log/resource evidence

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[System Call]] vì process gọi kernel qua system call
- [[Kernel Mode]] vì kernel thường chạy ở privileged mode

## Liên quan rộng

- OS internals

## Keywords / Từ khóa tìm kiếm

- Kernel
- OS kernel
- privileged mode
- system call handler
- device driver interface
- kernel space
- nhân hệ điều hành

## Source trace

- Operating Systems Map
