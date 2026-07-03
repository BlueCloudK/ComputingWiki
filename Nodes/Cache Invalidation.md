# Cache Invalidation

Aliases: Cache Invalidation, cache invalidation, invalidate cache, xóa cache cũ

Type: Backend Engineering

## Context / Ngữ cảnh

Cache Invalidation là node bổ sung cho ComputingWiki về quy tắc làm stale cache hết hiệu lực khi dữ liệu gốc thay đổi.

## Boundary / Ranh giới

### Nó là gì

Cache Invalidation dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới quy tắc làm stale cache hết hiệu lực khi dữ liệu gốc thay đổi.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Cache Invalidation là hiểu boundary, input/output, state và failure mode riêng của quy tắc làm stale cache hết hiệu lực khi dữ liệu gốc thay đổi.

## Project Role / Vai trò trong dự án

Cache Invalidation giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Cache Invalidation contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Cache Invalidation nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Cache Invalidation mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Cache Invalidation nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cache]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Cache Invalidation
- [[Stale Cache]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Cache Invalidation

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Cache Invalidation
- cache invalidation
- invalidate cache
- xóa cache cũ
- cache
- invalidation

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
