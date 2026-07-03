# Outbox Pattern

Aliases: Outbox Pattern, outbox pattern, transactional outbox, mẫu outbox

Type: Backend Engineering

## Context / Ngữ cảnh

Outbox Pattern là node bổ sung cho ComputingWiki về pattern ghi event vào database cùng transaction rồi publish sau để tránh mất event.

## Boundary / Ranh giới

### Nó là gì

Outbox Pattern dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới pattern ghi event vào database cùng transaction rồi publish sau để tránh mất event.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Outbox Pattern là hiểu boundary, input/output, state và failure mode riêng của pattern ghi event vào database cùng transaction rồi publish sau để tránh mất event.

## Project Role / Vai trò trong dự án

Outbox Pattern giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Outbox Pattern contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Outbox Pattern nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Outbox Pattern mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Outbox Pattern nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Domain Event]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Outbox Pattern
- [[Transaction]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Outbox Pattern

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Outbox Pattern
- outbox pattern
- transactional outbox
- mẫu outbox
- outbox
- pattern

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
