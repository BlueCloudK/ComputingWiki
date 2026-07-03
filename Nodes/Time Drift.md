# Time Drift

Aliases: Time Drift, time drift, clock drift, trôi thời gian

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Time Drift là node bổ sung cho ComputingWiki về đồng hồ hệ thống trôi dần khỏi thời gian chuẩn.

## Boundary / Ranh giới

### Nó là gì

Time Drift dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới đồng hồ hệ thống trôi dần khỏi thời gian chuẩn.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Time Drift là hiểu boundary, input/output, state và failure mode riêng của đồng hồ hệ thống trôi dần khỏi thời gian chuẩn.

## Project Role / Vai trò trong dự án

Time Drift giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Time Drift incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Time Drift biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Time Drift làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Time Drift nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Clock Skew]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Time Drift

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Time Drift
- time drift
- clock drift
- trôi thời gian
- time
- drift

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
