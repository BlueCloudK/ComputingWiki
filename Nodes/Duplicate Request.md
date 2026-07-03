# Duplicate Request

Aliases: duplicated request, double submit, request duplication, request bị gửi lặp

Type: Debugging / Failure Pattern

## Context / Ngữ cảnh

Duplicate Request xảy ra khi cùng một hành động bị gửi nhiều lần do user double click, retry, network timeout, refresh trang hoặc client/server chạy lại job.

## Boundary / Ranh giới

### Nó là gì

Nó là failure pattern ở boundary giữa client, API, queue và database, nơi một intent nghiệp vụ có thể tạo nhiều side effect.

### Nó không phải là gì

Nó không phải lúc nào cũng là lỗi frontend; retry policy, load balancer, worker hoặc webhook provider cũng có thể tạo request lặp.

## Core Mechanism / Cơ chế lõi

Hệ thống nhận nhiều request có cùng intent nhưng không có idempotency key, unique constraint, de-duplication hoặc transaction boundary đủ mạnh để gom chúng lại.

## Project Role / Vai trò trong dự án

Node này giúp debug lỗi tạo trùng order, thanh toán trùng, email gửi nhiều lần, job chạy lặp hoặc webhook xử lý lại.

## Output / Artifact nên có

- Idempotency decision cho endpoint/job quan trọng
- Request ID hoặc idempotency key trong log
- Unique constraint hoặc de-duplication rule cho side effect

## Decision Checklist / Câu hỏi kiểm tra

- Request này có tạo side effect không?
- Nếu client retry sau timeout, backend có nhận ra cùng một intent không?
- Có unique key nào chặn duplicate ở database không?
- Log có correlation ID để thấy request bị gửi lặp từ đâu không?

## Failure Modes / Cách nó gây lỗi

- Tạo nhiều payment/order vì endpoint không idempotent
- Webhook xử lý lại làm trạng thái nhảy sai
- Retry storm biến lỗi tạm thời thành nhiều side effect thật

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần cơ chế phức tạp cho read-only request
- Dễ over-engineer nếu mọi endpoint đều dùng idempotency store dù chỉ vài action có side effect

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Idempotency]] vì đây là control chính để xử lý duplicate request có side effect
- [[Retry]] vì retry thường là nguồn tạo request lặp

## Liên quan rộng

- API reliability
- Payment flow
- Queue processing
- Webhook handling

## Keywords / Từ khóa tìm kiếm

- Duplicate Request
- duplicated request
- double submit
- duplicate order
- idempotency key
- retry duplicate
- request bị gửi lặp
- gửi request hai lần

## Source trace

- Stripe API docs / idempotent requests
- Google SRE Book / handling overload and retries
