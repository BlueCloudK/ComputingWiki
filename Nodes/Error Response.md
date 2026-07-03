# Error Response

Aliases: Error Response, error response, API error, response lỗi

Type: Backend Engineering

## Context / Ngữ cảnh

Error Response là node bổ sung cho ComputingWiki về response lỗi có status code, error code và message đủ cho client xử lý.

## Boundary / Ranh giới

### Nó là gì

Error Response dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới response lỗi có status code, error code và message đủ cho client xử lý.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Error Response là hiểu boundary, input/output, state và failure mode riêng của response lỗi có status code, error code và message đủ cho client xử lý.

## Project Role / Vai trò trong dự án

Error Response giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Error Response contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Error Response nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Error Response mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Error Response nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Response]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Error Response
- [[API Contract]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Error Response

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Error Response
- error response
- API error
- response lỗi
- error
- response

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
