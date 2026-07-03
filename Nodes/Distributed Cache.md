# Distributed Cache

Aliases: Distributed Cache, distributed cache, Redis cache, cache phân tán

Type: Backend Engineering

## Context / Ngữ cảnh

Distributed Cache là node bổ sung cho ComputingWiki về cache dùng chung giữa nhiều instance/service.

## Boundary / Ranh giới

### Nó là gì

Distributed Cache dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới cache dùng chung giữa nhiều instance/service.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Distributed Cache là hiểu boundary, input/output, state và failure mode riêng của cache dùng chung giữa nhiều instance/service.

## Project Role / Vai trò trong dự án

Distributed Cache giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Distributed Cache contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Distributed Cache nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Distributed Cache mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Distributed Cache nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cache]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Distributed Cache
- [[Distributed System]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Distributed Cache

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Distributed Cache
- distributed cache
- Redis cache
- cache phân tán
- distributed
- cache

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
