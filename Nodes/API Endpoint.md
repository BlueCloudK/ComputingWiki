# API Endpoint

Aliases: API Endpoint, endpoint, API endpoint, đường dẫn API

Type: Backend Engineering

## Context / Ngữ cảnh

API Endpoint là node bổ sung cho ComputingWiki về địa chỉ và operation cụ thể mà client gọi để thao tác với backend.

## Boundary / Ranh giới

### Nó là gì

API Endpoint dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới địa chỉ và operation cụ thể mà client gọi để thao tác với backend.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của API Endpoint là hiểu boundary, input/output, state và failure mode riêng của địa chỉ và operation cụ thể mà client gọi để thao tác với backend.

## Project Role / Vai trò trong dự án

API Endpoint giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- API Endpoint contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- API Endpoint nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế API Endpoint mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu API Endpoint nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Route]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng API Endpoint
- [[API Contract]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng API Endpoint

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- API Endpoint
- endpoint
- API endpoint
- đường dẫn API

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
