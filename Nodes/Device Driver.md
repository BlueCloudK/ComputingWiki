# Device Driver

Aliases: driver, trình điều khiển thiết bị

Type: Operating System

## Context / Ngữ cảnh

Device Driver xuất hiện khi OS cần giao tiếp với hardware hoặc virtual device.

## Boundary / Ranh giới

### Nó là gì

Device Driver là software bridge giữa OS và device-specific protocol.

### Nó không phải là gì

Nó không phải application adapter/pattern.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là expose interface cho OS/app và xử lý command/event đặc thù của device.

## Project Role / Vai trò trong dự án

Node này giúp debug IO, GPU, network adapter, storage và hardware-dependent bugs.

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

- [[Input Output]] vì driver nằm ở boundary IO
- [[Interrupt]] vì device thường báo event qua interrupt

## Liên quan rộng

- Hardware abstraction

## Source trace

- Operating Systems Map
