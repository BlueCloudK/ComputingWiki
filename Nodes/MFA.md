# MFA

Aliases: MFA, xác thực đa yếu tố

Type: Security

## Context / Ngữ cảnh

MFA là node bổ sung cho ComputingWiki về xác thực nhiều yếu tố để giảm rủi ro khi password bị lộ.

## Boundary / Ranh giới

### Nó là gì

MFA dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới xác thực nhiều yếu tố để giảm rủi ro khi password bị lộ.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của MFA là hiểu boundary, input/output, state và failure mode riêng của xác thực nhiều yếu tố để giảm rủi ro khi password bị lộ.

## Project Role / Vai trò trong dự án

MFA giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- MFA control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi MFA?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai MFA sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho MFA nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Authentication]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng MFA

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- MFA
- multi-factor authentication
- xác thực đa yếu tố

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
