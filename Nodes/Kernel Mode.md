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

- [[Kernel]] vì kernel chạy chủ yếu ở kernel mode
- [[User Mode]] vì isolation đến từ phân tách mode

## Liên quan rộng

- Privilege separation

## Source trace

- Operating Systems Map
