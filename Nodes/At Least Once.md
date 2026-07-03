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

- Delivery guarantee note
- Consumer idempotency/dedup plan
- Ack/commit timing rule

## Decision Checklist / Câu hỏi kiểm tra

- Consumer chịu duplicate bằng cách nào?
- Ack xảy ra trước hay sau side effect?
- Retry/backoff có làm overload không?

## Failure Modes / Cách nó gây lỗi

- Duplicate tạo order/payment/job hai lần
- Ack trước xử lý làm mất message
- Retry vô hạn đè downstream

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu message loss chấp nhận được hoặc flow read-only
- Dễ over-engineer nếu đòi exactly-once khi duplicate có thể xử lý đơn giản

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
