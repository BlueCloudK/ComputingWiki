# FastAPI

Aliases: FastAPI, Python API framework

Type: Framework / Backend

## Context / Ngữ cảnh

FastAPI là Python framework để xây API dựa trên type hints, ASGI, automatic OpenAPI generation và validation.

## Boundary / Ranh giới

### Nó là gì

Nó là API framework cho route, dependency injection nhẹ, request/response validation, async handler và OpenAPI docs.

### Nó không phải là gì

Nó không tự giải quyết database transaction, background job reliability hoặc auth policy nếu app không thiết kế rõ.

## Core Mechanism / Cơ chế lõi

FastAPI đọc type hints/Pydantic model để validate input/output, map route tới handler và sinh OpenAPI schema.

## Project Role / Vai trò trong dự án

Node này giúp debug API schema, validation error, dependency injection, async blocking và contract mismatch giữa frontend/backend.

## Output / Artifact nên có

- OpenAPI schema sinh từ route/model
- Pydantic request/response model
- Dependency graph cho auth/database/session

## Decision Checklist / Câu hỏi kiểm tra

- Response model có khớp contract public không?
- Handler async có gọi blocking IO không?
- Dependency auth/database có scope đúng request không?
- Validation error có trả format ổn định cho client không?

## Failure Modes / Cách nó gây lỗi

- Type/model sai làm OpenAPI contract lệch thực tế
- Blocking IO trong async route làm latency tăng
- Dependency dùng sai scope làm leak session hoặc auth state

## Khi nào chưa cần hoặc dễ over-engineer

- Không cần FastAPI nếu chỉ viết script hoặc internal worker không có API boundary
- Dễ over-engineer nếu tách quá nhiều dependency nhỏ trước khi API ổn định

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[OpenAPI]] vì FastAPI sinh schema từ route và type model
- [[Request Validation]] vì validation là lợi ích chính của framework

## Liên quan rộng

- Python API
- ASGI
- Pydantic

## Keywords / Từ khóa tìm kiếm

- FastAPI
- Python API framework
- Pydantic
- ASGI
- OpenAPI generation
- dependency injection
- async route
- request validation

## Source trace

- FastAPI official documentation
