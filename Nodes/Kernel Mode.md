# Kernel Mode

Aliases: supervisor mode, chế độ kernel

Type: Operating System

## Context / Ngữ cảnh

Kernel Mode xuất hiện khi code OS cần quyền đầy đủ để quản lý hardware/resource.

## Boundary / Ranh giới

### Nó là gì

Kernel Mode là privileged execution mode cho kernel và một số driver.

### Nó không phải là gì

Nó không phải admin role của ứng dụng.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là cho phép instruction/resource bị cấm ở user mode.

## Project Role / Vai trò trong dự án

Hiểu kernel mode giúp lý giải crash/driver/security boundary.

## Output / Artifact nên có

- Privileged execution boundary
- Driver/kernel module risk note
- Crash/blast-radius note cho code privileged

## Decision Checklist / Câu hỏi kiểm tra

- Code nào thật sự chạy kernel mode?
- Có cần privileged access hay user-mode API đủ?
- Failure kernel mode có làm sập toàn host không?

## Failure Modes / Cách nó gây lỗi

- Driver bug làm crash toàn hệ thống
- Chạy code privileged để xử lý vấn đề có thể làm ở user mode
- Nhầm admin permission với kernel mode

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu không làm driver/OS/security thấp tầng
- Dễ over-engineer nếu app-level issue bị giải thích bằng kernel mode

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kernel]] vì kernel chạy chủ yếu ở kernel mode
- [[User Mode]] vì isolation đến từ phân tách mode

## Liên quan rộng

- Privilege separation

## Keywords / Từ khóa tìm kiếm

- Kernel Mode
- privileged mode
- kernel space
- hardware access
- interrupt handling
- chế độ kernel

## Source trace

- Operating Systems Map
