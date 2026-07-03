# Webhook

Aliases: callback webhook, webhook callback, HTTP callback, event callback, callback sự kiện

Type: API / Integration

## Context / Ngữ cảnh

Webhook xuất hiện khi một hệ thống cần báo sự kiện sang hệ thống khác bằng HTTP callback thay vì bên nhận phải polling liên tục.

## Boundary / Ranh giới

### Nó là gì

Webhook là integration pattern trong đó producer gửi request tới URL của consumer khi event xảy ra.

### Nó không phải là gì

Nó không phải API query thông thường, không đảm bảo delivery nếu không có retry/idempotency, và không thay thế message queue cho luồng phức tạp.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là event notification: đăng ký endpoint, ký/verify payload, gửi event, retry khi lỗi và xử lý trùng lặp an toàn.

## Project Role / Vai trò trong dự án

Webhook giúp integration gần realtime với third-party như payment, auth, repository hoặc notification service. Nó cần thiết kế kỹ vì consumer không kiểm soát thời điểm request đến.

## Output / Artifact nên có

- Webhook event contract
- Signature/verification rule
- Retry, timeout và idempotency behavior

## Decision Checklist / Câu hỏi kiểm tra

- Event nào được gửi và payload shape là gì?
- Consumer xác thực nguồn webhook thế nào?
- Retry có gây duplicate side effect không?
- Timeout và failure response được xử lý ra sao?
- Có cần lưu event raw để audit/replay không?

## Failure Modes / Cách nó gây lỗi

- Duplicate webhook tạo thanh toán/order hai lần
- Không verify signature nên nhận request giả
- Retry storm khi consumer lỗi kéo dài
- Payload thay đổi mà consumer không version/compatibility

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần webhook nếu polling đơn giản đủ và event không cần realtime
- Dễ over-engineer nếu dùng webhook cho workflow cần orchestration/state machine phức tạp

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Contract]] vì webhook cũng cần request/error/version contract rõ
- [[Idempotency]] vì webhook retry thường tạo duplicate event
- [[API Security]] vì webhook endpoint cần verify nguồn gửi và bảo vệ payload

## Liên quan rộng

- Event-driven integration
- Third-party callbacks
- Message delivery

## Keywords / Từ khóa tìm kiếm

- Webhook
- HTTP callback
- event callback
- webhook endpoint
- delivery retry
- signature verification
- event payload
- callback sự kiện
- endpoint webhook

## Source trace

- Microsoft REST API Guidelines
- OWASP API Security guidance
