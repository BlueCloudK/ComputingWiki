# Brownout

Aliases: Brownout, brownout, graceful degradation

Type: Debugging and Failure Patterns

## Context / Ngữ cảnh

Brownout là node bổ sung cho ComputingWiki về tình trạng hệ thống vẫn chạy nhưng giảm chất lượng hoặc tắt bớt feature để sống sót.

## Boundary / Ranh giới

### Nó là gì

Brownout dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới tình trạng hệ thống vẫn chạy nhưng giảm chất lượng hoặc tắt bớt feature để sống sót.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Debugging and Failure Patterns; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Brownout là hiểu boundary, input/output, state và failure mode riêng của tình trạng hệ thống vẫn chạy nhưng giảm chất lượng hoặc tắt bớt feature để sống sót.

## Project Role / Vai trò trong dự án

Brownout giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Brownout incident note hoặc runbook snippet
- Metric/log/trace dùng để nhận diện
- Mitigation và prevention note sau khi fix

## Decision Checklist / Câu hỏi kiểm tra

- Brownout biểu hiện ở user, service, database hay infrastructure?
- Signal nào phân biệt nó với failure mode gần giống?
- Có mitigation nhanh và fix dài hạn không?

## Failure Modes / Cách nó gây lỗi

- Nhận diện sai Brownout làm fix nhầm layer
- Thiếu telemetry khiến incident phải đoán thay vì trace
- Mitigation tạm không được follow-up thành fix bền vững

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần playbook riêng cho Brownout nếu chưa từng gặp hoặc impact thấp
- Dễ over-engineer nếu thêm observability phức tạp trước khi có signal cần đo

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Overload Handling]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Brownout
- [[Saturation]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Brownout

## Liên quan rộng

- Production debugging
- Incident response
- Reliability engineering

## Keywords / Từ khóa tìm kiếm

- Brownout
- brownout
- graceful degradation
- giảm chất lượng khi quá tải

## Source trace

- Google SRE Book
- Google SRE Workbook
- OpenTelemetry documentation
