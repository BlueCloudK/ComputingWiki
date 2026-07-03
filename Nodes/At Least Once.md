# At Least Once

Aliases: at-least-once delivery, ít nhất một lần

Type: Data / Database

## Context / Ngữ cảnh

At Least Once xuất hiện khi hệ thống ưu tiên không mất message/event và chấp nhận duplicate.

## Boundary / Ranh giới

### Nó là gì

At Least Once là guarantee rằng message được xử lý một hoặc nhiều lần nếu retry xảy ra.

### Nó không phải là gì

Nó không đảm bảo không duplicate và không đủ cho side effect không idempotent.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là retry cho tới khi có ack/commit; failure giữa xử lý và ack có thể tạo duplicate.

## Project Role / Vai trò trong dự án

Node này giúp thiết kế consumer phải chịu duplicate an toàn.

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

- [[Idempotency]] vì at-least-once gần như bắt buộc xử lý duplicate
- [[Backpressure]] vì retry có thể làm overload

## Liên quan rộng

- Message delivery
- Consumer design

## Source trace

- DDIA Ch11
