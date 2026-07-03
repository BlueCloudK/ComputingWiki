# Error Rate

Aliases: Error Rate, error rate, 5xx rate, tỷ lệ lỗi

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Error Rate là node bổ sung cho ComputingWiki về tỷ lệ request/job lỗi theo thời gian.

## Boundary / Ranh giới

### Nó là gì

Error Rate dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới tỷ lệ request/job lỗi theo thời gian.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Error Rate là hiểu boundary, input/output, state và failure mode riêng của tỷ lệ request/job lỗi theo thời gian.

## Project Role / Vai trò trong dự án

Error Rate giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Error Rate incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Error Rate biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Error Rate làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Error Rate nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Monitoring]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Error Rate
- [[Alert]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Error Rate

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Error Rate
- error rate
- 5xx rate
- tỷ lệ lỗi
- error
- rate

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
