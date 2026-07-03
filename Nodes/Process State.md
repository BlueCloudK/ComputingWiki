# Process State

Aliases: process lifecycle state, trạng thái tiến trình

Type: Operating System

## Context / Ngữ cảnh

Process State xuất hiện khi cần hiểu process đang running, ready, blocked, waiting hay terminated.

## Boundary / Ranh giới

### Nó là gì

Process State là trạng thái lifecycle của process trong scheduler/OS.

### Nó không phải là gì

Nó không phải state domain của app.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là OS chuyển process giữa state theo CPU, IO và event.

## Project Role / Vai trò trong dự án

Node này giúp debug hang, blocked process, resource wait và scheduling behavior.

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

- [[Process]] vì state là lifecycle của process
- [[Scheduling]] vì scheduler dựa trên state để chọn process

## Liên quan rộng

- Runtime debugging

## Source trace

- Operating Systems Map
