# Idempotency

Aliases: idempotent operation, tính lặp an toàn

Type: API / Integration

## Context / Ngữ cảnh

Idempotency xuất hiện khi cùng một request/event có thể được gửi lại do retry, timeout, webhook duplicate hoặc network uncertainty.

## Boundary / Ranh giới

### Nó là gì

Idempotency là tính chất một operation có thể chạy nhiều lần với cùng intent mà không tạo thêm side effect ngoài ý muốn.

### Nó không phải là gì

Nó không có nghĩa operation không thay đổi state, không thay thế transaction, và không tự xảy ra nếu không thiết kế key/state handling.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là nhận diện intent trùng lặp bằng idempotency key, request id hoặc natural key rồi trả cùng kết quả hoặc bỏ qua side effect đã thực hiện.

## Project Role / Vai trò trong dự án

Idempotency bảo vệ payment, order, webhook, job processing và API retry khỏi tạo duplicate record hoặc double charge.

## Output / Artifact nên có

- Idempotency key policy
- Storage/TTL cho request result hoặc processed event
- Test case cho retry, timeout và duplicate delivery

## Decision Checklist / Câu hỏi kiểm tra

- Operation này có thể được client/retry gửi lại không?
- Side effect nào không được xảy ra hai lần?
- Key nào đại diện cho cùng intent?
- Khi duplicate đến, trả response cũ hay current state?
- TTL/cleanup cho idempotency record là gì?

## Failure Modes / Cách nó gây lỗi

- Retry tạo payment/order/job hai lần
- Key chọn sai làm request khác nhau bị coi là trùng
- Lưu idempotency record không atomically với side effect
- TTL quá ngắn khiến retry muộn tạo side effect mới

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần idempotency phức tạp cho read-only request hoặc action không side effect
- Dễ over-engineer nếu mọi endpoint đều cần key dù không có retry/duplicate risk

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Webhook]] vì webhook delivery thường retry và duplicate
- [[API Contract]] vì idempotency key/behavior phải là một phần contract
- [[Transaction]] vì side effect và idempotency record cần consistency

## Liên quan rộng

- Retry safety
- Payment systems
- Job processing

## Source trace

- Designing Data-Intensive Applications
- Microsoft REST API Guidelines
