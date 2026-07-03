# Interrupt

Aliases: hardware interrupt, ngắt

Type: Operating System

## Context / Ngữ cảnh

Interrupt xuất hiện khi hardware/timer/event cần CPU dừng luồng hiện tại để xử lý sự kiện.

## Boundary / Ranh giới

### Nó là gì

Interrupt là signal chuyển control tới handler để xử lý event ưu tiên.

### Nó không phải là gì

Nó không phải exception business hay callback app.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là CPU lưu context, chạy interrupt handler rồi quay lại execution.

## Project Role / Vai trò trong dự án

Node này giúp hiểu IO, scheduling, latency thấp tầng và device interaction.

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

- [[Device Driver]] vì driver thường xử lý interrupt từ thiết bị
- [[Scheduling]] vì timer interrupt hỗ trợ preemption

## Liên quan rộng

- Hardware events

## Source trace

- Operating Systems Map
