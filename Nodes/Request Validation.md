# Request Validation

Aliases: Request Validation, request validation, validate request, kiểm tra request

Type: Backend Engineering

## Context / Ngữ cảnh

Request Validation là node bổ sung cho ComputingWiki về kiểm tra shape, type và rule của input trước khi xử lý nghiệp vụ.

## Boundary / Ranh giới

### Nó là gì

Request Validation dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới kiểm tra shape, type và rule của input trước khi xử lý nghiệp vụ.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Request Validation là hiểu boundary, input/output, state và failure mode riêng của kiểm tra shape, type và rule của input trước khi xử lý nghiệp vụ.

## Project Role / Vai trò trong dự án

Request Validation giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Request Validation contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Request Validation nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Request Validation mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Request Validation nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Input Validation]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Request Validation
- [[API Contract]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Request Validation

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Request Validation
- request validation
- validate request
- kiểm tra request
- request
- validation

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
