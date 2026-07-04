# OpenAPI

Aliases: OpenAPI Specification, Swagger, đặc tả OpenAPI

Type: API / Integration

## Context / Ngữ cảnh

OpenAPI xuất hiện khi REST-like API cần được mô tả bằng contract machine-readable để generate docs, client SDK, server stub, mock server, validation hoặc breaking-change check. Nó hữu ích khi API có nhiều consumer, nhiều team hoặc cần documentation luôn khớp implementation.

## Boundary / Ranh giới

### Nó là gì

OpenAPI là specification mô tả API surface: endpoint, method, path/query/header parameter, request body, response schema, status code, auth scheme, error shape và metadata. Spec thường ở dạng YAML/JSON và được tool như Swagger UI, codegen, validator hoặc contract test đọc được.

### Nó không phải là gì

OpenAPI không tự đảm bảo implementation đúng. Nếu spec stale hoặc chỉ mô tả happy path, consumer vẫn tích hợp sai. OpenAPI cũng không thay thế security review, authorization design, rate limit policy hoặc tài liệu nghiệp vụ; nó chỉ mô tả interface kỹ thuật của API.

## Core Mechanism / Cơ chế lõi

OpenAPI biến API contract thành schema có thể parse. Tooling dùng schema để render docs, validate request/response, generate client, mock API, compare breaking change và hỗ trợ contract-first hoặc code-first workflow. Giá trị thật đến từ việc spec được version, review và kiểm tra trong CI.

## Project Role / Vai trò trong dự án

OpenAPI giúp frontend/backend, mobile/backend hoặc third-party integration thống nhất contract trước khi code tích hợp sâu. Khi API thay đổi, spec là artifact để review field required/optional, error response, auth scheme, versioning và backward compatibility.

## Output / Artifact nên có

- OpenAPI spec file: `openapi.yaml` hoặc generated spec có source rõ
- Swagger/Redoc documentation nếu API cần người đọc
- Request/response schema cho success và failure path
- Auth/security scheme, scope/permission note nếu có
- CI check: lint spec, compare breaking change, optionally validate response contract
- Generated client/server stub nếu phù hợp workflow

## Decision Checklist / Câu hỏi kiểm tra

- Spec có phản ánh implementation thật không, hay đã stale?
- Mỗi endpoint có mô tả status code success và error quan trọng không?
- Request/response schema có required/optional/nullable rõ không?
- Auth scheme, bearer token, cookie/session hoặc OAuth scope có được mô tả không?
- Breaking change có bị detect trước release không?
- Spec được sinh từ code, code từ spec, hay maintain thủ công?
- Consumer có dùng spec để generate client/test không, hay chỉ đọc docs bằng mắt?

## Failure Modes / Cách nó gây lỗi

- Spec stale làm consumer tin sai contract và lỗi chỉ lộ khi tích hợp thật.
- Chỉ document 200 OK, bỏ 400/401/403/404/409/500 khiến client xử lý lỗi sai.
- Required/nullable/enum mô tả sai làm generated client reject dữ liệu hợp lệ hoặc bỏ sót lỗi.
- Auth/security scheme thiếu làm endpoint nhạy cảm bị hiểu là public.
- Generate client nhưng không version spec làm client cũ bị breaking change âm thầm.
- Spec quá generic hoặc lạm dụng `object` tự do làm mất giá trị kiểm chứng contract.

## Khi nào chưa cần hoặc dễ over-engineer

- Endpoint thử nghiệm nội bộ ngắn hạn có thể dùng README/test contract nhẹ trước.
- Không nên duy trì OpenAPI thủ công nếu team không có quy trình giữ spec khớp code.
- Không nên tạo schema quá phức tạp nếu API chưa ổn định và chưa có consumer thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Contract]] vì OpenAPI là artifact phổ biến để mô tả API contract.
- [[API Endpoint]] vì OpenAPI mô tả từng operation theo method/path.
- [[API Versioning]] vì spec giúp quản lý version, deprecation và breaking change.
- [[Validation]] vì schema có thể hỗ trợ request/response validation.
- [[Integration Test]] vì spec có thể làm nền cho contract/integration tests.

## Liên quan rộng

- API documentation
- Client generation
- Contract testing
- Backend frontend handoff

## Keywords / Từ khóa tìm kiếm

- OpenAPI
- Swagger
- OpenAPI Specification
- đặc tả OpenAPI
- API documentation
- API schema
- request schema
- response schema
- contract first API
- code first API
- Swagger UI
- OpenAPI generator
- breaking change detection
- contract validation
- tài liệu API

## Source trace

- OpenAPI Specification
- Swagger documentation
