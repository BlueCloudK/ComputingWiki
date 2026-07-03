# Heap Dump

Aliases: Heap Dump, heap dump, memory dump, ảnh chụp heap

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Heap Dump là node bổ sung cho ComputingWiki về snapshot memory heap dùng để phân tích leak hoặc object retention.

## Boundary / Ranh giới

### Nó là gì

Heap Dump dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới snapshot memory heap dùng để phân tích leak hoặc object retention.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Heap Dump là hiểu boundary, input/output, state và failure mode riêng của snapshot memory heap dùng để phân tích leak hoặc object retention.

## Project Role / Vai trò trong dự án

Heap Dump giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Heap Dump incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Heap Dump biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Heap Dump làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Heap Dump nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Memory Leak]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Heap Dump

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Heap Dump
- heap dump
- memory dump
- ảnh chụp heap
- heap
- dump

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
