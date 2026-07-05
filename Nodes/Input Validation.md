# Input Validation

Aliases: validate untrusted input, kiểm tra input

Type: Security

## Context / Ngữ cảnh

Input Validation xuất hiện ở mọi boundary nhận dữ liệu không tin cậy: HTTP request, form, file upload, webhook, message queue, CLI argument, config, AI prompt, third-party payload hoặc internal API. Nó giúp reject dữ liệu sai format/range/schema trước khi đi vào domain logic, database, shell command hoặc downstream service.

## Boundary / Ranh giới

### Nó là gì

Input Validation là kiểm tra input theo allowlist/schema/rule rõ: type, required/optional, length, format, enum, range, relation giữa field, file type/size và business constraint. Trong security, nó giảm attack surface cho injection, traversal, parser abuse, malformed payload và dữ liệu bẩn đi sâu vào hệ thống.

### Nó không phải là gì

Input Validation không thay thế output encoding, authorization, authentication hoặc parameterized query. Validate input tốt vẫn không đủ để chống XSS/SQL injection nếu output/DB layer dùng sai. Nó cũng không nên chỉ nằm ở frontend vì attacker có thể gọi backend trực tiếp.

## Core Mechanism / Cơ chế lõi

Backend nhận input, parse theo content type, validate schema/rule, normalize nếu cần, reject input không hợp lệ với error format nhất quán, rồi chỉ truyền dữ liệu đã được type-safe/validated vào service/domain. Rule nên ưu tiên allowlist hơn blocklist, và phải có test cho boundary value/malformed payload.

## Project Role / Vai trò trong dự án

Input Validation là node cần mở khi thiết kế API contract, file upload, search/filter, webhook, command execution, path/file access hoặc AI/tool input. Nó giúp team quyết định rule nằm ở controller/schema/domain/database đâu và lỗi trả cho client như thế nào.

## Output / Artifact nên có

- Input schema/rule: type, required, nullable, enum, range, length, pattern, file limit
- Error response format cho invalid input
- Test case: missing field, wrong type, boundary value, malformed JSON, oversized payload
- Normalization decision: trim/lowercase/canonicalize path/email/URL nếu cần
- Security review cho input đi vào SQL, shell, file path, template, parser hoặc LLM/tool

## Decision Checklist / Câu hỏi kiểm tra

- Input này đến từ boundary không tin cậy nào?
- Rule nên là allowlist/schema hay blocklist?
- Có giới hạn length/size/depth để tránh parser/resource abuse không?
- Input có đi vào SQL, shell, file path, template, regex hoặc external API không?
- Frontend/backend validation có khớp nhau không?
- Invalid input trả lỗi đủ rõ nhưng không leak internals không?
- Có test malformed/boundary case trong CI không?

## Failure Modes / Cách nó gây lỗi

- Chỉ validate ở frontend nên attacker gửi payload trực tiếp tới API.
- Blocklist thiếu case encoding/unicode khiến bypass rule.
- Không giới hạn size/depth làm parser hoặc memory bị cạn.
- Validate format nhưng không enforce authorization, vẫn cho truy cập object trái quyền.
- Normalize/canonicalize path sai dẫn tới path traversal.
- Error quá chi tiết lộ stack trace, schema nội bộ hoặc security rule.

## Khi nào chưa cần hoặc dễ over-engineer

- Input nội bộ rất hẹp có thể dùng validation nhẹ nhưng vẫn cần boundary rõ.
- Không nên tạo custom validator phức tạp nếu schema/framework validation đủ dùng.
- Không nên tin validation là “lá chắn duy nhất”; vẫn cần encoding, parameterized query, auth và least privilege.

## Gồm những gì

- [[Validation]]
- [[XSS]]
- [[SQL Injection]]

## Nối mạnh

- [[Validation]] vì input validation là một phần cụ thể của validation ở boundary.
- [[API Contract]] vì request schema phải khớp contract.
- [[Command Injection]] vì input đi vào shell/command cần kiểm soát rất nghiêm.
- [[Path Traversal]] vì path/filename cần canonicalize và enforce base directory.
- [[RCE]] vì nhiều RCE bắt đầu từ untrusted input vào execution primitive.

## Liên quan rộng

- Application security
- Backend boundary
- Parser safety
- Defensive programming

## Keywords / Từ khóa tìm kiếm

- Input Validation
- validate untrusted input
- kiểm tra input
- allowlist validation
- schema validation
- malformed payload
- boundary value
- input size limit
- canonicalization
- parser abuse
- validation bypass
- backend validation
- security input validation
- input validation debugging

## Source trace

- OWASP Input Validation Cheat Sheet
