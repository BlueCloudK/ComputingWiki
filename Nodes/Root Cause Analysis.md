# Root Cause Analysis

Aliases: Root Cause Analysis, RCA, root cause analysis, phân tích nguyên nhân gốc

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Root Cause Analysis là node bổ sung cho ComputingWiki về phân tích nguyên nhân hệ thống khiến failure xảy ra và tái diễn.

## Boundary / Ranh giới

### Nó là gì

Root Cause Analysis dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới phân tích nguyên nhân hệ thống khiến failure xảy ra và tái diễn.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Root Cause Analysis là hiểu boundary, input/output, state và failure mode riêng của phân tích nguyên nhân hệ thống khiến failure xảy ra và tái diễn.

## Project Role / Vai trò trong dự án

Root Cause Analysis giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Root Cause Analysis incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Root Cause Analysis biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Root Cause Analysis làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Root Cause Analysis nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Postmortem]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Root Cause Analysis

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Root Cause Analysis
- RCA
- root cause analysis
- phân tích nguyên nhân gốc
- root
- cause
- analysis

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
