# Log Correlation

Aliases: Log Correlation, log correlation, correlate logs, ghép log

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Log Correlation là node bổ sung cho ComputingWiki về ghép log của nhiều service/request bằng id hoặc context chung.

## Boundary / Ranh giới

### Nó là gì

Log Correlation dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới ghép log của nhiều service/request bằng id hoặc context chung.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Log Correlation là hiểu boundary, input/output, state và failure mode riêng của ghép log của nhiều service/request bằng id hoặc context chung.

## Project Role / Vai trò trong dự án

Log Correlation giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Log Correlation incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Log Correlation biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Log Correlation làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Log Correlation nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Trace ID]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Log Correlation
- [[Logging]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Log Correlation

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Log Correlation
- log correlation
- correlate logs
- ghép log
- correlation

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
