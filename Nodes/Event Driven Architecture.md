# Event Driven Architecture

Aliases: Event Driven Architecture, event-driven architecture, EDA, kiến trúc hướng sự kiện

Type: Backend Engineering

## Context / Ngữ cảnh

Event Driven Architecture là node bổ sung cho ComputingWiki về kiến trúc trong đó service giao tiếp bằng event thay vì gọi trực tiếp mọi việc.

## Boundary / Ranh giới

### Nó là gì

Event Driven Architecture dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới kiến trúc trong đó service giao tiếp bằng event thay vì gọi trực tiếp mọi việc.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Event Driven Architecture là hiểu boundary, input/output, state và failure mode riêng của kiến trúc trong đó service giao tiếp bằng event thay vì gọi trực tiếp mọi việc.

## Project Role / Vai trò trong dự án

Event Driven Architecture giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Event Driven Architecture contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Event Driven Architecture nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Event Driven Architecture mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Event Driven Architecture nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Event]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Event Driven Architecture
- [[Message Broker]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Event Driven Architecture

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Event Driven Architecture
- event-driven architecture
- EDA
- kiến trúc hướng sự kiện
- event
- driven
- architecture

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
