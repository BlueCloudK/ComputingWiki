# Graceful Shutdown

Aliases: Graceful Shutdown, graceful shutdown, drain requests, tắt dịch vụ an toàn

Type: Backend Engineering

## Context / Ngữ cảnh

Graceful Shutdown là node bổ sung cho ComputingWiki về quy trình service ngừng nhận request mới và xử lý xong việc đang chạy trước khi tắt.

## Boundary / Ranh giới

### Nó là gì

Graceful Shutdown dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới quy trình service ngừng nhận request mới và xử lý xong việc đang chạy trước khi tắt.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Graceful Shutdown là hiểu boundary, input/output, state và failure mode riêng của quy trình service ngừng nhận request mới và xử lý xong việc đang chạy trước khi tắt.

## Project Role / Vai trò trong dự án

Graceful Shutdown giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Graceful Shutdown contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Graceful Shutdown nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Graceful Shutdown mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Graceful Shutdown nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Deployment]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Graceful Shutdown
- [[Request Lifecycle]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Graceful Shutdown

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Graceful Shutdown
- graceful shutdown
- drain requests
- tắt dịch vụ an toàn
- graceful
- shutdown

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
