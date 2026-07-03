# Saga Pattern

Aliases: Saga Pattern, saga pattern, distributed saga, mẫu saga

Type: Backend Engineering

## Context / Ngữ cảnh

Saga Pattern là node bổ sung cho ComputingWiki về pattern điều phối nhiều local transaction bằng step và compensation.

## Boundary / Ranh giới

### Nó là gì

Saga Pattern dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới pattern điều phối nhiều local transaction bằng step và compensation.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Saga Pattern là hiểu boundary, input/output, state và failure mode riêng của pattern điều phối nhiều local transaction bằng step và compensation.

## Project Role / Vai trò trong dự án

Saga Pattern giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Saga Pattern contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Saga Pattern nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Saga Pattern mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Saga Pattern nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Distributed Transaction]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Saga Pattern
- [[Event Driven Architecture]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Saga Pattern

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Saga Pattern
- saga pattern
- distributed saga
- mẫu saga
- saga
- pattern

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
