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

- [[System Call]] vì user mode dùng system call để yêu cầu OS
- [[Kernel Mode]] vì hai mode tạo isolation boundary

## Liên quan rộng

- Process isolation

## Source trace

- Operating Systems Map
