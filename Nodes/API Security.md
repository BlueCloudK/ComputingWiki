# API Security

Aliases: secure API, bảo mật API, application programming interface security

Type: Security

## Context / Ngữ cảnh

API Security xuất hiện khi API nhận request từ client, service khác hoặc third-party và cần chống misuse, data leak, abuse hoặc unauthorized access.

## Boundary / Ranh giới

### Nó là gì

API Security là tập kiểm soát bảo vệ API boundary: identity, permission, input, rate, error, transport và sensitive data exposure.

### Nó không phải là gì

Nó không chỉ là thêm token vào header, không thay thế authorization rule, và không đảm bảo an toàn nếu contract/error/log vẫn lộ dữ liệu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là kiểm tra request trước khi API xử lý sâu: authenticate, authorize, validate, rate limit, log an toàn và trả error không lộ thông tin nhạy cảm.

## Project Role / Vai trò trong dự án

API Security giúp integration không trở thành cửa mở vào dữ liệu hoặc hành động nhạy cảm. Nó đặc biệt quan trọng khi API public, mobile, multi-tenant hoặc gọi giữa service.

## Output / Artifact nên có

- API security checklist cho endpoint quan trọng
- Auth/authz/input validation/rate limit rule
- Test case cho unauthorized, forbidden, invalid và abuse path

## Decision Checklist / Câu hỏi kiểm tra

- Ai được gọi API này và với quyền nào?
- Input untrusted đã validate chưa?
- API có rate limit hoặc abuse control không?
- Error/log có lộ secret, PII hoặc internal detail không?
- Transport/session/token handling có đúng không?

## Failure Modes / Cách nó gây lỗi

- Authenticated user gọi được action không thuộc quyền
- Validation thiếu làm injection hoặc data corruption
- Error trả quá chi tiết làm lộ internal structure
- Không rate limit nên bị abuse hoặc cost spike

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần security layer phức tạp cho API local chỉ dùng trong prototype
- Dễ over-engineer nếu endpoint nội bộ đơn giản bị bọc quá nhiều control không có threat model

## Gồm những gì

- [[Authentication]]
- [[Authorization]]
- [[Input Validation]]
- [[Rate Limiting]]

## Nối mạnh

- [[API Contract]] vì security rule phải nằm trong contract hoặc endpoint policy
- [[Secret]] vì API thường dùng token/key cần bảo vệ
- [[Error Handling]] vì error response có thể lộ dữ liệu hoặc hỗ trợ attacker

## Liên quan rộng

- OWASP API Security
- Threat modeling
- Audit logging

## Keywords / Từ khóa tìm kiếm

- API Security
- API authentication
- API authorization
- token validation
- rate limit security
- input validation
- OWASP API
- broken object level authorization
- bảo mật API
- kiểm tra quyền API

## Source trace

- OWASP API Security Top 10
- OWASP Cheat Sheet Series
