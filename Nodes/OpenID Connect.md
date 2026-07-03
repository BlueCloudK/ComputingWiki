# OpenID Connect

Aliases: OpenID Connect, OIDC, đăng nhập OIDC

Type: Backend Engineering

## Context / Ngữ cảnh

OpenID Connect là node bổ sung cho ComputingWiki về identity layer trên OAuth2 để xác thực user và lấy ID token.

## Boundary / Ranh giới

### Nó là gì

OpenID Connect dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới identity layer trên OAuth2 để xác thực user và lấy ID token.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của OpenID Connect là hiểu boundary, input/output, state và failure mode riêng của identity layer trên OAuth2 để xác thực user và lấy ID token.

## Project Role / Vai trò trong dự án

OpenID Connect giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- OpenID Connect contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- OpenID Connect nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế OpenID Connect mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu OpenID Connect nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[OAuth2]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng OpenID Connect
- [[Authentication]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng OpenID Connect

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- OpenID Connect
- OIDC
- đăng nhập OIDC
- openid
- connect

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
