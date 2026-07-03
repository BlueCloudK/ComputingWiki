# Webhook Signature

Aliases: Webhook Signature, webhook signature, HMAC webhook, xác minh webhook

Type: Backend Engineering

## Context / Ngữ cảnh

Webhook Signature là node bổ sung cho ComputingWiki về chữ ký giúp receiver xác minh webhook thật sự đến từ provider.

## Boundary / Ranh giới

### Nó là gì

Webhook Signature dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới chữ ký giúp receiver xác minh webhook thật sự đến từ provider.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Webhook Signature là hiểu boundary, input/output, state và failure mode riêng của chữ ký giúp receiver xác minh webhook thật sự đến từ provider.

## Project Role / Vai trò trong dự án

Webhook Signature giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Webhook Signature contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Webhook Signature nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Webhook Signature mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Webhook Signature nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Webhook]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Webhook Signature
- [[API Security]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Webhook Signature

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Webhook Signature
- webhook signature
- HMAC webhook
- xác minh webhook
- webhook
- signature

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
