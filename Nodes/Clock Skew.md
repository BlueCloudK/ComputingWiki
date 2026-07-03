# Clock Skew

Aliases: Clock Skew, clock skew, time skew, lệch đồng hồ

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Clock Skew là node bổ sung cho ComputingWiki về sai lệch thời gian giữa các machine/service.

## Boundary / Ranh giới

### Nó là gì

Clock Skew dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới sai lệch thời gian giữa các machine/service.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Clock Skew là hiểu boundary, input/output, state và failure mode riêng của sai lệch thời gian giữa các machine/service.

## Project Role / Vai trò trong dự án

Clock Skew giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Clock Skew incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Clock Skew biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Clock Skew làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Clock Skew nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Distributed System]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Clock Skew

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Clock Skew
- clock skew
- time skew
- lệch đồng hồ
- clock
- skew

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
