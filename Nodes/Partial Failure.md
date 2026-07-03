# Partial Failure

Aliases: Partial Failure, partial failure, distributed failure, lỗi cục bộ

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Partial Failure là node bổ sung cho ComputingWiki về failure chỉ xảy ra ở một phần hệ thống phân tán, phần khác vẫn chạy.

## Boundary / Ranh giới

### Nó là gì

Partial Failure dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới failure chỉ xảy ra ở một phần hệ thống phân tán, phần khác vẫn chạy.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Partial Failure là hiểu boundary, input/output, state và failure mode riêng của failure chỉ xảy ra ở một phần hệ thống phân tán, phần khác vẫn chạy.

## Project Role / Vai trò trong dự án

Partial Failure giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Partial Failure incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Partial Failure biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Partial Failure làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Partial Failure nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Distributed System]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Partial Failure
- [[Fault Tolerance]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Partial Failure

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Partial Failure
- partial failure
- distributed failure
- lỗi cục bộ
- partial
- failure

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
