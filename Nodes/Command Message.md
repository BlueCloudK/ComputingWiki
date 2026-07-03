# Command Message

Aliases: Command Message, command message, command event, lệnh bất đồng bộ

Type: Backend Engineering

## Context / Ngữ cảnh

Command Message là node bổ sung cho ComputingWiki về message yêu cầu một handler thực hiện hành động cụ thể.

## Boundary / Ranh giới

### Nó là gì

Command Message dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới message yêu cầu một handler thực hiện hành động cụ thể.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Command Message là hiểu boundary, input/output, state và failure mode riêng của message yêu cầu một handler thực hiện hành động cụ thể.

## Project Role / Vai trò trong dự án

Command Message giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Command Message contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Command Message nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Command Message mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Command Message nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Message Broker]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Command Message

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Command Message
- command message
- command event
- lệnh bất đồng bộ
- command
- message

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
