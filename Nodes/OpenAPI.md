# OpenAPI

Aliases: OpenAPI Specification, Swagger, đặc tả OpenAPI

Type: API / Integration

## Context / Ngữ cảnh

OpenAPI xuất hiện khi REST-like API cần được mô tả bằng machine-readable contract để generate docs, client, server stubs hoặc contract checks.

## Boundary / Ranh giới

### Nó là gì

OpenAPI là specification mô tả endpoint, method, parameter, request body, response, schema, auth và error shape của API.

### Nó không phải là gì

Nó không tự đảm bảo API implementation đúng, không thay thế security review, và không phù hợp cho mọi protocol/event flow.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là biến API contract thành schema có thể parse. Tooling dùng schema đó để validate, document, generate và detect breaking change.

## Project Role / Vai trò trong dự án

OpenAPI giúp client/server thống nhất contract và giảm mismatch. Nó đặc biệt hữu ích khi nhiều consumer hoặc team cùng dùng API.

## Output / Artifact nên có

- OpenAPI spec file
- Generated docs/client nếu phù hợp
- Contract validation hoặc breaking-change check

## Decision Checklist / Câu hỏi kiểm tra

- Spec có phản ánh implementation thật không?
- Error response và auth scheme có được mô tả không?
- Schema có required/optional rõ không?
- Spec có được kiểm tra trong CI không?
- Breaking change có bị detect trước release không?

## Failure Modes / Cách nó gây lỗi

- Spec stale làm consumer tin sai contract
- Chỉ document happy path, bỏ error/auth/edge case
- Generate client nhưng không kiểm tra compatibility
- Lạm dụng schema phức tạp làm API khó đọc

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần OpenAPI đầy đủ cho internal endpoint tạm thời
- Dễ over-engineer nếu spec chi tiết hơn nhiều so với API đang ổn định

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Contract]] vì OpenAPI là một dạng artifact của API contract
- [[API Versioning]] vì spec giúp quản lý version và deprecation
- [[Validation]] vì schema có thể hỗ trợ request/response validation

## Liên quan rộng

- API documentation
- Client generation
- Contract testing

## Keywords / Từ khóa tìm kiếm

- OpenAPI
- Swagger
- OpenAPI Specification
- API documentation
- API schema
- request schema
- response schema
- contract first API
- đặc tả OpenAPI
- tài liệu API

## Source trace

- OpenAPI Specification
