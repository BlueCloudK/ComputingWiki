# Flaky Test

Aliases: Flaky Test, flaky test, nondeterministic test, test chập chờn

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Flaky Test là node bổ sung cho ComputingWiki về test lúc pass lúc fail dù code không đổi.

## Boundary / Ranh giới

### Nó là gì

Flaky Test dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới test lúc pass lúc fail dù code không đổi.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Flaky Test là hiểu boundary, input/output, state và failure mode riêng của test lúc pass lúc fail dù code không đổi.

## Project Role / Vai trò trong dự án

Flaky Test giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Flaky Test incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Flaky Test biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Flaky Test làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Flaky Test nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh


- Chưa có nối mạnh ngoài các node con trực tiếp
## Liên quan rộng

- Testing and Verification
- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Flaky Test
- flaky test
- nondeterministic test
- test chập chờn
- flaky
- test

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
