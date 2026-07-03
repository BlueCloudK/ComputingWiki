# Incident Timeline

Aliases: Incident Timeline, incident timeline, timeline sự cố, dòng thời gian incident

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Incident Timeline là node bổ sung cho ComputingWiki về dòng thời gian event, alert, deploy và action trong incident.

## Boundary / Ranh giới

### Nó là gì

Incident Timeline dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới dòng thời gian event, alert, deploy và action trong incident.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Incident Timeline là hiểu boundary, input/output, state và failure mode riêng của dòng thời gian event, alert, deploy và action trong incident.

## Project Role / Vai trò trong dự án

Incident Timeline giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Incident Timeline incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Incident Timeline biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Incident Timeline làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Incident Timeline nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Incident]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Incident Timeline
- [[Postmortem]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Incident Timeline

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Incident Timeline
- incident timeline
- timeline sự cố
- dòng thời gian incident
- incident
- timeline

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
