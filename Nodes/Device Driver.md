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

- Driver/device/version note
- IO path và OS/hardware boundary
- Rollback/update plan nếu driver gây lỗi

## Decision Checklist / Câu hỏi kiểm tra

- Lỗi có phụ thuộc device model hoặc driver version không?
- Driver log/event viewer có signal gì?
- Update driver có thay đổi behavior không?

## Failure Modes / Cách nó gây lỗi

- App bị blamed trong khi driver crash
- Driver mismatch làm device/network/storage chập chờn
- Update driver không có rollback plan

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu app không chạm hardware/device-specific path
- Dễ over-engineer nếu mọi IO bug đều đổ cho driver trước khi có evidence

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Input Output]] vì driver nằm ở boundary IO
- [[Interrupt]] vì device thường báo event qua interrupt

## Liên quan rộng

- Hardware abstraction

## Source trace

- Operating Systems Map
