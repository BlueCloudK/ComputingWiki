# User Mode

Aliases: user space, chế độ người dùng

Type: Operating System

## Context / Ngữ cảnh

User Mode là execution mode giới hạn quyền của process/app để bảo vệ hệ thống.

## Boundary / Ranh giới

### Nó là gì

User Mode là chế độ CPU/OS nơi app chạy với quyền hạn bị giới hạn.

### Nó không phải là gì

Nó không phải user account hay permission business.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là cấm instruction/resource nhạy cảm và bắt buộc gọi kernel qua system call.

## Project Role / Vai trò trong dự án

Node này giúp hiểu vì sao app không được truy cập device/memory tùy ý.

## Output / Artifact nên có

- User-space process boundary
- System call needed for privileged action
- Permission/isolation note khi app bị denied

## Decision Checklist / Câu hỏi kiểm tra

- Code này đang chạy user-space hay privileged context?
- Action bị chặn vì OS mode hay app authorization?
- Có syscall hoặc capability nào cần cấp rõ không?

## Failure Modes / Cách nó gây lỗi

- Nhầm user account với CPU user mode
- Cố truy cập device/memory trực tiếp từ app
- Escalate privilege thay vì sửa boundary đúng

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu không gặp OS/runtime permission issue
- Dễ over-engineer nếu mọi lỗi permission đều kéo về CPU mode

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[System Call]] vì user mode dùng system call để yêu cầu OS
- [[Kernel Mode]] vì hai mode tạo isolation boundary

## Liên quan rộng

- Process isolation

## Keywords / Từ khóa tìm kiếm

- User Mode
- user space
- unprivileged mode
- application process
- system call boundary
- chế độ người dùng

## Source trace

- Operating Systems Map
