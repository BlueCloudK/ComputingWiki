# Refresh Token

Aliases: Refresh Token, refresh token, token làm mới, đổi access token

Type: Backend Engineering

## Context / Ngữ cảnh

Refresh Token là node bổ sung cho ComputingWiki về token dài hạn dùng để lấy access token mới.

## Boundary / Ranh giới

### Nó là gì

Refresh Token dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới token dài hạn dùng để lấy access token mới.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Refresh Token là hiểu boundary, input/output, state và failure mode riêng của token dài hạn dùng để lấy access token mới.

## Project Role / Vai trò trong dự án

Refresh Token giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Refresh Token contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Refresh Token nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Refresh Token mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Refresh Token nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Token Refresh]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Refresh Token
- [[OAuth2]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Refresh Token

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Refresh Token
- refresh token
- token làm mới
- đổi access token
- refresh
- token

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
