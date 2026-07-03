# OAuth2

Aliases: OAuth2, OAuth 2.0, ủy quyền OAuth

Type: Backend Engineering

## Context / Ngữ cảnh

OAuth2 là node bổ sung cho ComputingWiki về authorization framework cho phép app truy cập resource thay mặt user.

## Boundary / Ranh giới

### Nó là gì

OAuth2 dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới authorization framework cho phép app truy cập resource thay mặt user.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của OAuth2 là hiểu boundary, input/output, state và failure mode riêng của authorization framework cho phép app truy cập resource thay mặt user.

## Project Role / Vai trò trong dự án

OAuth2 giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- OAuth2 contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- OAuth2 nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế OAuth2 mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu OAuth2 nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Access Token]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng OAuth2
- [[Authorization]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng OAuth2

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- OAuth2
- OAuth 2.0
- ủy quyền OAuth
- oauth2

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
