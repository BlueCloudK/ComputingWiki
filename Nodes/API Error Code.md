# API Error Code

Aliases: API Error Code, error code, API error code, mã lỗi API

Type: Backend Engineering

## Context / Ngữ cảnh

API Error Code là node bổ sung cho ComputingWiki về mã lỗi ổn định giúp client phân biệt failure case mà không parse message.

## Boundary / Ranh giới

### Nó là gì

API Error Code dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới mã lỗi ổn định giúp client phân biệt failure case mà không parse message.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của API Error Code là hiểu boundary, input/output, state và failure mode riêng của mã lỗi ổn định giúp client phân biệt failure case mà không parse message.

## Project Role / Vai trò trong dự án

API Error Code giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- API Error Code contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- API Error Code nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế API Error Code mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu API Error Code nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Error Response]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng API Error Code

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- API Error Code
- error code
- API error code
- mã lỗi API
- error
- code

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
