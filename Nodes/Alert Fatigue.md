# Alert Fatigue

Aliases: Alert Fatigue, alert fatigue, alert noise, mệt mỏi cảnh báo

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Alert Fatigue là node bổ sung cho ComputingWiki về tình trạng quá nhiều alert nhiễu làm team bỏ lỡ cảnh báo quan trọng.

## Boundary / Ranh giới

### Nó là gì

Alert Fatigue dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới tình trạng quá nhiều alert nhiễu làm team bỏ lỡ cảnh báo quan trọng.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Alert Fatigue là hiểu boundary, input/output, state và failure mode riêng của tình trạng quá nhiều alert nhiễu làm team bỏ lỡ cảnh báo quan trọng.

## Project Role / Vai trò trong dự án

Alert Fatigue giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Alert Fatigue incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Alert Fatigue biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Alert Fatigue làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Alert Fatigue nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Alert]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Alert Fatigue
- [[Monitoring]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Alert Fatigue

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Alert Fatigue
- alert fatigue
- alert noise
- mệt mỏi cảnh báo
- alert
- fatigue

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
