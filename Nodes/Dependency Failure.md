# Dependency Failure

Aliases: Dependency Failure, dependency failure, third-party outage, lỗi dependency

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Dependency Failure là node bổ sung cho ComputingWiki về failure do service/library/third-party mà hệ thống phụ thuộc bị lỗi.

## Boundary / Ranh giới

### Nó là gì

Dependency Failure dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới failure do service/library/third-party mà hệ thống phụ thuộc bị lỗi.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Dependency Failure là hiểu boundary, input/output, state và failure mode riêng của failure do service/library/third-party mà hệ thống phụ thuộc bị lỗi.

## Project Role / Vai trò trong dự án

Dependency Failure giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Dependency Failure incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Dependency Failure biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Dependency Failure làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Dependency Failure nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Circuit Breaker]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Dependency Failure
- [[Timeout]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Dependency Failure

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Dependency Failure
- dependency failure
- third-party outage
- lỗi dependency
- dependency
- failure

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
