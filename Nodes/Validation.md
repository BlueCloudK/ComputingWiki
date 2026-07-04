# Validation

Aliases: validate input, xác thực dữ liệu

Type: Requirement / Planning

## Context / Ngữ cảnh

Validation xuất hiện khi request, form input, file, config, message, command hoặc requirement cần được kiểm tra có hợp lệ trước khi hệ thống xử lý tiếp. Nó là boundary quan trọng giữa dữ liệu không tin cậy và domain logic/database.

## Boundary / Ranh giới

### Nó là gì

Validation là kiểm tra dữ liệu theo rule rõ: required field, type, format, range, enum, length, schema, relation giữa field, domain constraint hoặc business invariant. Mục tiêu là reject dữ liệu không hợp lệ sớm, trả lỗi rõ và giữ dữ liệu bên trong hệ thống nhất quán.

### Nó không phải là gì

Validation không phải authentication, authorization hoặc output sanitization. Authentication hỏi “bạn là ai”; authorization hỏi “bạn được làm gì”; validation hỏi “dữ liệu này có hợp lệ để xử lý không”. Validation cũng không thay thế database constraint nếu invariant cần bảo vệ chắc chắn.

## Core Mechanism / Cơ chế lõi

Validation thường chạy theo nhiều lớp: client validation để UX tốt, API/request validation để bảo vệ boundary, domain validation để giữ rule nghiệp vụ, và database constraint để bảo vệ invariant cuối cùng. Rule tốt phải nhất quán với API contract và trả error format đủ rõ cho consumer sửa input.

## Project Role / Vai trò trong dự án

Validation giúp biến requirement mơ hồ thành rule kiểm chứng được và giúp backend không nhận dữ liệu rác. Khi debug bug dữ liệu, cần biết input sai lọt qua lớp nào, frontend/backend rule có lệch không, error response có đúng contract không và database có constraint cuối cùng không.

## Output / Artifact nên có

- Validation schema/rule: required, optional, nullable, enum, range, format, cross-field rule
- Error response format và status code cho invalid input
- Test case cho valid, invalid, boundary value, missing field và malformed payload
- Mapping rule với API Contract/OpenAPI nếu endpoint public hoặc nhiều consumer
- Database constraint hoặc invariant note cho rule quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Rule này là format-level, schema-level, domain-level hay business invariant?
- Validation nên nằm ở client, API boundary, domain service hay database constraint?
- Frontend và backend có cùng hiểu required/optional/nullable không?
- Invalid input sẽ reject, normalize hay yêu cầu user sửa?
- Error message có đủ rõ cho user/consumer nhưng không lộ thông tin nhạy cảm không?
- Có test boundary value và malformed payload không?
- Rule này có thay đổi theo role/permission/context không?

## Failure Modes / Cách nó gây lỗi

- Chỉ validate ở client nên API vẫn nhận dữ liệu sai từ script/tool khác.
- Frontend/backend validation lệch làm user thấy pass ở UI nhưng fail ở API.
- Error mơ hồ khiến consumer retry hoặc sửa sai chỗ.
- Validate quá muộn làm dữ liệu rác đi vào database/job/event.
- Nhầm validation với authorization làm user gửi dữ liệu hợp lệ nhưng không được phép vẫn lọt qua.
- Rule chỉ nằm ở app code, không có constraint, nên race condition vẫn phá invariant.

## Khi nào chưa cần hoặc dễ over-engineer

- Dữ liệu thử nghiệm nội bộ ngắn hạn có thể dùng validation nhẹ nhưng vẫn cần boundary rõ.
- Không nên validate mọi object trung gian nếu boundary chính đã rõ và domain invariant được bảo vệ.
- Không nên dùng schema quá phức tạp khi rule nghiệp vụ thay đổi liên tục và chưa ổn định.

## Gồm những gì

- [[Input Validation]]
- [[API Contract]]

## Nối mạnh

- [[API Contract]] vì validation rule phải khớp request/response contract.
- [[OpenAPI]] vì schema OpenAPI có thể mô tả và kiểm tra nhiều validation rule.
- [[Controller]] vì controller/API boundary thường là nơi nhận request và kích hoạt validation.
- [[Database Constraint]] vì invariant quan trọng nên có lớp bảo vệ ở database.
- [[Acceptance Criteria]] vì validation rule nên trace được thành tiêu chí pass/fail.

## Liên quan rộng

- Data quality
- Defensive programming
- Security boundary
- Requirements engineering

## Keywords / Từ khóa tìm kiếm

- Validation
- validate input
- xác thực dữ liệu
- input validation
- schema validation
- request validation
- required field
- nullable field
- boundary value
- validation error
- domain validation
- database constraint
- malformed payload
- validation rule
- validation debugging

## Source trace

- OWASP Input Validation Cheat Sheet
- Requirements Engineering Map
