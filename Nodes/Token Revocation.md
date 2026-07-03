# Token Revocation

Aliases: Token Revocation, token revocation, revoke token, thu hồi token

Type: Security

## Context / Ngữ cảnh

Token Revocation là node bổ sung cho ComputingWiki về cách vô hiệu hóa token trước khi hết hạn tự nhiên.

## Boundary / Ranh giới

### Nó là gì

Token Revocation dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới cách vô hiệu hóa token trước khi hết hạn tự nhiên.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Token Revocation là hiểu boundary, input/output, state và failure mode riêng của cách vô hiệu hóa token trước khi hết hạn tự nhiên.

## Project Role / Vai trò trong dự án

Token Revocation giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Token Revocation control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Token Revocation?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Token Revocation sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Token Revocation nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Access Token]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Token Revocation
- [[Session Management]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Token Revocation

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Token Revocation
- token revocation
- revoke token
- thu hồi token
- token
- revocation

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
