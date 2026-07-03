# Validation

Aliases: validate input, xác thực dữ liệu

Type: Requirement / Planning

## Context / Ngữ cảnh

Validation xuất hiện khi dữ liệu, request hoặc requirement cần được kiểm tra xem có phù hợp với rule mong đợi trước khi hệ thống xử lý tiếp hay không.

## Boundary / Ranh giới

### Nó là gì

Validation là kiểm tra tính hợp lệ theo rule: format, range, required field, schema, domain constraint hoặc business invariant.

### Nó không phải là gì

Nó không phải là authentication, không phải authorization, và không phải sanitize output. Validation trả lời "dữ liệu này có hợp lệ để xử lý không".

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đặt rule ở boundary phù hợp, reject dữ liệu sai sớm, trả lỗi rõ và giữ invariant bên trong hệ thống. Validation tốt có cùng nghĩa giữa client, API và domain.

## Project Role / Vai trò trong dự án

Validation bảo vệ API, database và business logic khỏi dữ liệu rác hoặc dữ liệu vượt constraint. Nó cũng làm acceptance criteria cụ thể hơn khi requirement có rule dữ liệu.

## Output / Artifact nên có

- Validation rule hoặc schema
- Error message/status cho input không hợp lệ
- Test case cho valid, invalid và boundary value

## Decision Checklist / Câu hỏi kiểm tra

- Rule hợp lệ nằm ở format, domain hay business process?
- Validation nên ở client, API, domain hay database?
- Khi invalid thì reject, normalize hay ask user sửa?
- Error có đủ rõ cho consumer xử lý không?
- Rule này có thống nhất với API contract không?

## Failure Modes / Cách nó gây lỗi

- Chỉ validate ở client nên API vẫn nhận dữ liệu sai
- Rule khác nhau giữa frontend/backend làm bug khó trace
- Error quá mơ hồ khiến consumer retry sai cách
- Nhầm validation với authorization làm lộ hoặc chặn sai quyền

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần schema phức tạp cho dữ liệu thử nghiệm chỉ dùng nội bộ
- Dễ over-engineer nếu validate mọi intermediate object thay vì boundary quan trọng

## Gồm những gì

- [[Input Validation]]
- [[API Contract]]

## Nối mạnh

- [[Acceptance Criteria]] vì rule dữ liệu thường cần tiêu chí pass/fail rõ
- [[Requirement]] vì validation rule nên trace được về nhu cầu hoặc constraint
- [[Authentication]] vì dễ bị nhầm với validation dù mục đích khác nhau

## Liên quan rộng

- Data quality
- Defensive programming
- Security boundary

## Keywords / Từ khóa tìm kiếm

- Validation
- validate input
- xác thực dữ liệu
- Input Validation
- API Contract
- Validation learning keyword

## Source trace

- Requirements Engineering Map / OWASP Map
