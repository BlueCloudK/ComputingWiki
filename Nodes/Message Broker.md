# Message Broker

Aliases: Message Broker, message broker, RabbitMQ Kafka, broker message

Type: Backend Engineering

## Context / Ngữ cảnh

Message Broker là node bổ sung cho ComputingWiki về hệ thống trung gian nhận, lưu và phân phối message giữa services.

## Boundary / Ranh giới

### Nó là gì

Message Broker dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới hệ thống trung gian nhận, lưu và phân phối message giữa services.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Message Broker là hiểu boundary, input/output, state và failure mode riêng của hệ thống trung gian nhận, lưu và phân phối message giữa services.

## Project Role / Vai trò trong dự án

Message Broker giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Message Broker contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Message Broker nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Message Broker mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Message Broker nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Queue]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Message Broker
- [[Event Driven Architecture]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Message Broker

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Message Broker
- message broker
- RabbitMQ Kafka
- broker message
- message
- broker

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
