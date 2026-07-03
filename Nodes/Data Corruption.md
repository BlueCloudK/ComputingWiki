# Data Corruption

Aliases: Data Corruption, data corruption, corrupt data, hỏng dữ liệu

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Data Corruption là node bổ sung cho ComputingWiki về dữ liệu bị ghi sai, mất tính toàn vẹn hoặc không đọc được.

## Boundary / Ranh giới

### Nó là gì

Data Corruption dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới dữ liệu bị ghi sai, mất tính toàn vẹn hoặc không đọc được.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Data Corruption là hiểu boundary, input/output, state và failure mode riêng của dữ liệu bị ghi sai, mất tính toàn vẹn hoặc không đọc được.

## Project Role / Vai trò trong dự án

Data Corruption giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Data Corruption incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Data Corruption biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Data Corruption làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Data Corruption nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Data Consistency]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Data Corruption
- [[Backup Restore]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Data Corruption

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Data Corruption
- data corruption
- corrupt data
- hỏng dữ liệu
- data
- corruption

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
