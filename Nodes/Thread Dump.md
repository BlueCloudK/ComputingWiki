# Thread Dump

Aliases: Thread Dump, thread dump, jstack, ảnh chụp thread

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Thread Dump là node bổ sung cho ComputingWiki về snapshot thread và stack hiện tại để debug deadlock/starvation.

## Boundary / Ranh giới

### Nó là gì

Thread Dump dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới snapshot thread và stack hiện tại để debug deadlock/starvation.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Thread Dump là hiểu boundary, input/output, state và failure mode riêng của snapshot thread và stack hiện tại để debug deadlock/starvation.

## Project Role / Vai trò trong dự án

Thread Dump giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Thread Dump incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Thread Dump biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Thread Dump làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Thread Dump nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Thread Starvation]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Thread Dump
- [[Deadlock]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Thread Dump

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Thread Dump
- thread dump
- jstack
- ảnh chụp thread
- thread
- dump

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
